# HTML Formatter — Prompt

**Node type:** AI / LLM (Ask AI)  
**Workflow:** Junk Mail Report  
**Role:** Converts a plain-text block of structured email rows into a clean, formatted HTML table

---

## ⚠️ Action Required

Paste the exact prompt from your Gumloop AI formatter node below.

**How to find it:**
1. Open the **Junk Mail Report** workflow in Gumloop
2. Click the **Format Junk Email List (Ask AI)** node
3. Copy the full prompt text
4. Paste it in the section below and delete this instruction block

---

## Prompt

```
You are an email formatter. Below is a log of emails that were automatically moved to the junk/trash folder. Format this data as a clean HTML table with three columns: Sender, Subject, and Date. Each email should be a row in the table. Do not analyze or summarize — just present the data as-is in a readable HTML table format.
```

---

## Notes

**Input:** A joined text block of rows, each formatted as:
```
📧 Subject: ... | 👤 Sender: ... | 📅 Date: ...
```

**Output:** A clean HTML table with three columns:
- Sender
- Subject  
- Date

**Target:** The table is embedded directly into a Gmail HTML email with subject **"🗑️ Junk Mail Report — Last 5 Hours"**
