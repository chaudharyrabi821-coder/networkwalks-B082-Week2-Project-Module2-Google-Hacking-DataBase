# 🔍 Footprinting & Reconnaissance with GHDB

<div align="center">

![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Ethical%20Hacking-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Educational-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-Educational%20Use%20Only-yellow?style=for-the-badge)

**Google Hacking Database (GHDB) — Passive Recon Lab**

*Week 2 | Project Module 2 — Networkwalks Cybersecurity & Ethical Hacking Track*

</div>

---

## ⚠️ Liability Disclaimer

> These materials are for **education and research purposes only**. This repository documents a passive OSINT/footprinting exercise performed entirely through publicly indexed Google search results. No target was scanned, logged into, or otherwise interacted with beyond opening a public search result in a browser.
>
> Hacking is only legal when:
> - You test a device or network **you own** or that is in **your lab environment**
> - You have **written, documented permission** from the owner
> - You are working as a security professional under a **signed agreement with an agreed scope**
>
> Everything outside these cases is illegal. Misuse can lead to criminal charges, fines, job loss, and a permanent record — **you are solely responsible for how you use this information.**

---

## 📖 Background

**GHDB (Google Hacking Database)** is a large, community-maintained collection of ready-made Google search queries — known as **"Google dorks"** — hosted on [exploit-db.com](https://www.exploit-db.com/google-hacking-database).

Dorks combine ordinary Google search operators (`intitle:`, `inurl:`, `intext:`, `index.of`, etc.) in clever ways to surface information that a website has *accidentally* left publicly indexed — things like exposed camera feeds, open directories, login portals, configuration files, and leaked documents.

Because GHDB relies entirely on Google's own index, this is one of the **quietest forms of footprinting**: the target is never directly contacted or scanned, and has no way of knowing it was found this way. It is used by:
- **Attackers**, to build a picture of a target's exposed surface before ever touching it
- **Defenders & researchers**, to discover what their own organization is leaking and fix it before someone else finds it

> 💡 **Key takeaway:** the less an organization exposes to Google's crawlers, the smaller its attack surface becomes.

---

## 🎯 Objective

Using GHDB dorks and Google search alone (no direct target interaction), this lab:

1. Identifies **10 live, publicly exposed security camera interfaces**
2. Identifies **10 publicly indexed directory listings** hosting downloadable mathematics PDFs

Each finding is verified manually and logged with the exact dork used to surface it.

---

## 🛠️ Methodology

### Step 1 — Open Exploit-DB
Navigate to [exploit-db.com](https://www.exploit-db.com), the official host of the GHDB.

![Step 1 - Exploit-DB homepage](assets/screenshots/step1-exploitdb-home.png)

### Step 2 — Open the GHDB Menu
Click **GHDB** in the left-hand sidebar to switch from the exploit listing to the dork database.

![Step 2 - GHDB menu](assets/screenshots/step2-ghdb-menu.png)

### Step 3 — Search for a Keyword
Use the GHDB quick-search box to filter dorks by keyword (e.g. `cam` for Task 1, `index of` for Task 2).

![Step 3 - GHDB keyword search](assets/screenshots/step3-ghdb-search.png)

### Step 4 — Copy a Candidate Dork
Right-click a dork in the results list and copy it to the clipboard.

![Step 4 - Copying a dork](assets/screenshots/step4-copy-dork.png)

### Step 5 — Run the Dork on Google
Paste the copied dork into [google.com](https://www.google.com) and execute the search.

![Step 5 - Google search with dork](assets/screenshots/step5-google-search.png)

### Step 6 — Open & Verify Each Result
Click through the search results one by one and confirm each is live and genuinely matches the target criteria before logging it.

![Step 6 - Verifying a result](assets/screenshots/step6-verify-result.png)

### Step 7 — Repeat & Log Findings
Repeat Steps 3–6 across additional dorks until 10 verified entries are collected, logging the link and exact dork used for each.

| Step | Action |
|------|--------|
| 1 | Open [exploit-db.com](https://www.exploit-db.com) |
| 2 | Navigate to the **GHDB** section from the left-hand menu |
| 3 | Search GHDB for a relevant keyword (e.g. `cam`, `index of`) |
| 4 | Copy a candidate dork from the results list |
| 5 | Paste the dork into **google.com** and run the search |
| 6 | Open each result and manually verify it is live and matches the target criteria |
| 7 | Repeat until 10 verified results are collected per task, logging the link + dork used |

---

## 📸 Task 1 — Exposed Security Cameras

**Goal:** Find 10 live, internet-accessible security camera interfaces exposed via GHDB dorks.

![Example - live camera interface found via dork](assets/screenshots/task1-example-camera.png)
*Example: a `webcamXP` interface reached via `intitle:"webcamXP" inurl:8080`, confirming the dork's validity.*

| No. | Link | Relevant Dork | Username / Password |
|----|------|----------------|----------------------|
| 1 | `http://122.116.41.8:8080/` | `intitle:"webcamXP" inurl:8080` | --- |
| 2 | `http://109.233.191.130` | `intitle:"webcamXP" inurl:8080` | — |
| 3 | `http://139.64.168.120` | `intitle:"webcamXP" inurl:8080` | — |
| 4 | `http://72.199.200.5` | `intitle:"webcamXP" inurl:8080` | — |
| 5 | `http://104.8.232.105` | `intitle:"webcamXP" inurl:8080` | — |
| 6 | `http://75.149.26.30` | `intitle:"webcamXP" inurl:8080` | — |
| 7 | `http://85.93.53.175` | `intitle:"webcamXP" inurl:8080` | — |
| 8 | [insecam.org/en/view/212604](http://www.insecam.org/en/view/212604/) | `intitle:"webcamXP" inurl:8080` | — |
| 9 | [insecam.org/en/view/167618](http://www.insecam.org/en/view/167618/) | `intitle:"webcamXP" inurl:8080` | — |
| 10 | [insecam.org/en/view/635627](http://www.insecam.org/en/view/635627/) | `intitle:"webcamXP" inurl:8080` | — |

> 📝 *Note: entries 8–10 route through [insecam.org](http://www.insecam.org), a public directory that aggregates unsecured/publicly-shared webcam feeds discovered via similar dork techniques.*

### Additional camera-related dorks worth practicing

```text
allintitle: "Network Camera NetworkCamera"
intitle:"EvoCam" inurl:"webcam.html"
intitle:"Live View / - AXIS"
intitle:"LiveView / - AXIS" | inurl:view/view.shtml
inurl:indexFrame.shtml "Axis Video Server"
inurl:axis-cgi/jpg
inurl:"MultiCameraFrame?Mode=Motion"
inurl:/view.shtml
inurl:/view/index.shtml
"my webcamXP server!"
```

---

## 📚 Task 2 — Downloadable Mathematics eBooks (PDF)

**Goal:** Find 10 publicly indexed directory listings containing downloadable mathematics PDFs.

| No. | Link | Relevant Dork | Username / Password |
|----|------|----------------|----------------------|
| 1 | [skylineuniversity.ac.ae/pdf/math](https://www.skylineuniversity.ac.ae/pdf/math/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 2 | [erewhon.superkuh.com/library/Math](http://erewhon.superkuh.com/library/Math/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 3 | [jsoftware.com/books/pdf](https://www.jsoftware.com/books/pdf/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 4 | [education.giakonda.org.uk/Maths](https://education.giakonda.org.uk/Maths/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 5 | [unm.edu/~megrad/Math](http://www.unm.edu/~megrad/Math/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 6 | [netlib.org/math/docpdf](https://www.netlib.org/math/docpdf/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 7 | [pcwww.liv.ac.uk/maths](http://pcwww.liv.ac.uk/maths/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 8 | [math.dartmouth.edu/~carlp/PDF](https://www.math.dartmouth.edu/~carlp/PDF/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 9 | [inis.jinr.ru Math Encyclopedia](http://inis.jinr.ru/sl/vol2/Mathematics/Math.Encyclopedia/Pdf/) | `intitle:index.of "parent directory" mathematics pdf` | — |
| 10 | [wvfa.org/pdf/projectLearningTree](http://www.wvfa.org/pdf/projectLearningTree/) | `intitle:index.of "parent directory" mathematics pdf` | — |

---

## 🧠 Why GHDB Matters in Footprinting

Reconnaissance is the first stage of every real attack. Before touching a target, an attacker quietly builds a full picture of it using only public information — and Google is one of the richest sources of that information. GHDB turns ordinary Google search into a precise recon tool that surfaces exposed cameras, open folders, backup files, login portals, and leaked documents that owners never meant to publish.

Because everything comes straight from Google's own index, the target is never directly contacted — making GHDB one of the quietest and hardest-to-detect forms of footprinting. The same dorks used offensively are used defensively: organizations can search their own domains to discover and lock down what they're inadvertently leaking.

---

## 📂 Repository Structure

```
ghdb-footprinting-lab/
├── README.md                       # This file
├── docs/
│   └── methodology.md               # Extended write-up of the recon process
└── assets/
    └── screenshots/                  # Step-by-step screenshots
        ├── step1-exploitdb-home.png
        ├── step2-ghdb-menu.png
        ├── step3-ghdb-search.png
        ├── step4-copy-dork.png
        ├── step5-google-search.png
        ├── step6-verify-result.png
        └── task1-example-camera.png
```

> See [`assets/screenshots/README.md`](assets/screenshots/README.md) for exactly what to capture for each filename.

---

## 🔗 References

- [Exploit-DB — Google Hacking Database](https://www.exploit-db.com/google-hacking-database)
- [Networkwalks Academy](https://www.networkwalks.com)

---

## 📬 Contact

Questions, comments, and suggestions are welcome.

**Networkwalks Academy** — Cisco CCNA · Cybersecurity · Ethical Hacking · Python · Linux · AI
📧 info@networkwalks.com

---

<div align="center">

*This repository is a training artifact from a structured cybersecurity course and is shared strictly for educational demonstration of OSINT/footprinting methodology.*

</div>
