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

````

**Observed Behavior:**
When a malformed character (single quote `'`) is appended to the URL, the application returns an **HTTP 404** error page containing:
````
