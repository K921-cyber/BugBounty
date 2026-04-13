# Outdated Jetty Server Version (10.0.25) – ASSA ABLOY America

## 📌 Summary
During passive testing of the `*.eacconfig.assaabloy.com` web application, it was discovered that the server is running **Jetty version 10.0.25**.  
The version information is disclosed in HTTP error pages and is affected by multiple known vulnerabilities, including **Denial of Service (DoS)** and **Server-Side Request Forgery (SSRF)**.

**Severity:** Informational (P5)  
**Status:** Closed – Informational  
**Reported Date:** 05 Aug 2025  
**Closed Date:** 06 Aug 2025  
**Platform:** Bugcrowd  
**Category (VRT):** Using Components with Known Vulnerabilities → Outdated Software Version

---

## 🛠️ Technical Details

**Vulnerability Type:** Outdated Software Version (Jetty)  
**Endpoint Tested:**  
---

**Observed Behavior:**
When a malformed character (single quote `'`) is appended to the URL, the application returns an **HTTP 404** error page containing:
https://eacconfig.assaabloy.com/gatingForm


<img width="1919" height="924" alt="Screenshot 2025-08-05 223515" src="https://github.com/user-attachments/assets/01d73b9f-c39b-4d33-ae7a-fb834702e3a8" />


---


---

## 🔍 Steps to Reproduce

1. Navigate to:
```
https://eacconfig.assaabloy.com/gatingForm
```
2.Append a single quote (`'`):
```
https://eacconfig.assaabloy.com/gatingForm

```
3. Observe the HTTP 404 error page.
4. The response discloses:

<img width="1919" height="924" alt="Screenshot 2025-08-05 223515" src="https://github.com/user-attachments/assets/7bed41ae-a71f-4d1f-9875-43d461574b7d" />


---
---

## 🧩 Affected Version & CVEs

- **CVE-2025-1948** – HTTP/2 settings misconfiguration allowing memory exhaustion via malicious frames (DoS).  
🔗 https://www.opencve.io/cve/CVE-2025-1948

- **CVE-2024-6763** – Improper URI validation potentially enabling SSRF and open redirect.  
🔗 https://www.opencve.io/cve/CVE-2024-6763

- Other risks may include:
- Request smuggling
- Path traversal
- Internal path leakage

---

## 🎯 Impact

- Enables attackers to **fingerprint backend technology** and match known exploits.
- Increases the attack surface for **DoS** or **SSRF**.
- Can be chained with other vulnerabilities for more severe exploitation.

---

## 🛡️ Recommendations

- Upgrade Jetty to **10.0.26** or preferably **Jetty 11/12** for latest security patches.
- Suppress server version disclosure:
- Disable `Server` header in HTTP responses.
- Remove version info from error pages.
- Implement custom error handling pages to prevent tech stack leakage.

---


## 📚 References

- [CVE-2025-1948](https://www.opencve.io/cve/CVE-2025-1948)  
- [CVE-2024-6763](https://www.opencve.io/cve/CVE-2024-6763)  
- [OWASP Secure Headers Project](https://owasp.org/www-project-secure-headers/)

---

> **Disclaimer:** This report was submitted under a responsible disclosure program.  
> It is shared here for educational and portfolio purposes only.

---
