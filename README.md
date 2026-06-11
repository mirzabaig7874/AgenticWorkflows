# 🤖 Agentic Workflows

A collection of AI-powered automation workflows built on [Gumloop](https://gumloop.com) or similar paltform. Each workflow automates a real-world task using a combination of AI agents, web search, Gmail, and Google Sheets.

---

## 📁 Projects

| Project | Description | Key Tech |
|---|---|---|
| [🤖 DadBot](./dadbot/) | Weekly AI digest emailed to my daughter — science, inspiration, jokes & good news | Parallel agents, web search, HTML email |
| [📧 Inbox Cleaner](./inbox-cleaner/) | Reads 50 Gmail messages, AI-classifies junk vs. legitimate, bulk-trashes spam & logs it | Gmail, AI router, Google Sheets |
| [🗑️ Junk Mail Report](./junk-mail-report/) | Scheduled digest that reads the junk log, emails an HTML report, then clears the sheet | Google Sheets, AI formatter, Gmail |

---

## 🔗 How Inbox Cleaner & Junk Mail Report Work Together

```
Inbox Cleaner (on-demand)
  └── Classifies emails → logs junk to Google Sheet
        ↓
Junk Mail Report (every 5 hours)
  └── Reads sheet → sends HTML report email → clears sheet
```

These two workflows form a connected system — one writes, the other reads, reports, and resets.

---

## 🛠️ Tech Stack

- **Platform:** [Gumloop](https://gumloop.com)
- **AI:** Large language models via Gumloop's AI nodes
- **Integrations:** Gmail API · Google Sheets API · Web Search
- **Triggers:** Scheduled (weekly / every 5 hours) · Manual

---

## 👤 Author

**Mirza Baig**
Built as personal productivity and family projects using Gumloop's agentic workflow platform.
