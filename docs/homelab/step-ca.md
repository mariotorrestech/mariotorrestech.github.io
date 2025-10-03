# Step-CA (Internal PKI — Manual Issuance)

!!! abstract "BLUF"
    **What I built:** An internal certificate authority using Step-CA, initialized with a root + intermediate CA.  
    **Why it mattered:** Gave my homelab consistent TLS with a centralized trust anchor, and allowed internal HTTPS through Nginx Proxy Manager.  
    **Outcome:** All services now run with certificates issued from Step-CA. Clients trust them once the root CA is installed.

---

## Context & Goals

- **Problem:** Internal services originally ran on plain HTTP. TLS was needed for security and for Nginx Proxy Manager to proxy them.  
- **Goal:** Deploy a PKI inside the lab that mirrors enterprise practice (root → intermediate → service certificates).  
- **Constraints:**  
  - Local-only lab (`*.lab` domains).  
  - Manual issuance at first (no ACME automation).  
  - Certificates loaded into NPM for TLS termination.

---

## Design & Decisions

- **PKI layout:** Offline root CA; online intermediate CA running in a Proxmox LXC.  
- **Trust distribution:** Root stays offline, intermediate distributed to clients.  
- **Integration:** Issue certs via CLI → import into Nginx Proxy Manager → assign to proxied services.  
- **Why manual issuance?** Fewer services to start with, so token/ACME automation deferred.

---

## Implementation

### Initialize the CA
```bash
step ca init   --name "Homelab CA"   --dns "stepca.lab"   --address ":443"   --provisioner "admin@internal"
```

- Root + intermediate created.  
- Root stored offline; intermediate lives in container.  
- Configured `ca.json` with DNS name `stepca.lab`.

```json
// Example excerpt from /home/step/config/ca.json (sanitized)
{
  "root": "root_ca.crt",
  "crt": "intermediate_ca.crt",
  "key": "intermediate_ca_key",
  "address": ":443",
  "dnsNames": ["stepca.lab"]
}
```

### Start the CA Service
```bash
systemctl enable step-ca
systemctl start step-ca
```

### Bootstrap a Client
```bash
step ca bootstrap   --ca-url https://stepca.lab   --fingerprint <ROOT_FP>
```

### Health Check
```bash
step ca health   --ca-url https://stepca.lab   --root /etc/ssl/step/root_ca.crt
```

### Issue a Certificate (manual)
```bash
# Example: issue cert for nginx.lab
TOKEN=$(step ca token nginx.lab)
step ca certificate "nginx.lab" nginx.crt nginx.key   --token "$TOKEN"   --ca-url https://stepca.lab   --root /etc/ssl/step/root_ca.crt
```

- Copy `nginx.crt` + `nginx.key` into NPM.  
- In NPM: add new SSL cert → assign to proxy host.

### Trust the Root
- Export `root_ca.crt`.  
- Install into OS trust stores (macOS Keychain, browsers, etc.).  
- Import into containers/services as needed.

---

## Operations

### Renewal
- Manual: re-issue with `step ca certificate` before expiry.  
- Automated:  
  ```bash
  step ca renew --daemon     --exec "systemctl reload nginx"     /etc/ssl/npm.crt /etc/ssl/npm.key
  ```

### Backup
- Offline backup of root + intermediate private keys (encrypted).  
- Version-controlled configs (no secrets).  
- Archive root cert with docs.

---

## Optional: ACME Integration
- Add ACME provisioner on CA host:
  ```bash
  step ca provisioner add acme-lab --type ACME
  ```
- Directory URL:  
  `https://stepca.lab/acme/acme-lab/directory`  
- Configure NPM → Let’s Encrypt → Custom ACME directory above.  
- Use DNS-01 challenges against `.lab` DNS zone.  
- Benefit: full auto-issue and renewal.

---

## Pitfalls & Fixes

- **Untrusted warnings** → root CA not installed. *Fix:* add root to trust stores.  
- **Cert not applied in NPM** → forgot reload. *Fix:* reload NPM after update.  
- **Web consoles not loading** → missing WebSockets in NPM entry. *Fix:* enable WebSockets for proxied services.  

---

## Reflection

- **Skills demonstrated:** PKI hierarchy, cert issuance, TLS termination, trust distribution.  
- **Why this matters:** Mirrors enterprise PKI/CA practice in a lab.  
- **Next steps:**  
    - Script renewals and reloads.  
    - Centralize certificate inventory + logging.  
    - Roll out ACME for automation.
