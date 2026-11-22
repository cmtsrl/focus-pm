# FOCUS PM · CMT demo workbench

Demo tool for the **FOCUS PM** workshop by CMT S.r.l. (Communication Meets Translation).
It brings together, in a single page, the daily dashboard, the rate calculator, automatic quoting from email and Teams, and a public tender analyser.

> **All data is fictional.** Clients, vendors, emails, Teams chats, tenders and costs are invented.
> The repository contains no keys, passwords, links to real services or client data.

## Open it (Windows and Mac)

Nothing to install: no Python, no Git. You only need an up-to-date browser (Chrome, Edge, Firefox or Safari).

1. On this page click the green **Code** button, then **Download ZIP**.
2. Extract the ZIP:
   - **Windows:** right-click the file → **Extract All** → **Extract**.
   - **Mac:** double-click the ZIP.
3. In the extracted folder, double-click **index.html**. It opens in your browser.

Good to know:

- **Windows: extract first.** If you open `index.html` from inside the ZIP, Windows runs it from a temporary folder and your changes may not be kept.
- **Windows: wrong program?** Right-click `index.html` → **Open with** → Chrome or Edge.
- **Windows: file blocked?** Right-click the ZIP → **Properties** → tick **Unblock** → OK, then extract.
- After editing the file, reload with **Ctrl+F5** (Windows) or **Cmd+Shift+R** (Mac).

<details>
<summary>Optional: run it as a local website</summary>

Not needed for the workshop. If you have Python 3 installed (on Windows from python.org; on recent Macs `python3` asks to install the developer tools the first time), run this in the project folder and open http://localhost:8765:

```bash
python3 -m http.server 8765
```

On Windows the command is `py -m http.server 8765`.
</details>

## What's inside

| View | What it does |
|---|---|
| **Dashboard** | Today's requests read from email and Teams (simulated), sorted by urgency, with a red / amber / green traffic light and notes. Items that ask for a price have a **Prepare quote** button. |
| **Quote window** | Opens on top of the dashboard and closes with the X or Esc. It reads the message by itself, in English or Italian, highlights language pairs, volumes, delivery and urgency, and prices the job **by words, hours or minutes**, with margin and a draft reply. |
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

The rules Claude must follow are in [INSTRUCTIONS.md](INSTRUCTIONS.md): new features go in the TOOLS section, everything else stays as it is. The same first message works in Claude Code and in the chat: Claude reads where it is working and delivers the changes the right way.

### Recommended: Claude desktop app, Code tab (Windows and Mac)

Needs a paid Claude plan (Pro, Max, Team or Enterprise). No Git, no GitHub account.

1. Install the Claude desktop app from claude.ai/download and sign in.
2. Download and extract this project as described in **Open it** above.
3. In the app open the **Code** tab, choose **Local**, then **Open folder…** and select the extracted folder.
4. First message: *"Read INSTRUCTIONS.md and follow it. Then add this feature: …"*
5. When Claude asks to edit the file, approve. Then reload `index.html` in your browser (Ctrl+F5 / Cmd+Shift+R) and open **Tools**.

Tip: keep a copy of the extracted folder before big changes, so you can start again.

### Alternative: Claude chat (any plan, including Free)

1. In a new chat on claude.ai, attach `index.html` and `INSTRUCTIONS.md`.
2. Write: *"Read INSTRUCTIONS.md and follow it. Then add this feature: …"*
3. Claude shows the updated page as an artifact. At the end, download it and replace your `index.html`.

The file is large for a chat: ask for one small feature at a time.

### Ready-made solutions

Participants build the six ideas themselves. If someone gets stuck, each idea card in the **Tools** view has a **▶ Preview** button that opens a finished version of that tool, working on the demo data. Close it with the X or Esc.

For presenters: each finished tool is also on its own branch, already added to the Tools list as a participant would add it:

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
