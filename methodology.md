# 🧭 Methodology — GHDB Footprinting Walkthrough

> ⬅️ Back to [main README](../README.md) for the objective, findings tables, and repo overview. This page is the detailed, narrated version of the same 7-step process summarized there.

---

## Overview

Both tasks in this lab follow an identical passive-recon loop. Only the **keyword** searched inside GHDB and the **dork** applied on Google differ between them.

| | Task 1 — Cameras | Task 2 — Math PDFs |
|---|---|---|
| GHDB keyword | `cam` | `index of` |
| Dork used | `intitle:"webcamXP" inurl:8080` | `intitle:index.of "parent directory" mathematics pdf` |
| Target artifact | Live camera interface | Open directory listing with PDFs |
| Screenshots | [`assets/screenshots/task1-camera/`](../assets/screenshots/task1-camera/) ✅ | [`assets/screenshots/task2-pdf/`](../assets/screenshots/task2-pdf/) ⏳ |

---

## Step-by-Step: Task 1 (Exposed Cameras)

### Step 1 — Open Exploit-DB
Navigate to [exploit-db.com](https://www.exploit-db.com). This is the official home of both the general exploit archive and the GHDB.

<p align="center"><img src="../assets/screenshots/task1-camera/01-exploitdb-home.png" width="85%"></p>

### Step 2 — Open the GHDB Menu
Expand the left-hand sidebar and click **GHDB** to switch from the exploit listing view into the dork database.

<p align="center"><img src="../assets/screenshots/task1-camera/02-ghdb-menu.png" width="85%"></p>

### Step 3 — Search GHDB by Keyword
Type `cam` into the GHDB search box. This filters thousands of entries down to dorks specifically aimed at camera interfaces, login portals, and streaming endpoints.

<p align="center"><img src="../assets/screenshots/task1-camera/03-ghdb-search-cam.png" width="85%"></p>

### Step 4 — Copy a Candidate Dork
Right-click a promising dork entry and select **Copy link address** (or copy the dork text directly) to place it on the clipboard.

<p align="center"><img src="../assets/screenshots/task1-camera/04-copy-dork.png" width="85%"></p>

### Step 5 — Run the Dork on Google
Paste the copied dork — e.g. `intitle:"webcamXP" inurl:8080` — into [google.com](https://www.google.com) and search.

<p align="center"><img src="../assets/screenshots/task1-camera/05-google-search-dork.png" width="85%"></p>

### Step 6 — Review the Results
Google returns a list of pages matching the dork. Scan titles and URLs for likely live hits before clicking through.

<p align="center"><img src="../assets/screenshots/task1-camera/06-google-results.png" width="85%"></p>

### Step 7 — Open & Verify
Open a result and manually confirm:
- The page **loads** and is genuinely **live**
- It shows a real camera interface (not a decoy or dead link)
- Whether credentials were required, default, or blank

<p align="center">
<img src="../assets/screenshots/task1-camera/07-live-camera-verified.png" width="70%">
<br><em>A live, unauthenticated <code>webcamXP</code> feed — confirmed and logged.</em>
</p>

**Repeat Steps 3–7** across additional dorks until 10 verified, live entries are collected → logged in the [Task 1 table](../README.md#-task-1--exposed-security-cameras) in the main README.

---

## Step-by-Step: Task 2 (Open Directory Listings — Math PDFs)

The same loop applies, starting directly from Google since the target dork (`intitle:index.of "parent directory" mathematics pdf`) is simple enough to run without first browsing GHDB's UI.

1. **Search Google directly** with the directory-listing dork combined with subject keywords.
2. **Review the results list** — look for `Index of /...` style titles, which indicate an exposed directory listing rather than a normal web page.
3. **Open a listing** and confirm it contains genuine, downloadable mathematics PDF files (not just a folder name coincidentally matching).
4. **Log the finding**: URL and exact dork used.
5. **Repeat** until 10 verified entries are collected → logged in the [Task 2 table](../README.md#-task-2--downloadable-mathematics-ebooks).

> 🖼️ **Screenshots pending:** drop your 4 Task 2 screenshots (Google search → results list → directory listing → opened PDF) into [`assets/screenshots/task2-pdf/`](../assets/screenshots/task2-pdf/) following the naming guide there, and this section will display them the same way Task 1 does above.

---

## Verification Principles

- Only **passive** interaction is used — viewing a page returned by a search engine, never submitting credentials, brute-forcing, or attempting to bypass access controls.
- Every entry is manually opened and confirmed before being logged; unverified or dead search hits are discarded.
- The exact dork is preserved for every entry so the finding is reproducible and auditable.

## Why This Matters for Defenders

Every entry found this way represents information the *target itself* published to a public, crawlable location. The fix in each case is not "block Google" — it's:

- Placing authentication in front of camera/administration interfaces
- Disabling directory listing on web servers (`Options -Indexes` in Apache, equivalent in nginx/IIS)
- Periodically auditing what an organization's own domains reveal via the same dorks

---

⬅️ Back to [main README](../README.md)
