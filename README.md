# Tabs — Localization Automation Project

A work-in-progress localization pipeline built around **Tabs**, a mock mental clarity app.

🌐 Live site: [tabs.egle.works](https://tabs.egle.works)

---

## Why this exists

Started to explore what current AI automation capabilities actually look like in practice — not just in theory. Less reading about pipelines, more building one.

---

## What I'm figuring out

AI can write code, generate scripts, guide integrations step by step, and help optimize prompts. But it has tunnel vision. It needs the right questions asked and real-world constraints pointed out.

One example: the default setup had strings managed directly in GitHub – which no real localization workflow does. Copywriters work in Google Sheets, not repos. So the pipeline got adjusted: Google Sheets is the copy source, an Apps Script bridge will handle the JSON generation and push to GitHub automatically.

---

## Pipeline (in progress)

```
Google Sheets (copy source)
        ↓
Apps Script → auto-generates en.json → pushes to GitHub
        ↓
Crowdin picks up changes via GitHub integration
        ↓
Translations managed in Crowdin (LT / JA / DE)
        ↓
Translated files pushed back to GitHub
        ↓
Live site reflects updates
```

---

## Current state

| Component | Status |
|---|---|
| i18n JSON string structure (30 strings) | ✅ Done |
| GitHub repository | ✅ Done |
| Crowdin TMS integration (LT, JA, DE) | ✅ Done |
| Landing page: [tabs.egle.works](https://tabs.egle.works) | ✅ Live |
| Google Sheets → GitHub automation bridge | 🔄 In progress |
| Glossary + style guide | 🔄 In progress |
| Asana board (Agile sprint tracking) | 🔄 In progress |
| Expand language pairs | 📋 Planned |
| Invite colleagues to stress-test the workflow | 📋 Planned |

---

## Stack

GitHub · Crowdin · Google Sheets · Apps Script · Asana · Carrd · Claude (AI pair programming throughout)

---

## Notes

This is intentionally a work in progress. The goal isn't a polished finished product – it's to experiment and understand localization infrastructure from the inside, not just manage it from above.
