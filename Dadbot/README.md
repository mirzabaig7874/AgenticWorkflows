# 🤖 DadBot — Weekly Digest for My Daughter

> An automated weekly AI digest that curates and emails personalized content to a 13-year-old girl — science, inspiration, dad jokes, and good news — all in one beautiful HTML email.

---

## 📋 Overview

DadBot runs **5 AI agents in parallel** once a week. Four specialized content curator bots scour the web simultaneously, then a final aggregator bot picks the best item from each and formats everything into a clean HTML email delivered straight to the inbox.

---

## 🔄 How It Works

```
         ┌─────────────────────────────────────────┐
         │           Weekly Schedule Trigger        │
         └──────────────────┬──────────────────────┘
                            │
         ┌──────────────────▼──────────────────────┐
         │      Runs 4 bots simultaneously          │
         └──────────────────────────────────────────┘
         │            │            │            │
    ┌────▼───┐  ┌─────▼──┐  ┌────▼───┐  ┌────▼──────┐
    │Science │  │Inspire │  │ Joke   │  │ GoodNews  │
    │  Bot   │  │  Bot   │  │  Bot   │  │   Bot     │
    └────┬───┘  └─────┬──┘  └────┬───┘  └────┬──────┘
         └────────────┴──────────┴────────────┘
                            │
         ┌──────────────────▼──────────────────────┐
         │              AggregatorBot               │
         │  Picks 1 best per bot · Builds HTML email│
         └──────────────────┬──────────────────────┘
                            │
         ┌──────────────────▼──────────────────────┐
         │    📧 "DadBot Weekly Digest" → Inbox     │
         └─────────────────────────────────────────┘
```

---

## 🤖 The 4 Content Curator Bots

| Bot | Role |
|---|---|
| **ScienceBot** | Searches for 3 recent science topics engaging for an 8th grader (videos, articles, comics) |
| **InspireBot** | Finds 3 recent inspirational life lessons or quotes to build character, curiosity & resilience |
| **JokeBot** | Searches for 3 age-appropriate dad jokes, prioritizing comics and pictures |
| **GoodNewsBot** | Curates 3 uplifting news stories from the past week — kindness, breakthroughs, animal rescues |

All 4 bots run **independently and simultaneously**, each searching the web for fresh, age-appropriate content.

---

## 🧩 AggregatorBot (Final Step)

- Receives all 4 bot outputs
- Picks exactly **1 best item** from each (prioritising video/audio/image over text)
- Formats into a **beautiful HTML email** — aesthetically pleasing for an 8th grader
- Sends with subject line: **"DadBot Weekly Digest"**

---

## 🛠️ Tech Stack

| Component | Tool |
|---|---|
| Platform | Gumloop |
| Trigger | Weekly schedule |
| Web search | Gumloop web search nodes |
| AI agents | LLM nodes (×5) |
| Email delivery | Gmail API |
| Execution | 4 parallel branches → merge |

---

## 📁 Files

```
dadbot/
├── README.md               ← This file
├── portfolio-card.html     ← Embeddable portfolio card
├── portfolio-card.css      ← Card stylesheet
└── prompts/
    ├── sciencebot-prompt.md
    ├── inspirebot-prompt.md
    ├── jokebot-prompt.md
    ├── goodnewsbot-prompt.md
    └── aggregatorbot-prompt.md
```

---

## 📝 Notes

- Runs **once per week** on a scheduled trigger
- Prioritises rich media (video, images, comics) over plain text links
- Content is curated for a **13-year-old girl (8th grade)** — age-appropriate and engaging
