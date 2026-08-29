# Methodology — GHDB Footprinting Walkthrough

This document expands on the step-by-step process used to complete both tasks in this lab.

## Task 1: Locating Exposed Security Cameras

1. **Open exploit-db.com** and navigate to the **GHDB** tab from the left sidebar.
2. **Search the term `cam`** in the GHDB quick search box. This surfaces a curated list of dorks specifically aimed at camera interfaces, login portals, and streaming endpoints.
3. **Copy a dork** (e.g. `intitle:"webcamXP" inurl:8080`) from the results list.
4. **Paste it into google.com** and run the search.
5. **Open each result** returned by Google and manually confirm:
   - The page loads and is *live*
   - It genuinely shows a camera interface (not a decoy, dead link, or unrelated page)
   - No credentials were required, or default/blank credentials were shown
6. **Log the finding**: URL, exact dork used, and credentials if visible.
7. **Repeat** across multiple dorks until 10 verified, live entries are collected.

## Task 2: Locating Open Directory Listings (Math PDFs)

1. **Open google.com** directly and search a directory-listing dork combined with subject keywords:
   `intitle:index.of "parent directory" mathematics pdf`
2. **Open each listing** returned and check whether it contains genuine, downloadable mathematics PDF content (not just a folder name match).
3. **Log the finding**: URL and dork used.
4. **Repeat** until 10 verified entries are collected.

## Verification Principles

- Only **passive** interaction is used — viewing a page returned by a search engine, never submitting credentials, brute-forcing, or attempting to bypass any access control.
- Each entry is manually opened and confirmed before being logged; unverified/dead search hits are discarded.
- The exact dork is preserved for every entry so the finding is reproducible and auditable.

## Why This Matters for Defenders

Every entry found this way represents information the *target itself* published to a public, crawlable location. The fix in each case is not "block Google" — it's:
- Placing authentication in front of camera/administration interfaces
- Disabling directory listing on web servers (`Options -Indexes` in Apache, equivalent in nginx/IIS)
- Auditing what a organization's own domains reveal via the same dorks, on a recurring basis
