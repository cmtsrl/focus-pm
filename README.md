# FOCUS PM · CMT demo workbench

Demo tool for the **FOCUS PM** workshop by CMT S.r.l. (Communication Meets Translation).
It brings together, in a single page, the daily dashboard, the rate calculator, automatic quoting from email and Teams, and a public tender analyser.

> **All data is fictional.** Clients, vendors, emails, Teams chats, tenders and costs are invented.
> The repository contains no keys, passwords, links to real services or client data.

## Start in one command

All you need is Python 3, which comes with macOS and Linux.

```bash
git clone https://github.com/cmtsrl/focus-pm.git && cd focus-pm && python3 -m http.server 8765
```

Then open **http://localhost:8765** in your browser.

- On Windows, use `py -m http.server 8765` instead of `python3 -m http.server 8765`.
- You can also just double-click `index.html`: it works without a server.
- After editing the file, reload with Cmd+Shift+R (Mac) or Ctrl+F5 (Windows).

Nothing to install, nothing to configure.

## What's inside

| View | What it does |
|---|---|
| **Dashboard** | Today's requests read from email and Teams (simulated), sorted by urgency, with a red / amber / green traffic light and notes. Items that ask for a price have a **Prepare quote** button. |
| **Quote window** | Opens on top of the dashboard and closes with the X or Esc. It reads the message by itself, highlights language pairs, volumes, delivery and urgency, and prices the job **by words, hours or minutes**, with margin and a draft reply. |
| **Quotes** | Saved quotes with status (sent, won, lost) and win rate. You can also paste any text. |
| **Rate calculator** | From resource costs to client price: TEP, translation only, MTPE, revision, rush, market cap and maximum acceptable cost. |
| **Tender analyser** | The "wow" feature: reads tender documents from a simulated SharePoint folder, checks the requirements, estimates price and maximum discount, and shows a score, deadlines, risks and the document passages it used. |
| **Vendors** | The (invented) resource costs used by the pricing engine. |
| **Tools** | Where participants add new features with Claude: six ready-made ideas to copy, each with a Preview of the finished tool. |

## Pricing scheme

- Reference cost = highest cost among the vendors for the pair (max translation + max revision).
- Price = cost × 1.35 (1.40 for rare languages, post-editing and revision), rounded up to 0.005.
- Translation only = TEP −20%. Revision only = the higher of revision × 1.4 and €45/h ÷ 1,000 words/h.
- Repetitions charged at 30%. Rush +10% and super rush +25% based on words per day. All pricing values are examples, not a real price list.
- Margin = (price − cost) ÷ price, floor 25.93% (= 35% markup).
- Minutes (subtitling, transcription) and interpreting hours: demo rule (vendor cost × markup), to be tuned. DTP €35/h.

The parameters can be changed in the **Rate calculator** view and apply to the whole tool.

## Adding a feature with Claude

Read [INSTRUCTIONS.md](INSTRUCTIONS.md). In short: give Claude the `index.html` file with the instructions, describe the feature you want, and Claude adds it to the TOOLS section without touching the rest.

### Ready-made solutions

Participants build the six ideas themselves. If someone gets stuck, each idea card in the **Tools** view has a **▶ Preview** button that opens a finished version of that tool, working on the demo data. Close it with the X or Esc.

Each finished tool is also on its own branch, already added to the Tools list as a participant would add it:

| Branch | Tool |
|---|---|
| `tool/capacity-radar` | Vendor capacity radar |
| `tool/spoken-briefing` | Spoken morning briefing |
| `tool/file-word-count` | Word count from a dropped file |
| `tool/delay-risk` | Predictive delay light |
| `tool/price-history` | Price history check |
| `tool/delivery-date` | Delivery date calculator |

```bash
git checkout tool/capacity-radar
```

Then reload the page and open **Tools**. Go back to the starting version with `git checkout main`.

## Structure

```
index.html        the whole app: HTML, CSS and JavaScript, no external libraries
INSTRUCTIONS.md   instructions to give Claude during the workshop
README.md         this file
```

Changes you make (traffic lights, notes, quotes) stay in your browser (localStorage). The **Reset demo data** button puts everything back.

---
CMT S.r.l. | Communication Meets Translation
