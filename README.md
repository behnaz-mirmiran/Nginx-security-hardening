# Nginx-security-hardening
# Nginx Infrastructure Hardening & Security Configuration

This repository contains a production-ready, security-hardened `nginx.conf` template designed to remediate common infrastructure vulnerabilities identified during penetration testing and security audits.

## 🛡️ Vulnerabilities Remediated

| Vulnerability / Risk | Remediation Strategy | Directive / Header Used |
| :--- | :--- | :--- |
| **H_Brute Force** | Implemented rate limiting on sensitive endpoints | `limit_req_zone` & `limit_req` |
| **M_Clickjacking** | Prevented UI Redressing / framing from external origins | `X-Frame-Options: SAMEORIGIN` |
| **H_HSTS Missing** | Enforced strict HTTPS browser-level redirection | `Strict-Transport-Security` |
| **M_CORS Misconfiguration** | Restricted cross-origin resource sharing | `Access-Control-Allow-Origin` |
| **M_CSP Not Implemented** | Added a strict policy to mitigate XSS risks | `Content-Security-Policy` |
| **Information Disclosure** | Obfuscated server software banner and versions | `server_tokens off;` |
| **Insecure Cookies** | Injected security flags dynamically via web server | `proxy_cookie_path` (Secure, HttpOnly) |

## 🚀 How to Use

1. Clone this repository.
2. Replace placeholders like `example.com` and `127.0.0.1:3000` with your actual domain and upstream service details.
3. Validate configuration syntax:
   ```bash
   nginx -t
   systemctl reload nginx
