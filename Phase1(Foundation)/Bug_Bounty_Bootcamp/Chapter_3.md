# 🌐 Bug Bounty Bootcamp: Chapter 3 — How the Internet Works (And Why I Needed to Learn It)

> *This chapter helped me finally understand what’s happening under the hood when I type a URL into my browser — and why this knowledge is critical for hacking.*

---

## 🧭 Why This Chapter Mattered

Before diving into real bug hunting, this chapter gave me a proper walkthrough of how the internet actually works. Turns out, many web vulnerabilities stem from how these foundational components are implemented — or misimplemented.

---

## 🔁 The Client-Server Model

I learned that:
- The **browser is a client**, and the **web app/server** is the responder.
- When I visit a site, I’m actually asking a server to send back files — HTML, CSS, JS, images, and videos.
- APIs are just servers responding to programmatic requests instead of browsers.

It's all just **request + response** — but understanding it is the key to manipulating it.

---

## 🧭 DNS: The Internet's Address Book

Next, I found out how **DNS (Domain Name System)** works:
- Every device online has an **IP address** (like `216.58.192.132` for Google).
- DNS translates human-friendly domains like `www.google.com` into these IPs.
- Without DNS, we’d be memorizing IPs like it's 1998. No thanks.

---

## 🔌 Internet Ports

- Devices use **ports** (0–65535) to offer different services.
- Example:
  - Port 80 = HTTP
  - Port 443 = HTTPS
  - Port 25 = Email
- When I connect to a server, I'm *really* saying: “Talk to me on this specific service line.”

---

## 📡 HTTP Requests and Responses

This was 🔥 — because as a bug bounty hunter, I’ll be reading and manipulating these all the time.

### A basic GET request looks like this:
```
GET / HTTP/1.1
Host: www.google.com
User-Agent: Mozilla/5.0
Accept: text/html
```

It has:
- **Request line** (`GET / HTTP/1.1`)
- **Headers** (e.g., `User-Agent`, `Host`)
- Optional **body** (mostly for `POST`, `PUT`, etc.)

### Responses return:
- A **status code** (200 = OK, 403 = forbidden, 500 = server error)
- **Headers** (like `Set-Cookie`, `Content-Type`)
- **Body** — the actual HTML or API data

---

## 🔐 Internet Security Controls

### 🧬 Content Encoding
Data isn’t always plain text. It might be:
- **Base64** – for images, JWTs
- **Hex** – readable but bulky
- **URL-encoded** – `%20` for space, etc.

Burp Suite and tools like CyberChef help decode this.

---

## 🍪 Session Management & Cookies

Here’s how the web "remembers" me:
1. I log in → Server creates a session → Sends back a **session ID** as a cookie.
2. My browser stores it and sends it with every request.
3. That cookie = my identity on that website.

When I log out, the session ID is invalidated.

---

## 🔐 Token-Based Authentication (vs Cookies)

Some sites don’t use sessions. They use **tokens**, usually JSON Web Tokens (JWTs).

A **JWT** has:
- Header: algorithm info
- Payload: user data
- Signature: to verify integrity

But if JWTs are **not implemented securely**, they can be decoded, forged, or tampered with — which can lead to account takeovers. Yikes.

---

## 🚫 Same-Origin Policy (SOP)

This was a game-changer:

SOP says:
> Scripts from Site A can’t access content from Site B unless they share the same protocol, hostname, and port.

So even if a malicious site tricks my browser into sending a request to `onlinebank.com`, SOP **prevents it from reading the response** — which is a massive safeguard.

---

## 💡 Pro Tip: Learn to Code

Vickie recommends:
- **Learn Python** (automation, scripting)
- **Read JavaScript** (client-side logic, hidden endpoints, secrets)

Her suggestions:
- Codecademy
- *Learn Python the Hard Way*
- *Eloquent JavaScript*

---

## 🧠 Final Thoughts

> “You can’t hack what you don’t understand.”

This chapter didn’t just prep me for the tech — it taught me the logic, flow, and assumptions behind how the web works.

Next up: setting up my hacking environment with Burp Suite!