<div align="center">

# 📂 Evidence & Findings

### Footprinting & Reconnaissance Attacks with GHDB

![Evidence](https://img.shields.io/badge/Type-Findings%20%26%20Screenshots-blueviolet?style=for-the-badge)
![Verified](https://img.shields.io/badge/All%20Entries-Manually%20Verified-success?style=for-the-badge)

**⬅️ [Back to README — Overview & Summary](README(1).md)**

</div>

---

## 📑 Table of Contents

- [Task 1 Walkthrough — Exposed Security Cameras](#-task-1-walkthrough--exposed-security-cameras)
- [Task 1 Findings Table](#-task-1-findings-table)
- [Task 2 Walkthrough — Math PDF Directories](#-task-2-walkthrough--math-pdf-directories)
- [Task 2 Findings Table](#-task-2-findings-table)
- [Verification Notes](#-verification-notes)

---

## 📸 Task 1 Walkthrough — Exposed Security Cameras

**Objective:** Find 10+ live, internet-accessible security camera interfaces exposed via GHDB dorks.
**Dork used:** `intitle:"webcamXP" inurl:8080`

<table>
<tr>
<td width="50%" valign="top">

### Step 1 — Open Exploit-DB
Navigate to [exploit-db.com](https://www.exploit-db.com), the official host of the GHDB.

<img src="assets/screenshots/task1-camera/01-exploitdb-home.png" width="100%">

</td>
<td width="50%" valign="top">

### Step 2 — Open the GHDB Menu
Expand the left sidebar and click **GHDB** to switch from the exploit archive into the dork database.

<img src="assets/screenshots/task1-camera/02-ghdb-menu.png" width="100%">

</td>
</tr>
<tr>
<td width="50%" valign="top">

### Step 3 — Search by Keyword
Type `cam` into the GHDB search box to filter down to camera/streaming-related dorks.

<img src="assets/screenshots/task1-camera/03-ghdb-search-cam.png" width="100%">

</td>
<td width="50%" valign="top">

### Step 4 — Copy a Candidate Dork
Right-click a promising entry and select **Copy link address** / copy the dork text.

<img src="assets/screenshots/task1-camera/04-copy-dork.png" width="100%">

</td>
</tr>
<tr>
<td width="50%" valign="top">

### Step 5 — Run the Dork on Google
Paste `intitle:"webcamXP" inurl:8080` into [google.com](https://www.google.com) and search.

<img src="assets/screenshots/task1-camera/05-google-search-dork.png" width="100%">

</td>
<td width="50%" valign="top">

### Step 6 — Review the Results
Google returns live camera interfaces indexed under this exact search pattern.

<img src="assets/screenshots/task1-camera/06-google-results.png" width="100%">

</td>
</tr>
</table>

### Step 7 — Open & Verify
Each result was opened and manually confirmed live before logging.

<p align="center">
<img src="assets/screenshots/task1-camera/07-live-camera-verified.png" width="75%">
<br><em>Confirmed: a live, unauthenticated <code>webcamXP 5</code> feed at <code>109.233.191.130:8080</code>.</em>
</p>

**➡️ [Jump to Task 1 findings table](#-task-1-findings-table)**

---

## 📋 Task 1 Findings Table

| No. | Link | Relevant Dork | Username / Password |
|:---:|------|----------------|:---:|
| 1 | `http://122.116.41.8:8080/` | `intitle:"webcamXP" inurl:8080` | --- |
| 2 | `http://109.233.191.130:8080/` | `intitle:"webcamXP" inurl:8080` | --- |
| 3 | `http://139.64.168.120` | `intitle:"webcamXP" inurl:8080` | --- |
| 4 | `http://72.199.200.5` | `intitle:"webcamXP" inurl:8080` | --- |
| 5 | `http://104.8.232.105` | `intitle:"webcamXP" inurl:8080` | --- |
| 6 | `http://75.149.26.30` | `intitle:"webcamXP" inurl:8080` | --- |
| 7 | `http://85.93.53.175` | `intitle:"webcamXP" inurl:8080` | --- |
| 8 | [insecam.org/en/view/212604](http://www.insecam.org/en/view/212604/) | `intitle:"webcamXP" inurl:8080` | --- |
| 9 | [insecam.org/en/view/167618](http://www.insecam.org/en/view/167618/) | `intitle:"webcamXP" inurl:8080` | --- |
| 10 | [insecam.org/en/view/635627](http://www.insecam.org/en/view/635627/) | `intitle:"webcamXP" inurl:8080` | --- |
| 11 | [insecam.org/en/view/932097](http://www.insecam.org/en/view/932097/) | `intitle:"webcamXP" inurl:8080` | --- |
| 12 | [insecam.org/en/view/997691](http://www.insecam.org/en/view/997691/) | `intitle:"webcamXP" inurl:8080` | --- |
| 13 | [insecam.org/en/view/570197](http://www.insecam.org/en/view/570197/) | `intitle:"webcamXP" inurl:8080` | --- |
| 14 | [insecam.org/en/view/818703](http://www.insecam.org/en/view/818703/) | `intitle:"webcamXP" inurl:8080` | --- |
| 15 | [insecam.org/en/view/886985](http://www.insecam.org/en/view/886985/) | `intitle:"webcamXP" inurl:8080` | --- |

> 📝 Entries 8–15 route through [insecam.org](http://www.insecam.org), a public directory that aggregates unsecured, publicly-shared webcam feeds discovered via the same style of dork.

<details>
<summary>📎 Additional camera-related dorks worth practicing</summary>

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

</details>

**⬆️ [Back to top](#-evidence--findings) · ⬅️ [Back to README](README.md)**

---

## 📚 Task 2 Walkthrough — Math PDF Directories

**Objective:** Find 10+ publicly indexed directory listings containing downloadable mathematics PDFs.
**Dork used:** `intitle:index.of "parent directory" mathematics pdf`

<table>
<tr>
<td width="50%" valign="top">

### Step 1 — Run the Dork on Google
The directory-listing dork is simple enough to run directly on Google, combined with the subject keyword `mathematics pdf`.

<img src="assets/screenshots/task2-pdf/01-google-search-dork.png" width="100%">

*(screenshot pending — see [note below](#️-screenshots-pending-for-task-2))*

</td>
<td width="50%" valign="top">

### Step 2 — Review the Results
Google surfaces multiple `Index of /...` style pages — the tell-tale sign of an exposed directory listing.

<img src="assets/screenshots/task2-pdf/02-google-results.png" width="100%">

*(screenshot pending)*

</td>
</tr>
<tr>
<td width="50%" valign="top">

### Step 3 — Open the Directory Listing
Opening a result shows the raw file index — e.g. `Index of /Maths/` — with mathematics PDFs and related files listed directly.

<img src="assets/screenshots/task2-pdf/03-directory-listing.png" width="100%">

*(screenshot pending)*

</td>
<td width="50%" valign="top">

### Step 4 — Open & Verify a PDF
One file from the listing is opened to confirm it's a genuine, readable mathematics ebook.

<img src="assets/screenshots/task2-pdf/04-pdf-opened.png" width="100%">

*(screenshot pending)*

</td>
</tr>
</table>

> #### ⚠️ Screenshots pending for Task 2
> The 4 Task 2 screenshots were uploaded using the same filenames (`Step_1.png`–`Step_4.png`) as the Task 1 camera screenshots, so the second upload overwrote the first on disk — only the camera set survived. **Re-upload the 4 math/PDF screenshots with distinct names** (e.g. `01-google-search-dork.png`, `02-google-results.png`, `03-directory-listing.png`, `04-pdf-opened.png`) into `assets/screenshots/task2-pdf/` and this section will render them exactly like Task 1 above — no other changes needed.

**➡️ [Jump to Task 2 findings table](#-task-2-findings-table)**

---

## 📋 Task 2 Findings Table

| No. | Link | Relevant Dork | Username / Password |
|:---:|------|----------------|:---:|
| 1 | [skylineuniversity.ac.ae/pdf/math](https://www.skylineuniversity.ac.ae/pdf/math/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 2 | [erewhon.superkuh.com/library/Math](http://erewhon.superkuh.com/library/Math/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 3 | [jsoftware.com/books/pdf](https://www.jsoftware.com/books/pdf/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 4 | [education.giakonda.org.uk/Maths](https://education.giakonda.org.uk/Maths/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 5 | [unm.edu/~megrad/Math](http://www.unm.edu/~megrad/Math/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 6 | [netlib.org/math/docpdf](https://www.netlib.org/math/docpdf/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 7 | [pcwww.liv.ac.uk/maths](http://pcwww.liv.ac.uk/maths/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 8 | [math.dartmouth.edu/~carlp/PDF](https://www.math.dartmouth.edu/~carlp/PDF/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 9 | [inis.jinr.ru Math Encyclopedia](http://inis.jinr.ru/sl/vol2/Mathematics/Math.Encyclopedia/Pdf/) | `intitle:index.of "parent directory" mathematics pdf` | --- |
| 10 | [wvfa.org/pdf/projectLearningTree](http://www.wvfa.org/pdf/projectLearningTree/) | `intitle:index.of "parent directory" mathematics pdf` | --- |

**Example verified listing (`education.giakonda.org.uk/Maths/`):**

| File | Last Modified | Size |
|---|---|---|
| Additional_Mathematics__Pure_and_Applied.pdf | 2022-04-02 | 25,147 KB |
| FINALISED GRADE 10-12 ADDITIONAL MATHS 20 AUGUST 2013... | 2022-04-02 | 875 KB |
| GRADE 2 NUMERACY WEEK 5 TERM THREE.pdf | 2022-10-05 | 145 KB |
| GRADE 8 AND 9 MATHEMATICS SYLLABI.pdf | 2022-04-02 | 704 KB |
| math6.pdf | 2022-04-02 | 94,330 KB |
| math7.pdf | 2022-04-02 | 478,915 KB |

> One of the PDFs (*Additional Mathematics — Pure & Applied*, 6th Edition, by J.F. Talbert & H.H. Heng) was opened directly in-browser to confirm it renders as a genuine, readable 536-page textbook — verifying the listing is a real, live exposure and not a decoy.

**⬆️ [Back to top](#-evidence--findings) · ⬅️ [Back to README](README.md)**

---

## ✅ Verification Notes

- Only **passive** interaction was used — viewing a page returned by a search engine, never submitting credentials, brute-forcing, or bypassing access controls.
- Every entry was manually opened and confirmed live before being logged; dead or irrelevant search hits were discarded.
- The exact dork is preserved for every entry so each finding is reproducible and auditable.
- No login credentials were required for any Task 1 or Task 2 entry — all interfaces and directories were open by default (`---` in the Username/Password column).

### Why this matters for defenders

Every entry found this way represents information the *target itself* published to a public, crawlable location. The fix in each case is not "block Google" — it's:

- Placing authentication in front of camera/administration interfaces
- Disabling directory listing on web servers (`Options -Indexes` in Apache, equivalent in nginx/IIS)
- Periodically auditing what an organization's own domains reveal via the same dorks

---

<div align="center">

**⬅️ [Back to README — Overview, Objective & Summary](README.md)**

</div>
