# 🐞 Bug Bounty — Learning, Practice & Study Pack

> A compact, study-oriented introduction to bug bounty hunting: what to learn, where to practice, and a step-by-step learning plan with labs, exercises and templates. Drop this into your repo as `README.md` or `LEARN.md`.

---

## 🎯 Purpose

This file is for learners who want a guided path into bug bounties — from basic web security concepts to advanced exploitation and reporting. It combines structured theory, hands-on labs, practice targets, tool commands, and a reproducible study schedule.

---

## 🚦 Who is this for?

* Absolute beginners with basic web knowledge (HTTP, HTML, JS).
* Students preparing to get real-world practice on HackerOne/Bugcrowd.
* Self-learners who prefer a checklist + labs-based approach.

---

## 🧭 Learning Roadmap (High-level)

**Phase 0 — Foundations (0–2 weeks)**

* HTTP basics: methods, status codes, headers, cookies, CORS.
* HTML/JS fundamentals: DOM, forms, event flow.
* Basic Linux commands, curl, and working with files.

**Phase 1 — Web App Security Core (2–6 weeks)**

* XSS (Reflected, Stored, DOM)
* SQL Injection (blind, time-based)
* Insecure Direct Object References (IDOR)
* CSRF
* Open Redirects
* SSRF (intro)
* Authentication & Session management issues

**Phase 2 — Tooling & Recon (ongoing)**

* Burp Suite / OWASP ZAP basics
* Proxying, Intercepting, Replaying requests
* Subdomain discovery, port scanning, and sitemap discovery

**Phase 3 — Advanced Topics & Exploitation (6+ weeks)**

* Advanced SSRF -> RCE chains
* Deserialization vulnerabilities
* Business logic flaws discovery
* WebSockets, API auth abuse

**Phase 4 — Reporting & Responsible Disclosure (ongoing)**

* Clear, minimal reproducible PoCs
* Severity justifications, mitigation suggestions
* Workflow to communicate with programs

---

## 🧱 Hands-on Lab List (setup locally)

Start these in a VM or Docker environment.

1. **OWASP Juice Shop** — full of real-world-like flaws. (practice XSS, auth bypass, IDOR)
2. **Damn Vulnerable Web App (DVWA)** — classic learning tool for XSS/SQLi.
3. **WebGoat** — lesson-based web security training.
4. **NodeGoat / Vulnerable Docker images** — advanced app flows.
5. **PortSwigger Academy labs** — free interactive labs for each vulnerability.

> Tips: Use isolated VMs, snapshots, and never test against systems you don't have permission for.

---

## 🛠 Tooling Cheatsheet (quick commands)

**Recon**

* `amass enum -d example.com`
* `subfinder -d example.com -o subs.txt`
* `assetfinder --subs-only example.com`
* `gau --subs example.com` (get urls)

**Port scan**

* `nmap -sC -sV -oA scan/example.com 10.10.10.10`

**Directory brute force**

* `gobuster dir -u https://example.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`

**Simple curl PoC**

```bash
curl -i -s -k -X POST "https://target.com/path" \
  -H "Content-Type: application/json" \
  -d '{"comment":"<script>alert(1)</script>"}'
```

**Burp basics**

* Configure browser to use `127.0.0.1:8080` as proxy
* Turn on intercept → send to Repeater → modify → send

---

## 🔬 Practical Exercises (weekly)

**Week 1 — Foundations**

* Read HTTP/HTML/JS primer (20–30 pages)
* Lab: Submit a POST form via curl; capture with Burp

**Week 2 — XSS & Input Validation**

* Learn reflected vs stored XSS
* Lab: Find a reflected XSS in Juice Shop or PortSwigger lab
* Write a minimal PoC using curl and a screenshot

**Week 3 — SQLi & Auth**

* Learn SQLi types and boolean/time-based checks
* Lab: Practice blind SQLi on DVWA (use safe local instance)

**Week 4 — Recon & Automation**

* Set up `amass`, `subfinder`, `gau`, `ffuf`
* Map a sample target's subdomains and discover hidden paths

**Ongoing**

* Do 2 PortSwigger labs per week
* Write one public writeup (sanitized) per month

---

## 🧾 Report Template (files/report-template.md)

Use this for every report — keep it concise and reproducible.

```markdown
# [Title]

## Summary
One-line description and impact.

## Affected URL(s)
- https://example.com/path

## Steps to reproduce
1. Step 1 (curl / burp raw request)
2. Step 2

## PoC
- Minimal curl / script

## Impact
- Explain confidentiality/integrity/availability consequences

## Mitigation
- Suggested fix

## Timeline
- Found: YYYY-MM-DD
- Reported: YYYY-MM-DD
- Fixed: YYYY-MM-DD
```

---

## 🧭 Learning Resources (curated)

**Interactive**

* PortSwigger Academy — practical labs
* HackTheBox — web boxes & CTF-style challenges
* TryHackMe — guided rooms (web exploitation)

**Books / Guides**

* The Web Application Hacker's Handbook (classic)
* OWASP Top 10 (read and practice each item)

**Payload & Wordlists**

* PayloadsAllTheThings (playground of payloads)
* SecLists (wordlists for bruteforce)

**Programs to practice responsibly**

* HackerOne Hacktivity (read reports to learn)
* Bugcrowd University
* Public bug bounty programs with broad scope (read their rules carefully)

---

## ✅ Practice Etiquette & Rules

* Only test targets you have explicit permission to test.
* Respect scope, non-disclosure, and privacy rules.
* Do not exfiltrate or expose real user data.
* When in doubt, contact the program and ask.

---

## 📁 Suggested Repo Structure

```
/README.md                  <- This file
/report-template.md         <- Copy of reporting template
/labs/                     <- Lab notes and PoCs (sanitized)
/notes/                    <- Your learning notes and bookmarks
/scripts/                  <- Useful scripts and automation
/cheatsheets/              <- Quick reference files
```

---

## 🚀 Starter Projects & Mini-challenges (for your portfolio)

* Build a small vulnerable app (Flask/Express) with 3 known issues and fix them — write before/after reports.
* Automate subdomain discovery and save results to CSV.
* Create a Burp macro that finds an auth token and reports endpoints that leak it.
* Write a public, sanitized writeup of a PortSwigger or Juice Shop lab you solved.

---

## 🧩 Next Steps (do now)

1. Spin up Juice Shop in Docker:

```bash
docker run --rm -p 3000:3000 bkimminich/juice-shop
```

2. Open PortSwigger Academy and complete the "Reflected XSS" module.
3. Fork this repo and add one sanitized lab writeup into `/labs`.

---

## 📬 Need help or mentorship?

Open an Issue with the `help` label and describe what you're stuck on (include screenshots and error messages). Community members or mentors can provide pointers.

---

*Made with ❤️ for curious security learners.*
