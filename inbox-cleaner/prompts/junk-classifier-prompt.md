# Junk Classifier — Prompt

**Node type:** AI / LLM Router  
**Workflow:** Inbox Cleaner  
**Role:** Classifies each email as Junk or Legitimate and routes it to the appropriate branch

---

## ⚠️ Action Required

Paste the exact prompt from your Gumloop Junk Classifier node below.

**How to find it:**
1. Open the **Inbox Cleaner** workflow in Gumloop
2. Click the **AI Classifier / Router** node
3. Copy the full prompt text
4. Paste it in the section below and delete this instruction block

---

## Prompt

```
Route: Junk
email contains any of the following signals:
- Unsolicited promotional offers, deals, or advertisements
- Phishing attempts (fake login pages, credential requests)
- Lottery/prize winnings the recipient never entered
- Urgency tactics ("Act NOW!", "Limited time!", "Your account will be suspended!")
- Requests for personal, financial, or login information
- Suspicious sender addresses mismatching the claimed brand
- Excessive use of capital letters, emojis, or exclamation marks
- Grammar/spelling errors typical of scam emails
- Unknown senders with vague or irrelevant content
- Links to suspicious or unrelated domains

Route: Legitimate
- Comes from a known sender or organization with consistent branding
- Contains expected transactional content (receipts, confirmations, shipping)
- Is a direct personal or professional communication
- Is a subscribed newsletter with a clear sender identity and unsubscribe option
- Contains no deceptive urgency, suspicious links, or credential requests
- the sender is from following whitelist:
mirza.asad.baig@gmail.com
masad@levi.com
```

---

## Classification Logic

**Routes to 🗑️ Junk when:**
- Urgency or pressure language detected ("Act now!", "You've won!", "Limited time!")
- Suspicious or unknown sender domain
- Grammar/spelling errors consistent with spam
- Prize, lottery, or inheritance scams
- Unsolicited promotional bulk mail
- Phishing patterns or spoofed addresses

**Routes to ✅ Legitimate when:**
- Trusted sender addresses (e.g. `mirza.asad.baig@gmail.com`, `masad@levi.com`)
- Transactional emails (order confirmations, shipping, receipts, account alerts)
- Personal or professional correspondence
- Recognised service providers and subscriptions

---

## Input

Each email is passed with: `subject`, `sender`, `body`, `date`, `message_id`

## Output

Two routes: `junk` → Bulk Trash + Log · `legitimate` → No action
