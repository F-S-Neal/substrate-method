# Substrate Starter — install (5 minutes)

This whole `SubstrateVault` folder is a ready-to-use Obsidian vault — every folder and file is already in place, including the prompts. You install a few plugins, point two of them at the right folders, add your Copilot API key, and move a couple of folders.

## 0. Install these Community plugins (Settings → Community plugins → Browse)
- **Copilot** by Logan Yang — the AI; needs an API key. (Several plugins are named "Copilot" — pick this author's.)
- **Dataview** — powers the live views (the Book Bible, Canonical Index, Spark Assembler). After install you MUST turn on its JavaScript Queries — see step 2b.
- **Templater** — makes the templates work.
- **Smart Connections** — surfaces related sparks; just let it index once.
- **Auto Note Mover** — auto-files rejected sparks. **You MUST add the rule or nothing moves:** Settings → Auto Note Mover → **Add new rule** → Folder `Rejected`, Tag `#rejected`, Trigger **Automatic**. (It moves a note when you tag it — not on restart — so to move one already tagged, edit it once or run command palette → "Auto Note Mover: Move the note".)
- **Advanced Merger** — optional, for merging a folder of pages into one file.
- **Note Composer** (core) — turn on in Settings → Core plugins.

## 1. Open the vault
In Obsidian: **Open folder as vault** → point at this `SubstrateVault` folder. (Or copy its folders into an existing vault's root.) It's already laid out:

- `Sparks/` — your idea pile (flat).
- `Canonical/` — settled pages, **flat, named `Type_Name`** (e.g. `Character_Gary`); plus `_Book Bible`, `_Book Bible Export`, and `_Canonical Index`.
- `Themes/`, `Rejected/`, `SceneReports/`, `Exploratory Prose/`.
- `Spark Assembler.md` — the review note, at the root (Chrono ⇄ Topic toggle: chronological full-text or aspect-grouped summaries).
- `_Templates/`, `_Prompts/`, `_External AI Prompts/`, `_tags.md`, plus `MANUAL.md`, `README.md`, `CHANGELOG.md`, and `LICENSE`. (Most folders also hold a small `_README.md`.)

**Add your own sub-folders anytime** — Substrate finds notes by tag and by the `type:` / `book:` properties, not by folder.

## 2a. Point Templater at the templates
Settings → Templater → **Template folder location** → `_Templates`. The Substrate templates *prompt* you for what they need, so make new pages with the command **"Templater: Create new note from template"** (not the core Templates plugin). Optional: turn on **Settings → Templater → Trigger Templater on new file creation** if you want it to run automatically.

## 2b. Turn on Dataview's JavaScript Queries (don't skip)
Settings → Community plugins → **Dataview** (gear/options) → toggle ON **"Enable JavaScript Queries."** (Leave "Enable Inline JavaScript Queries" alone — you don't need it.) Without this, the **Spark Assembler**, **Canonical Index**, and **Book Bible** show a "Dataview JS queries are disabled" error.

## 3. Set up Copilot
**a) Add your API key.** Settings → Copilot → your provider (Anthropic/Claude, OpenAI, Google…) → paste an API key from that provider's site. Pay-as-you-go, usually pennies. Pick a model (Claude Sonnet is a good default).
*(Zero-cost alternative: point Copilot at a local model — type "local" in the key field; generally weaker and slower, but free and private.)*

**b) Copy the prompts into Copilot's folder.** Installing Copilot creates its own prompt folder — by default `copilot-custom-prompts/` at your vault root. **Copy** the five files from `_Prompts/` — `Synthesis Prompt.md`, `Tag Spark.md`, `Scene Report Prompt.md`, `Smoke Test Prompt.md`, `Theme Discovery Prompt.md` — into that `copilot-custom-prompts/` folder. (If Settings → Copilot lists a different custom-prompts folder, copy them there instead. Do NOT re-point that setting at our `_Prompts/` folder — re-pointing hides Copilot's built-ins.)

**c) Reload Copilot so it sees them.** Settings → Community plugins → toggle **Copilot** off and on (or restart Obsidian). Now typing `/` in the chat shows **Synthesis Prompt**, **Tag Spark**, **Scene Report Prompt**, **Smoke Test Prompt**, and **Theme Discovery Prompt** alongside Copilot's built-ins. You can delete the now-empty `_Prompts/` afterward.

## 4. Smoke test — do this BEFORE importing your real notes
The vault ships three demo sparks for exactly this (all tagged `gary`, one also `rejected`).
1. Create a blank scratch note anywhere and keep it open (so Copilot's "current note" context can't interfere). Then open a **new** Copilot chat.
2. Type `/` → pick **Smoke Test Prompt** → send. It's already filled in (topic Gary, tag `{#gary}`) — nothing to edit.
3. The report should include the **red boot** AND the **fear of water**, and leave out the **lost king** (it's rejected).
   - All three correct → the gather works. You're good.
   - A note missing → see manual §9.5: quit/reopen Obsidian, let Copilot finish indexing, re-run the smoke test in a new chat, and cross-check with the **Spark Assembler** (`topic: gary`).
4. When it passes, delete the demo content: the three `DEMO - gary…` sparks **and** the demo cast (search the vault for `zzdemo` to grab every demo `Character_`/`Magic_`/`Setting_` page at once), then blank the `_Book Bible`'s `series`.

## 5. The one habit that makes it all work.
Put tags in a note's **Properties** (the `tags:` field), not loose `#tags` in the body — the gather only sees Properties tags. The templates already do this for you.

That's it. Day-to-day use is §8 of the Manual.
