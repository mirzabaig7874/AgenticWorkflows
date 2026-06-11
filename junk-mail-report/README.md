# 🗑️ Junk Mail Report — Scheduled Digest & Sheet Reset

> Every 5 hours, checks the junk email log in Google Sheets. If entries exist, formats them into a clean AI-generated HTML table, emails the report, then wipes the sheet clean for the next cycle.

---

## 📋 Overview

Junk Mail Report is the **reporting companion** to [Inbox Cleaner](../inbox-cleaner/). While Inbox Cleaner writes junk emails to a Google Sheet, this workflow reads that sheet on a schedule, generates a formatted HTML digest, emails it to you, and resets the sheet — creating a complete 5-hour loop.

---

## 🔄 How It Works

```
┌──────────────────────────────────────────────┐
│          Scheduled Trigger (every 5 hrs)     │
└─────────────────────┬────────────────────────┘
                      │
          ┌───────────▼──────────┐   ┌─────────────────┐
          │   Count Sheet Rows   │   │  Sheet URL       │
          │   How many entries?  │   │  Constant value  │
          └───────────┬──────────┘   └────────┬────────┘
                      └──────────┬────────────┘
                                 │
          ┌──────────────────────▼──────────────────────┐
          │         Router: Is Sheet Empty?             │
          └──────────────┬────────────────┬─────────────┘
                         │                │
                    Rows = 0         Rows > 0
                         │                │
                    ┌────▼────┐    ┌──────▼──────────────────┐
                    │  Stop   │    │    Read Sheet Data       │
                    │  Exit   │    │  Subject · Sender · Date │
                    └─────────┘    └──────┬───────────────────┘
                                          │
                                   ┌──────▼──────────────────┐
                                   │  Structure Each Row     │
                                   │  📧 Subject · 👤 Sender │
                                   │  📅 Date (per row)      │
                                   └──────┬───────────────────┘
                                          │
                                   ┌──────▼──────────────────┐
                                   │  Join All Rows          │
                                   │  Single text block      │
                                   └──────┬───────────────────┘
                                          │
                                   ┌──────▼──────────────────┐
                                   │  AI → HTML Table        │
                                   │  Clean formatted table  │
                                   └──────┬───────────────────┘
                                          │
                                   ┌──────▼──────────────────┐
                                   │  Send Email Report      │
                                   │  "🗑️ Junk Mail Report   │
                                   │   — Last 5 Hours"       │
                                   └──────┬───────────────────┘
                                          │
                                   ┌──────▼──────────────────┐
                                   │  Clear Sheet Rows       │
                                   │  Ready for next batch   │
                                   └─────────────────────────┘
```

---

## 📊 Step-by-Step

| Step | Action | Detail |
|---|---|---|
| 1 | Count rows | Reads row count from junk log sheet |
| 2 | Sheet URL | Stores the Google Sheet URL as a constant |
| 3 | Router | If 0 rows → stop. If rows exist → continue |
| 4 | Read sheet | Pulls Subject, Sender, Date columns |
| 5 | Structure rows | Formats each row into a readable string |
| 6 | Join rows | Combines all rows into one text block |
| 7 | AI format | Converts text to a clean HTML table |
| 8 | Send email | Delivers report to mirza.asad.baig@gmail.com |
| 9 | Clear sheet | Wipes rows — resets for next cycle |

---

## 🛠️ Tech Stack

| Component | Tool |
|---|---|
| Platform | Gumloop |
| Trigger | Scheduled (every 5 hours) |
| Data source | Google Sheets API (read + clear) |
| AI formatting | LLM node (text → HTML table) |
| Email delivery | Gmail API |
| Logic | Conditional router (empty check) |

---

## 📁 Files

```
junk-mail-report/
├── README.md               ← This file
├── portfolio-card.html     ← Embeddable portfolio card
├── portfolio-card.css      ← Card stylesheet
└── prompts/
    └── html-formatter-prompt.md
```

---

## 🔗 Related Workflows

- **[Inbox Cleaner](../inbox-cleaner/)** — classifies and trashes junk emails, writes to the Google Sheet this workflow reads from.

---

## 📝 Notes

- If the Google Sheet is empty when this runs, the flow exits silently — no email sent
- The **5-hour subject line** ("Last 5 Hours") matches the schedule interval, so reports are always scoped correctly
- After sending, the sheet is **fully cleared** — no duplicate reporting across runs
- Works best when paired with Inbox Cleaner running on-demand or on a frequent schedule
