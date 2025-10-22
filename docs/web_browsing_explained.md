
# Understanding Web Browsing in Makers Mate

**Last updated:** October 2025  

Makers Mate is currently configured with **web_browsing disabled**.  
This document explains why, what happens when it’s on, and how it could safely evolve in the future.

---

## 🌐 What “Web Browsing” Means

When a Custom GPT has **web browsing** enabled in the ChatGPT builder:

- The model can perform live searches on the public internet.  
- It can fetch and summarize any public webpage (unless globally blocked by OpenAI).  
- It may expand its search beyond your intended domains if it decides that’s relevant.

That means even if the GPT’s **instructions** say “only use content from lowellmakes.com,” the model can *still* visit other sites like Wikipedia, Reddit, or Medium.  
The instruction is *a guideline, not a technical fence*.

---

## ⚙️ Why Browsing Is Off

For the Lowell Makes community, accuracy and safety matter more than novelty.  
Keeping browsing off ensures that:

- Answers come **only** from the documents you’ve uploaded.  
- The GPT can’t accidentally quote **unofficial** or **unsafe** sources.  
- Internal or member-only information stays **private** within your knowledge set.

You can always re-enable browsing later if the GPT’s role changes (for example, pulling event dates or public blog posts).

---

## 🧱 What the Config File Shows

In `gpt/config.yaml` you’ll see:

```yaml
capabilities:
  web_browsing: false
```

That field simply documents the intent.  
Inside ChatGPT, this flag is **advisory only** — it doesn’t enforce domain limits.  
If you turn browsing on in the GPT Builder, the model gains open internet access.

---

## 🔒 What “Domain Limits” Would Mean Later

When Lowell Makes eventually hosts its own LLM or retrieval system, we can make these rules real:

```yaml
capabilities:
  web_browsing:
    enabled: true
    allowed_domains:
      - "lowellmakes.com"
      - "wiki.lowellmakes.com"
    disallowed_domains:
      - "facebook.com"
      - "reddit.com"
```

A self-hosted environment could enforce those settings with a local **crawler** or **retriever**, keeping results trustworthy.

---

## 🧭 Quick Reference

| Setting | Behavior | Risk | Recommendation |
|----------|-----------|------|----------------|
| `web_browsing: false` | Uses uploaded docs + model memory only | Low | ✅ Default for Makers Mate |
| `web_browsing: true` | Can browse the full public web | Medium – High | Use only for public-info tasks |
| “Only use lowellmakes.com” (instruction) | Textual guideline | May be ignored | Keep as reminder, not protection |

---

## 🔮 Future Path

When Lowell Makes adopts a self-hosted or hybrid model:

1. Enable browsing in a **controlled** way (only official domains).  
2. Add a **retriever layer** for your wiki, classes, and bylaws.  
3. Revisit this document to define policy for what “public” means.

Until then, Makers Mate stays sandboxed — simple, safe, and reliable.
