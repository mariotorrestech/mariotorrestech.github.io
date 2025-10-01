# Step-CA (Internal PKI — Manual Issuance)

!!! abstract "BLUF"
    **What I built:** An internal certificate authority using Step-CA, initialized with a root + intermediate CA.  
    **Why it mattered:** Gave my homelab consistent TLS with a centralized trust anchor, and allowing for internal port forwarding. 
    **Outcome:** All services now run with certificates issued from Step-CA, consumed by Nginx Proxy Manager for HTTPS. Clients trust them once the root CA is installed.

---

## Context & Goals

- **Problem:** Some internal services originally ran on plain HTTP. Internal port forwarding through NPM also requires a SSL certificate.
- **Goal:** Deploy a proper PKI inside the lab that mirrors enterprise practice (root → intermediate → service certificates).  
- **Constraints:**  
  - Local-only lab (`*.lab` domains).  
  - Using **manual issuance** for now (no ACME automation).  
  - Certificates loaded into Nginx Proxy Manager for TLS termination.

---

## Design & Decisions

- **PKI layout:** Offline root CA; online intermediate CA in a Proxmox LXC.  
- **Trust distribution:** Intermediate CA installed into my laptop, browsers, and other clients.  
- **Integration:** Issue certs via CLI → import into Nginx Proxy Manager → assign to proxied services.  
- **Why manual issuance?** Following the official Step-CA guide, I started with `step ca certificate` to keep things simple. I don't have many new services so automation is on the backburner.  

---

## Implementation

### Initialize the CA

```bash
step ca init
```

- Created root + intermediate certs.  
- Root stored offline; intermediate runs inside container.  
- Configured `ca.json` with DNS name (e.g., `ca.home.lab`).  

<!-- CONFIG FILE PLACEHOLDER -->

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

### Issue a Certificate (manual)

```bash
# Example: issue cert for nginx.home.lab
step ca certificate "nginx.lab" nginx.crt nginx.ksey
```

- Copy `nginx.crt` + `nginx.key` into NPM.  
- In NPM: add new SSL cert → assign to proxy host.  

<!-- SCREENSHOT / PATH PLACEHOLDER -->

### Trust the Root

- Export `root_ca.crt`.  
- Install into OS trust stores (macOS Keychain, browsers, etc.).  
- Import into containers/services as needed.

---

## Operations

### Renewal

- Track expiry dates.  
- Re‑issue with `step ca certificate` before expiry.  
- Reload NPM to pick up the updated cert.  
- Plan: add script/cron to automate renewal.  

### Backup

- Offline backup of root and intermediate private keys (encrypted).  
- Version‑controlled config (without secrets).  
- Root cert archived with documentation.

---

## Pitfalls & Fixes

- **Untrusted warnings** → forgot to install root CA.
*Fix:* add root to trust stores.  
- **Cert not applied in NPM** → service not reloaded. *Fix:* restart NPM after updating cert.  
- **Web consoles not loading** → web consoles not connecting after adding to NPM. *Fix:* enable WebSockets support in the NPM entry for Proxmox.  

---

## Reflection

- **Skills demonstrated:** PKI hierarchy, cert issuance, TLS termination with reverse proxy, trust distribution.  
- **Why this matters:** Similar principles used in enterprise internal PKI setups.  
- **Next steps:**  
  - Script renewals with `step` CLI.  
  - Centralize certificate inventory and alerting (feed into SIEM/logging).  
  - Enable ACME in the future to remove manual steps entirely.  
