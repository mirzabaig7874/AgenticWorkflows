# 📧 Inbox Cleaner — AI-Powered Spam Classifier

> Reads the last 50 Gmail messages, uses AI to classify each as junk or legitimate, bulk-moves spam to Trash, and logs every trashed email to a Google Sheet.

---

## 📋 Overview

Inbox Cleaner runs an **AI classification router** across your 50 most recent emails. It distinguishes spam, phishing, and promotions from real mail — then automatically trashes junk while simultaneously building a logged record in Google Sheets for auditing.

---

## 🔄 How It Works

```
┌─────────────────────────────────────┐
│           Gmail Reader              │
│  Reads last 50 inbox emails         │
│  subject · sender · body · date · ID│
└──────────────────┬──────────────────┘
                   │
┌──────────────────▼──────────────────┐
│       AI Junk Classifier            │
│  Scores each email against:         │
│  urgency tactics · suspicious       │
│  senders · grammar · prize scams    │
│  trusted contacts                   │
└──────────┬───────────────┬──────────┘
           │               │
    🗑️ JUNK            ✅ LEGITIMATE
           │               │
┌──────────▼──────┐   ┌───▼──────────┐
│  Bulk Trash     │   │ Left         │
│  Moves to Gmail │   │ Untouched    │
│  Trash in bulk  │   │ Stays in     │
└──────────┬──────┘   │ inbox        │
           │          └──────────────┘
  simultaneously
           │
┌──────────▼──────────────────────────┐
│     Log to Google Sheet             │
│     Subject · Sender · Date         │
└─────────────────────────────────────┘
```

---

## 🔍 Classification Signals

**Junk indicators:**
- Urgency or pressure language ("Act now!", "Limited time!")
- Suspicious sender domains
- Grammar/spelling errors
- Prize or lottery scams
- Unsolicited promotional content
- Phishing patterns

**Legitimate indicators:**
- Trusted sender addresses (e.g. `mirza.asad.baig@gmail.com`, `masad@levi.com`)
- Transactional emails (receipts, shipping confirmations, account alerts)
- Personal or professional correspondence
- Known services and subscriptions

---

## 🛠️ Tech Stack

| Component | Tool |
|---|---|
| Platform | Gumloop |
| Email source | Gmail API (read last 50) |
| AI classification | LLM router node |
| Junk action | Gmail API (bulk move to trash) |
| Audit log | Google Sheets API |
| Execution | Linear → binary branch |

---

## 📁 Files

```
inbox-cleaner/
├── README.md               ← This file
├── portfolio-card.html     ← Embeddable portfolio card
├── portfolio-card.css      ← Card stylesheet
└── prompts/
    └── junk-classifier-prompt.md
```

---

## 🔗 Related Workflows

- **[Junk Mail Report](../junk-mail-report/)** — reads the Google Sheet this workflow writes to, sends an HTML digest report, then clears the sheet.

---

## 📝 Notes

- Processes the **50 most recent inbox emails** per run
- Legitimate emails are **never touched** — the workflow only acts on emails it's confident are junk
- The Google Sheet log serves as a full **audit trail** of everything trashed
- Designed to be run **on-demand** or triggered on a schedule
