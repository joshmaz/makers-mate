
# Website-to-Knowledge Ingestion Playbook

**Goal:** Keep web browsing **off** while giving Makers Mate high-quality, up-to-date content from official sources.  
**Outcome:** Clean, reviewable Markdown/PDF files in `/knowledge` that you can also upload to the GPT.

---

## 🔎 What to Ingest (Priority Order)

1. **Official policies & safety** (Bylaws, shop rules, training checklists)
2. **Procedures & SOPs** (step-by-step how-tos, onboarding)
3. **Stable reference** (class descriptions, equipment specs that rarely change)
4. **Public FAQs** (member-facing and visitor-facing info)

> Avoid personal data and anything not intended for public/member consumption.

---

## 🧱 File Shape & Size

- Prefer **Markdown** (`.md`) for text and lists; **PDF** for “print views” or forms.
- Keep each file **focused** (2–5 pages or ~2–5k words). Split long pages into sections.
- At the top of every file, include a metadata header:
  - **Title:**  
  - **Source URL:**  
  - **Captured:** YYYY-MM-DD  
  - **Owner/Contact:** (Shop Captain or committee)  
  - **Notes:** (scope, caveats)

Use the template in `/templates/page_snapshot_template.md`.

---

## 🧰 Methods (from least to most automated)

### A) Manual Snapshot (simple & reliable)

- Open the official page
- Use browser **Print → Save as PDF** *or* the **SingleFile** extension to save as a clean HTML.
- Convert to Markdown (optional, see pandoc below).
- Save under `/knowledge` with a clear name, e.g.:
  - `2025-10-21_shop-ceramics_rules.md`
  - `2025-10-21_bylaws_article-iii.pdf`

### B) Semi-automatic with Pandoc (Markdown output)

If you downloaded an HTML snapshot (or copied raw HTML):

```bash
pandoc input.html -f html -t gfm -o 2025-10-21_ceramics_rules.md
```

- Review headings and lists; fix formatting as needed.

### C) Targeted Mirroring (advanced curators)

For a sub-section like `/docs/shops/ceramics`:

```bash
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent https://lowellmakes.com/docs/shops/ceramics/
```

Then convert important pages with pandoc, curate, and add only the canonical ones to `/knowledge`.

> Respect `robots.txt` and copyright. Only ingest content that Lowell Makes owns or is intended for members.

---

## 🧪 Quality Checklist (before PR)

- [ ] File includes URL and **Captured** date
- [ ] Content is **official** (not a personal blog or forum)
- [ ] Clear headings and bullet lists; steps are numbered where helpful
- [ ] Safety-critical statements are **verbatim** or clearly quoted
- [ ] Removed navigation/footers/ads
- [ ] No private or PII content

---

## 🔁 Update Cadence

- **Policies & safety:** update **immediately** when changed
- **Procedures:** review **quarterly**
- **Reference:** review **twice a year**

Include changes in `CHANGELOG.md` and bump CalVer minor.

---

## 🧩 Naming Conventions

`YYYY-MM-DD_area-topic.md`  
Examples:

- `2025-10-21_shop-wood_rules.md`
- `2025-11-01_bylaws_voting-procedures.md`

---

## 🙋 Escalation

If you’re unsure whether a page is canonical or current, tag the relevant **Shop Captain** or **ExCom** in your PR.
