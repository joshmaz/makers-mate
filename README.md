
# Makers Mate

**Makers Mate** is a community-maintained knowledge base and instruction set for a custom GPT used by the Lowell Makes community.  
This repository tracks the GPT's **instructions**, **uploaded reference docs**, and **collaboration workflow** so anyone can improve it together.

> Scope: keep it simple. We are *only* tracking GPT instructions and knowledge files here.  
> Future-friendly: if we later self-host an LLM or add tools, this repo already has space for that evolution.

---

## Quick Start

1. Read [`/gpt/instructions.md`](gpt/instructions.md).
2. Update the GPT in ChatGPT Builder with the latest **Instructions** and upload any **knowledge files** from `/knowledge`.
3. Open a PR for any edits so the community can review them.

### Suggested Workflow
- All instruction changes happen via PRs.
- Tag releases when instructions change in meaningful ways (see **Versioning** below).

---

## Directory Layout

```
/gpt/               # Everything the GPT builder needs
  instructions.md   # The canonical instruction text (paste into the GPT)
  config.yaml       # Metadata (name/desc/voice/domains/capabilities) for reference
/docs/
  CONTRIBUTING.md   # How to propose changes
  CODE_OF_CONDUCT.md
  GOVERNANCE.md
  ROADMAP.md
  STYLEGUIDE.md
/knowledge/         # Reference documents you upload to the GPT (“Knowledge” section)
  README.md
  .gitkeep
/.github/
  ISSUE_TEMPLATE/bug_report.md
  ISSUE_TEMPLATE/feature_request.md
  PULL_REQUEST_TEMPLATE.md
CHANGELOG.md
LICENSE
SECURITY.md
```

---

## Versioning

Use **CalVer + semver-ish** tags: `YYYY.MM.MINOR` (e.g., `2025.10.0`).  
- Bump **MINOR** for instruction changes that affect GPT behavior.
- Use the **CHANGELOG** to summarize notable updates.

---

## Future Expansion (Optional)

If we later run our own LLM or add tools (retrieval, actions, webhooks), we can add folders like:

- `/tools/` — tool specs & config
- `/scripts/` — utility scripts for migrations or validation
- `/infra/` — IaC or deployment notes

These are intentionally *not* included now to keep the scope small.

---

## License

[MIT](LICENSE)
