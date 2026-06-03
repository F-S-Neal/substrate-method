# The Substrate Method

**An Obsidian vault + workflow for fiction writers and worldbuilders.**

Catch your story ideas the messy, jump-around way they actually arrive — as small tagged notes called *sparks* — then cull a topic down to the sparks you decide to keep and have an AI write them into a single report. Use the report as a reference page to your Canon for when you write. No code. No filing. You stop building hierarchical folders and static lists, instead asking for views of your ideas (character views, setting views).

It's built for the way fiction notes really behave: ideas hit any time of day or night, and any given idea ("Gary's magic comes from stones of power") is about Gary *and* your magic system *and* maybe a series-wide theme, all at once. A filing cabinet forces that note into one drawer. Substrate lets it carry every label it deserves and reassembles the views on demand.

If you write novels, run a long series, build a TTRPG setting, or keep a sprawling story bible and you're concerned about continuity, this is for you.

---

## How it works, in one breath

1. **Capture** — sparks, auto-tagged, individually or in bulk.
2. **Review & make choices** — pull up a topic in the Spark Assembler, which groups its sparks into subtopics called aspects and puts contradictions side by side for convenience. You keep or reject each one — **this is where you decide what's true for your story or world, and it's the step you never automate.**
3. **Synthesize** — use the AI to report your approved sparks into a canonical page for part of your story (a character, a setting, etc.). 
4. **Write** — from your canonical pages and scene sheets.

If you find an error or change your mind, just fix the spark and re-synthesize.

## What's in the box

- **Sparks** — atomic, tagged idea-notes. The raw pile.
- **Tag Spark** — a one-click prompt that adds a spark's entity tags, aspect (facet) tags, and a one-line summary.
- **Spark Assembler** — review a topic's sparks grouped by aspect (appearance, relationships…), and cull before you synthesize.
- **Synthesis** — an AI prompt that reports a topic's approved sparks into its reference page (aspect-organized for characters), and re-reports incrementally as sparks change.
- **Canonical pages** — the report of the sparks you kept; what you write from. You don't hand-edit them — fix a spark and regenerate. Flat, named `Type_Name`.
- **Canonical Index** — every page by type, plus a "to synthesize" queue so you never forget the cast.
- **Book Bible** — a whole project's world (cast by priority, everything else by type), with a full-text **export** version.
- **Spark Catalog** — the full text of every raw spark on a topic, for brainstorming.
- **Scene cheat sheets** — a one-pager for exactly the scene you're about to write.
- **A Rejected pile** — ideas you killed but kept, out of synthesis yet never lost.

Setup is **INSTALL.md** (about five minutes).
For the full walkthrough check out **MANUAL.md** 

---

## Requirements — read this before you download

This is an opinionated workflow that leans on an AI plugin. Be clear-eyed about that going in:

- **[Obsidian](https://obsidian.md)** (free).
- **Copilot for Obsidian** by *Logan Yang* — the AI. Several community plugins are named "Copilot"; you want this author's. It needs **either** an API key from a provider (Anthropic, OpenAI, Google — pay-as-you-go, usually pennies per use) **or** a free local model via Ollama / LM Studio (slower and weaker, but free and private).
- **Dataview** — powers the live views (Book Bible, Canonical Index, Spark Assembler, Spark Catalog). You must turn on its **JavaScript Queries** toggle (INSTALL §2b).
- **Templater**, **Smart Connections**, **Auto Note Mover** — templates, related-note surfacing, and auto-filing of rejected sparks.

> **Tested on:** Obsidian `1.12.7`, Copilot `3.3.3`, Dataview `0.5.68`. If your plugin versions differ and the gather misbehaves, please say so in an issue — see the honest caveat below.

## The one thing that makes (or breaks) it

The whole system rests on a single mechanism: Copilot's `{#tag}` custom-prompt placeholder injects the **full text of every note** whose Properties `tags:` field contains that tag. It is a literal, exhaustive expansion — *not* RAG-style sampling — which is what makes "gather everything about my character Gary" trustworthy instead of approximate.

Two habits you cannot skip:

1. **Tags must live in a note's Properties (`tags:`), not typed loose in the body.** A `#gary` in your prose won't be gathered. The templates handle this for you.
2. **Functionality depends on the Copilot plugin.** If a future version changes how `{#tag}` works, the gather changes with it. 

The vault ships a **smoke test** (three demo sparks) precisely so you can verify the exhaustive gather on *your* setup in two minutes before trusting it with your real notes. I'd run it first before doing the work of porting in your ideas (INSTALL §4.).

---

## Quick start

1. Download/clone this repo and **Open folder as vault** in Obsidian.
2. Follow **INSTALL.md** (install plugins, add an API key or local model, copy the prompts).
3. Run the **smoke test** (INSTALL §4) — confirm the demo gather pulls both Gary sparks and excludes the rejected one.
4. Delete the demo files and start capturing your own sparks. Day-to-day use is **MANUAL.md §8**.

## Troubleshooting

- **"It only found some of my notes."** The missing notes have their tag in the body, not in Properties. Move it to the `tags:` field. Then quit and reopen Obsidian so Copilot re-indexes, and re-run in a *new* chat.
- **"Dataview JS queries are disabled."** Turn on Settings → Dataview → **Enable JavaScript Queries** (INSTALL §2b). The Spark Assembler, Spark Catalog, Canonical Index, and Book Bible need it.
- **"My prompts don't show up in Copilot."** They must sit in Copilot's own custom-prompts folder (default `copilot-custom-prompts/` at the vault root), then toggle the plugin off/on. Don't re-point Copilot's setting at the `_Prompts/` folder. (INSTALL §3.)
- **"Rejected notes aren't moving" — or a note vanished into `Rejected/`.** Auto Note Mover fires when you tag a note, not on restart — add the rule (INSTALL §0) and edit the note once. And the reverse trap: never write a literal `#tag` in a note's *prose* — a stray `#rejected` in your text reads as a live tag and gets the whole note auto-filed away. Wrap tags in `backticks` or drop the `#`.

---

## License & credit

Released under the MIT License (see `LICENSE`) — use it, fork it, adapt it for your own stories. Created and maintained by **F. S. Neal**. If you build something with it, I'd love to hear about it.

*Substrate is a workflow assembled from off-the-shelf Obsidian plugins plus an AI. It is not a plugin and there is nothing to compile — just notes, tags, and prompts.*
