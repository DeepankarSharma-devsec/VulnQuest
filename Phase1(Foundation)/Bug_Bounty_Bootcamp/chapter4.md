# 🖥️ Bug Bounty Bootcamp: Chapter 4 — Setting Up My Hacking Environment

> *My detailed notes after reading Chapter 4 of Vickie Li’s Bug Bounty Bootcamp, focused on building a solid hacking environment and intercepting traffic effectively.*

---

## 🗃️ Why Environment Setup Matters

Before hunting bugs, I realized I need a **robust, reliable environment**. Setting things up right avoids confusion, data loss, and makes me more efficient when I’m deep into testing.

---

## 🐧 Picking the Right OS

I learned the recommended OS is **Linux** — especially **Kali Linux** or **Parrot Security OS** — because they come preinstalled with hacking tools.

- **Kali Linux**:
  - Preloaded with Burp Suite, Gobuster, Wfuzz, DirBuster, etc.
  - Free download: [kali.org/downloads](https://www.kali.org/downloads/)

If I’m using **macOS** or **Windows**, I can still install tools, but it takes more effort (and the book focuses mostly on Linux setups).

---

## 🧭 Setting Up the Core Tools: Browser + Proxy

### 🌐 Browser
- I should have **two browsers**:
  1. One dedicated to hacking the target app.
  2. One for general browsing/research (to isolate traffic).

- **Firefox** is recommended because it’s easiest to configure with proxies and certificates.

---

### 🔥 Proxy (Burp Suite)

Burp Suite is the backbone of my setup — it sits between the browser and the server, letting me intercept, inspect, and modify requests.

Without a proxy:
- Browser ↔️ Server (automatic communication, no visibility)

With a proxy:
- Browser → **Proxy (Burp)** → Server
- I can capture, change, or drop requests before they reach the server.

---

## 🖥️ Launching Burp’s Embedded Browser

Burp has an **embedded browser**. By using Burp’s “Open Browser” button under the Proxy tab, traffic is **automatically routed** through Burp — no manual configuration needed.

This is the **simplest way** to get started and avoid headaches with certificates.

---

## 🛠️ Manual Setup: Firefox + Burp Proxy

If I want to set up my own browser:

1️⃣ Download Burp Suite and Firefox.

2️⃣ In Firefox:
   - Preferences → Network Settings → Manual Proxy → set HTTP Proxy to `127.0.0.1` and Port to `8080`.

3️⃣ Burp listens by default on `127.0.0.1:8080`.

4️⃣ Install Burp’s CA certificate into Firefox (so I can intercept HTTPS traffic without errors).

---

## 🔎 Burp Suite Modules I Need to Master

This chapter walked me through Burp’s main tools:

- **Proxy**: Intercept and modify traffic in real-time.
- **Intruder**: Automate attacks by sending many payloads (useful for brute-force or fuzzing).
- **Repeater**: Manually tweak and resend single requests to analyze how the server responds.
- **Decoder**: Convert data formats (Base64, URL-encoded, hex) — crucial for debugging encoded payloads.
- **Comparer**: Diff tool to spot subtle differences in requests or responses.

---

## 💾 Saving Sessions & Notes

- Burp can **save session files** → helps avoid losing progress.
- I should **frequently save state** (especially before big fuzzing runs).
- Keeping **detailed notes** on:
  - Parameters tested
  - Payloads sent
  - Observations and potential leads

… makes writing reports and revisiting tests much easier.

---

## 📝 Tips From the Chapter

- Use a dedicated hacking machine (physical or virtual).
- Update Burp Suite regularly to patch bugs and vulnerabilities.
- Always test in a controlled environment to avoid legal trouble.

---

## ✅ My Key Takeaways

> “A well-organized environment is half the battle.”

- Burp Suite is my Swiss Army knife — I need to master Proxy, Intruder, Repeater, Decoder, and Comparer.
- Save work frequently and take organized notes.
- Linux (Kali) + Firefox + Burp is the recommended beginner-friendly stack.

---

### 🚀 Next Up: Chapter 5 — Reconnaissance

I’m excited to learn about gathering targets, endpoints, and mapping attack surfaces. Time to move from setup → **action**!
