# Tabs – Localization Automation Project

A work-in-progress localization pipeline built around **Tabs**, a mock mental clarity app.

🌐 Live site: [tabs.egle.works](https://tabs.egle.works)

---

## Why this exists

Started to explore what current AI automation capabilities actually look like in practice – not just in theory. Less reading about pipelines, more building one.

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
| Google Sheets → GitHub automation bridge | ✅ Done |
| Glossary + style guide | ✅ Done |
| Asana board (Agile sprint tracking) | ✅ Done |
| DE + JA pretranslation via MT | ✅ Done |
| LT translation | 🔄 In progress |
| Translation review and approval | 🔄 In progress |
| Netlify auto-deploy (replace Carrd) | 📋 Planned |
| n8n workflow automation experiments | 📋 Planned |
| Expand language pairs | 📋 Planned |
| Invite colleagues to stress-test the workflow | 📋 Planned |

![Asana board](https://github.com/user-attachments/assets/a0bc575a-2b4d-416f-8417-b0e94ea815d3)

---

Copy is managed in a Google Sheet (the single source of truth for all English strings). A Google Apps Script syncs the sheet to `locales/en/en.json` in this repository via the GitHub API on a daily trigger – no manual file editing required. Crowdin detects the commit and pulls the updated source strings automatically. Translations are produced via MT pre-translation (Crowdin Translate for DE and JA) and manual translation for LT, reviewed and approved in Crowdin, then exported back to GitHub as locale files. 
The landing page at tabs.egle.works is currently updated manually from GitHub – auto-deploy via Netlify is a planned next step.

---

## Stack

GitHub · Crowdin · Google Sheets · Apps Script · Asana · Carrd · Claude (AI pair programming throughout) | Planned: Netlify · n8n

---

## Notes

This is intentionally a work in progress. The goal isn't a polished finished product – it's to experiment and understand localization infrastructure from the inside, not just manage it from above.
