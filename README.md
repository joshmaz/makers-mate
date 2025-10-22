
# Makers Mate

**Makers Mate** is the Lowell Makes community’s custom GPT, designed to help members and volunteers quickly find information, follow processes, and learn how to use shops and tools safely.

🧠 **Use it here:** [Makers Mate on ChatGPT](https://chatgpt.com/g/g-68f84628b8688191b2569ee7afaea16c-maker-s-mate)

---

## 🎯 Purpose

This repository tracks everything that defines and feeds the Makers Mate GPT:

- The **instructions** used in the ChatGPT Builder  
- All **knowledge documents** uploaded to the GPT  
- The **catalog** that indexes where every official document lives  
- Contribution guides, governance info, and templates for consistent updates  

> **Scope:** Keep it simple and transparent.  
> **Future-friendly:** The structure can easily evolve to support a self-hosted or retrieval-based LLM later.

---

## 🧩 Repository Layout

```
/gpt/               # GPT identity and configuration
  instructions.md   # Canonical system prompt for the GPT Builder
  config.yaml       # Metadata and advisory capability flags
/catalog/           # Index of all documents and their locations
  doc_index.csv     # Canonical list of docs (title, owner, URL, freshness, etc.)
  doc_index_schema.json
/docs/              # Guides and reference documentation
  CONTRIBUTING.md
  CODE_OF_CONDUCT.md
  GOVERNANCE.md
  STYLEGUIDE.md
  ROADMAP.md
  web_browsing_explained.md
  ingestion_playbook.md
  catalog_playbook.md
/knowledge/         # Mirrored or manually curated member-facing documents
/templates/         # Reusable content templates
/.github/           # Issue and pull-request templates
CHANGELOG.md
LICENSE
SECURITY.md
```

---

## 🚀 Getting Started

1. **Read the GPT instructions**  
   - [`/gpt/instructions.md`](gpt/instructions.md) defines how Makers Mate behaves.  
   - Paste the full contents into the Custom GPT’s *Instructions* field.

2. **Upload knowledge files**  
   - Place Markdown or PDF snapshots of official docs into `/knowledge`.  
   - Follow the [Ingestion Playbook](docs/ingestion_playbook.md) for clean formatting.

3. **Update the document catalog**  
   - Add or update rows in `/catalog/doc_index.csv` using the schema provided.  
   - Reference the [Catalog Playbook](docs/catalog_playbook.md) for workflow details.

4. **Open a Pull Request**  
   - Use the templates under `.github/` to propose new docs or edits.  
   - Tag the relevant Shop Captain or ExCom for policy-affecting content.

---

## 🧱 Capabilities (and Limits)

| Capability | Status | Notes |
|-------------|---------|-------|
| Web Browsing | ❌ Off | Makers Mate only answers from uploaded and catalogued docs. |
| Code Interpreter | ❌ Off | Not needed for normal member guidance. |
| Image Generation | ❌ Off | Can be enabled later for media-related workflows. |

See [web_browsing_explained.md](docs/web_browsing_explained.md) for a full explanation.

---

## 🕸️ Document Ingestion & Indexing

Makers Mate does not browse the web; instead, content from official sources (like `lowellmakes.com` or `wiki.lowellmakes.com`) is **snapshotted** into `/knowledge` and recorded in the catalog.

Read these for how to do it:

- 📘 [Website-to-Knowledge Ingestion Playbook](docs/ingestion_playbook.md)  
- 📗 [Document Catalog Playbook](docs/catalog_playbook.md)

---

## 🔄 Versioning

- **CalVer + Minor:** `YYYY.MM.MINOR` (e.g., `2025.10.2`)  
- **Minor bump** = any instruction or content update that changes GPT behavior or adds major documents.

See [CHANGELOG.md](CHANGELOG.md) for release notes.

---

## 🧩 Future Expansion

This repo anticipates growth into a self-hosted or retrieval-augmented environment.  
Potential future folders:

- `/tools/` — plugin or connector definitions  
- `/scripts/` — validation or ingestion helpers  
- `/infra/` — deployment notes or LLM hosting configs

---

## 🧑‍🤝‍🧑 Governance & Community

- Policy authority: **Lowell Makes Executive Committee (ExCom)**  
- Shop content authority: **Relevant Shop Captain(s)**  
- Maintainers: Volunteer documentation team

See [GOVERNANCE.md](docs/GOVERNANCE.md) and [CONTRIBUTING.md](docs/CONTRIBUTING.md) for details.

---

## ⚖️ License

[MIT License](LICENSE) © Lowell Makes
