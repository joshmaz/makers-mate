
# Document Catalog Playbook

**Purpose:** Provide a single, searchable index of official documents — what they are, who owns them, where they live, and how fresh they are.

## Where the index lives

- **File:** `/catalog/doc_index.csv`
- **Schema:** `/catalog/doc_index_schema.json`
- **Docs:** This playbook and the ingestion playbook (`/docs/ingestion_playbook.md`)

## What goes in the index

Every member-facing document that Makers Mate should rely on:

- Policies, Bylaws, Safety rules
- SOPs and Onboarding
- Stable references and public FAQs

## Key fields (high level)

- **id** — Stable ID for references (e.g., `DOC-0101`)
- **title** — Human-friendly name
- **category** — Bylaws / Safety / SOP / Reference / Onboarding / Form / FAQ / Other
- **shop** — If shop-specific (e.g., Ceramics), else blank
- **status** — Canonical / Draft / Superseded / Archived
- **owner_role** — Who is accountable (role), e.g., Shop Captain or ExCom
- **canonical_url** — The source-of-truth link
- **mirror_path** — Path in `/knowledge` if mirrored
- **last_updated** — Date we verified content freshness
- **review_cycle** — “Quarterly”, “Annually”, etc.
- **access_level** — Public / Members / Internal

See `/catalog/doc_index_schema.json` for full definitions.

## Workflow

1. **Add/Update a Document**
   - Create a page snapshot in `/knowledge` (see Ingestion Playbook)
   - Add/Update a row in `/catalog/doc_index.csv`
   - Open a Pull Request describing the change
2. **Review**
   - At least one maintainer reviews formatting and metadata
   - For policy content, tag the relevant Shop Captain or ExCom
3. **Merge**
   - Update `CHANGELOG.md` with a summary
   - If content changed materially, bump CalVer minor (e.g., 2025.10.1)

## Freshness Cadence

- **Policies & Safety**: update immediately when changed
- **Procedures**: quarterly
- **Reference**: twice a year

## Tips

- Keep **canonical_url** accurate even if you mirror content — the website remains source of truth.
- Use **notes** to flag pending transitions (e.g., “new policy in draft: DOC-0102”).
- Avoid adding member-only/private docs to this public repo; track them as metadata only with `access_level: Members` or `Internal` and leave `mirror_path` blank.
