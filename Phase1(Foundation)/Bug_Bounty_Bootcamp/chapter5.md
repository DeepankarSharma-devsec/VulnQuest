# 🕵️ Bug Bounty Bootcamp: Chapter 5 — Reconnaissance

> *My deep-dive notes from Chapter 5 of Vickie Li’s Bug Bounty Bootcamp — focused on gathering intel, building recon scripts, and mapping the attack surface effectively.*

---

## 📚 Why Recon Matters

I learned that recon is the **foundation** of bug bounty hunting. It’s all about understanding the target’s **attack surface** before deciding how to approach it.

- If an app doesn’t use PHP → no point testing for PHP-specific bugs.
- If a company doesn’t use AWS → don’t waste time on S3 bucket tests.

> Recon separates **good hackers** from time-wasters.

---

## 🏃 Manual Walkthrough

Before firing up tools, it’s crucial to **manually explore** the app:

- Click every link, access all features, check odd corners.
- Create accounts at different privilege levels.
- Example: In Slack, create multiple admins, owners, and channel members to see various views.
- Result: Understand **how data flows**, where user inputs happen, and get a sense of potential attack points.

---

## 🔎 Google Dorking

I saw how advanced Google search (dorking) can reveal:

- Hidden admin portals
- Leaked password files
- Forgotten debug endpoints

Useful Google operators:

| Operator | Purpose |
|-----------|---------|
| `site:` | limit to specific domain |
| `inurl:` | search URL text |
| `filetype:` | find specific file types |
| `intitle:` | search page titles |
| `cache:` | view cached version |

---

## 🌐 Scope Discovery

The chapter emphasized finding **every domain, subdomain, and IP** a company owns.

- Tools & methods:
  - WHOIS / reverse WHOIS lookups
  - Checking IP address ranges
  - Certificate transparency logs (crt.sh, Censys)
  - Reverse IP lookups

---

## 🌍 WHOIS & IP Discovery

- WHOIS: get domain ownership data → find linked contact info, related assets.
- Reverse WHOIS: search by keyword → find other domains owned by same entity.
- ViewDNS.info → handy tool for reverse IP and WHOIS checks.

---

## 🔐 Certificate Parsing

SSL/TLS certificates often list related domains/subdomains in their **Subject Alternative Name (SAN)** fields.

- Tools:
  - crt.sh → view in browser or download as JSON.
  - Censys / Cert Spotter → alternative sources.

---

## 🛰️ Subdomain Enumeration

A big part of recon:

- Tools:
  - Sublist3r → queries engines + public datasets
  - SubBrute → brute-forces subdomains
  - Amass → combines multiple methods
  - Gobuster → brute-forces with wordlists

- Wordlists:
  - SecLists (Daniel Miessler) → comprehensive collection
  - Commonspeak2 → generate lists from fresh public data

> Combine lists → remove duplicates → cover more ground.

---

## 📚 Service Enumeration & Dir Brute-Forcing

Find hidden directories, endpoints, and services:

- Dirsearch → brute-force directories.
- Gobuster → same idea, supports DNS & directories.
- Spidering → crawl app automatically (careful with large targets).

---

## 👀 Third-Party & GitHub Recon

Check GitHub for:

- Exposed tokens
- Internal config files
- Leaked credentials

Tip: Use advanced GitHub search and recon tools that parse GitHub repos for secrets.

---

## 🤫 Sneaky OSINT Tricks

- Find company employee info on LinkedIn.
- Use Shodan & Censys to discover exposed services/devices.
- Find forgotten dev subdomains or test apps.

---

## 🛠️ Tech Stack Fingerprinting

Identify underlying tech → target known vulnerabilities:

- Analyze HTTP headers, cookies, server responses.
- Tools: Wappalyzer, BuiltWith.

---

## ⚙️ Writing Recon Scripts (Bash)

The chapter walks through **building my own bash scripts** to automate recon.

Key elements:

1. **Basic Bash Syntax** → variables, loops, conditions.
2. **Functions** → reuse code.
3. **Saving Output** → redirect to files, timestamp reports.
4. **Regex & Grep** → parse tool outputs efficiently.
5. **Combining Tools** → build master recon reports.

---

## 📑 Master Report Example

By combining:

- Nmap scans
- Dirsearch results
- Certificate parsing via crt.sh (with `jq`)

…I can generate a **single report** summarizing findings. This becomes the foundation of future tests.

---

## ⏰ Automation & Scheduling

Use `cron` jobs to:

- Schedule recon scans nightly
- Auto-push results to GitHub
- Alert on new discoveries

---

## 🔑 Recon APIs

Many tools (Shodan, LinkedIn, Censys) offer APIs. Integrate them in scripts → fetch fresh data automatically.

---

## 🎯 Starting Attacks

Key point: recon isn’t the goal — it **feeds the attacks**.

- Prioritize sensitive features (credit cards, passwords).
- Target bugs related to discovered tech stack.
- Monitor continuously — targets change over time.

---

## ✅ Takeaways

> “Recon never stops.”

- Build solid recon foundation → feed smarter testing.
- Automate where possible.
- Write notes & keep scripts organized.

---

### 🚀 Next: Chapter 6 — Cross-Site Scripting

Ready to dive into **my first major vulnerability class**: XSS — mechanisms, payloads, bypasses, and hunting real bugs. Let’s go!
