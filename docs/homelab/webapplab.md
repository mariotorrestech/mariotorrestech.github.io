# Web Application Security Lab - OWASP Juice Shop

!!! abstract "BLUF"
    **What I built:** An OWASP Juice Shop instance hosted on Kali Linux for practicing web application security testing.  
    **Why it mattered:** Provides hands-on experience with OWASP Top 10 vulnerabilities in a safe, intentionally insecure application, bridging the gap between theory and practical exploitation.  
    **Outcome:** Functional web application testing environment with Burp Suite and FoxyProxy configured, enabling practice with SQL injection, XSS, authentication bypasses, and other common web vulnerabilities.

---

## Context & Goals

- **Problem:** Understanding web application vulnerabilities requires practical exploitation experience beyond reading documentation.
- **Goal:** Deploy a vulnerable web application to practice identifying, exploiting, and documenting security flaws following industry-standard methodologies.
- **Constraints:**
    - Internal-only access (no WAN exposure).
    - Hosted on existing Kali Linux VM to minimize resource overhead.
    - Must integrate with existing tooling (Burp Suite, browser proxies).

---

## Design & Decisions

- **Platform:** OWASP Juice Shop - maintained by OWASP, covers full spectrum of web vulnerabilities.
- **Deployment:** Containerized on Kali Linux (Docker or direct installation).
- **Tooling:** Burp Suite Community Edition as intercepting proxy, FoxyProxy for browser traffic routing.
- **Methodology:** Follow OWASP Testing Guide for structured approach to vulnerability assessment.
- **Documentation:** Record each finding with vulnerability description, exploitation steps, and remediation recommendations.

---

## Implementation

### Installation

```bash
# Docker deployment on Kali Linux
docker pull bkimminich/juice-shop
docker run -d -p 3000:3000 bkimminich/juice-shop

# Access at http://localhost:3000 or http://kali-ip:3000
```

### Tooling Setup

**Burp Suite Configuration:**

1. Launch Burp Suite Community Edition
2. Configure proxy listener on `127.0.0.1:8080`
3. Import Burp's CA certificate into browser trust store

**FoxyProxy Setup:**

1. Install FoxyProxy extension in Firefox/Chrome
2. Add proxy configuration:
    - **Title:** Burp Suite
    - **Proxy IP:** 127.0.0.1
    - **Port:** 8080
3. Toggle proxy on/off as needed for traffic interception

### Vulnerability Focus Areas

=== "Injection Attacks"

    - **SQL Injection:** Authentication bypass, data extraction, blind SQLi
    - **Command Injection:** OS command execution via vulnerable input fields
    - **XXE (XML External Entity):** Reading local files, SSRF attacks
    - **LDAP/NoSQL Injection:** Database-specific injection techniques

=== "Authentication & Session Management"

    - **Broken Authentication:** Weak password recovery, credential stuffing
    - **Session Fixation:** Hijacking user sessions
    - **JWT Manipulation:** Token forgery and algorithm confusion
    - **Brute Force:** Password and API endpoint enumeration

=== "Access Control"

    - **IDOR (Insecure Direct Object Reference):** Accessing unauthorized resources
    - **Privilege Escalation:** Horizontal and vertical privilege abuse
    - **Path Traversal:** Directory listing and file access outside web root
    - **Missing Function Level Access Control:** Admin panel access

=== "Client-Side Attacks"

    - **XSS (Cross-Site Scripting):** Reflected, stored, and DOM-based XSS
    - **CSRF (Cross-Site Request Forgery):** Forced actions on authenticated users
    - **Clickjacking:** UI redressing attacks
    - **Open Redirects:** Phishing via trusted domain redirects

=== "Security Misconfigurations"

    - **Information Disclosure:** Sensitive data in responses, error messages
    - **Insecure File Upload:** Malicious file upload and execution
    - **CORS Misconfiguration:** Cross-origin data access
    - **Security Headers:** Missing or weak headers (CSP, HSTS, X-Frame-Options)

### Tools Used

=== "Primary Tools"

    - **Burp Suite Community:** Traffic interception, parameter manipulation, vulnerability scanning
    - **FoxyProxy:** Browser proxy management for quick toggling
    - **sqlmap:** Automated SQL injection testing
    - **Netcat:** Reverse shell listeners and network testing

=== "Supporting Tools"

    - **curl/wget:** Manual HTTP request crafting
    - **jq:** JSON parsing and manipulation
    - **Nikto/dirb:** Web server scanning and directory enumeration
    - **OWASP ZAP:** Alternative web proxy and scanner

---

## Testing Methodology

1. **Reconnaissance:** Map application structure, identify input vectors
2. **Vulnerability Identification:** Test for common OWASP Top 10 vulnerabilities
3. **Exploitation:** Demonstrate impact of discovered vulnerabilities
4. **Documentation:** Record findings with screenshots, payloads, and severity ratings
5. **Remediation Research:** Document proper fixes for each vulnerability type

---

## Pitfalls & Fixes

- **Burp Suite certificate issues:** Browser not trusting proxy certificate.  
  *Fix:* Export Burp's CA cert and import into browser certificate store (Settings → Privacy → Certificates).

- **Docker port conflicts:** Port 3000 already in use.  
  *Fix:* Map to alternative port: `docker run -d -p 3001:3000 bkimminich/juice-shop`

- **FoxyProxy not routing traffic:** Proxy misconfigured or not enabled.  
  *Fix:* Verify proxy settings match Burp listener (127.0.0.1:8080), ensure FoxyProxy is set to "Use enabled proxies by patterns and order".

---

## Reflection

- **Skills demonstrated:** Web application security testing, intercepting proxy usage, vulnerability exploitation and documentation, understanding of OWASP Top 10.
- **Why this matters:** Web applications are primary attack vectors in modern environments; practical exploitation experience is essential for both offensive and defensive security roles.
- **Next steps:**
    - Complete all Juice Shop challenges and document findings
    - Practice writing professional vulnerability reports
    - Explore advanced techniques (race conditions, deserialization attacks)
    - Build automated testing scripts for common vulnerability patterns
    - Integrate findings into a mock penetration test report

---

## Resources

- **OWASP Juice Shop:** [https://owasp.org/www-project-juice-shop/](https://owasp.org/www-project-juice-shop/)
- **OWASP Testing Guide:** [https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)
- **PortSwigger Web Security Academy:** [https://portswigger.net/web-security](https://portswigger.net/web-security)

---

_Return to [Home](../index.md)_

_Return to [Homelab](../homelab/index.md)_
