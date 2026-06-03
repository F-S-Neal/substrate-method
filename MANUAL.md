---
title: The Substrate Method — A Worldbuilding Vault for Novelists
version: 1.3
status: setup guide
---

# The Substrate Method
### A worldbuilding & note-synthesis vault for fiction writers

> A way to catch your scattered story ideas the messy, jump-around way they actually arrive, and turn them — whenever you're ready — into clean reference pages you can write from. It runs inside Obsidian with a little help from an AI, and you don't have to write any code.

---

## First, the big idea: this is not folders and files

Most note systems work like a filing cabinet. You make a folder called **Characters**, a file inside it called **Gary**, and you put your Gary notes in the Gary file. Every note has one home, and *you* decide that home the moment you write it. To reorganize, you move files around.

That breaks down for many fiction writing processes, for one stubborn reason: **ideas don't typically arrive sorted.** Not to mention, ideas often come in a batch. A single thought — *"Gary's magic comes from stones of power"* — is about Gary, *and* your magic system, *and* maybe a theme in the story. In a filing cabinet that note can only live in one drawer, so the other connections quietly vanish — or you copy it into three drawers and now there are three versions drifting out of sync (write a series, and it's worse: the same **Characters** folder gets repeated in every book). And the cabinet forces you to decide your whole structure before you even understand your world yet.

Inspired by Niklas Luhmann's Zettelkasten, Substrate flips it around. Picture a big shoebox of index cards instead of a filing cabinet:

- **Every idea is its own little card**, dropped in the box as it occurs to you. You never decide where it "goes," you don't categorize it, you don't organize it. Quick capture.
- **Copilot labels each card with what it's about** — and a card can carry several labels at once (`gary`, `magic`, `theme`). Nothing is forced into a single drawer.
- **The organized views you probably want — Gary's full character page, a list of everything in Book One — don't sit in folders you maintain. They get assembled on the fly** by putting every card with the right label into one note. Ask for Gary, and his page is built from every Gary card in the box, immediately — organized around what you've actually dreamed up about him over days, weeks or months, and not by filling in a pre-determined blank character sheet.

So the mental shift is: **you stop filing, and you start labeling. You stop building folders, and you start asking for views.** "Reorganizing" isn't dragging files between folders anymore — it's just asking a different question of the same pile. The pile of cards only grows as you add ideas; what changes is the view you call up from it.

That one change is the whole paradigm. The cards are called **sparks**. The assembled views are **canonical pages** (one settled topic) and the **Book Bible** is a whole book or series at a glance built from canonical pages. A few prompts and notes work like utilities to help you make creative choices about your raw sparks and label them thoroughly. Everything in this manual is just: how to drop cards in, and how to call up the views. Hold onto the shoebox picture and the rest will make sense.

---

## If this were a plugin

Imagine you installed an Obsidian plugin called **Substrate**. Here's what it would feel like to use:

- You **capture** half-formed ideas as fast as you can type — a line of dialogue, a character quirk, a rule of magic — and tag each one with what it's about (or invoke Copilot to do it for you). No filing, no folders to choose, no slowing down. You forget them on purpose.

- You can also import a **pile of notes you already have** as sparks: images of your legal pads, phone notes, old docs — and turn that whole backlog into the same kind of tagged ideas for you, so you start with your real material already inside.

- Months later, you feel ready, so you **review** the character Gary. You call up a special note and Substrate shows you every scrap you ever wrote about him — even the thoughts you jotted while writing about something else — grouped by topic, all in one place, and with contradictions identified. 

You **decide which sparks are strong**, keeping the good ones and rejecting the wrong ones. Bonus: that review and winnowing burns Gary back into your memory, which can prove useful before you start shooting prose onto the page.

- Then, on command, Substrate **reports**: it gathers the sparks you approved and writes them up as one clean page — traits grouped, contradictions flagged, gaps named. That page is your official Gary (or setting, or magic system, or...) reference. If you change your mind, or find a problem to correct, or add new ideas, you don't edit this page. You add or fix the spark, and then you regenerate this page.

- When you sit down to write a scene, you can ask Substrate to build you a special version of one of these pages: **a scene cheat sheet** containing exactly the people, places, and things in that scene, which you can export or keep open while you draft.

Substrate is **not actually a plugin** — nobody wrote one. But it is that workflow, built from a handful of off-the-shelf Obsidian plugins plus an AI, with no code for you to write and nothing custom to maintain. 

If you read nothing else, I'd read **"What you can make"** (just below) and **§8 (How to use it)**, then run the **§9.5 smoke test** as your quickstart.

## Three things to get straight first

I'm going to assume you know your Obsidian basics, so this is just the parts specific to Substrate that are easy to misread:

1. **There are no special note "types."** Sparks, canonical pages, the Book Bible, the Spark Catalog — every one of them is just an ordinary `.md` note. What makes them different is only where they sit and what's inside them. When this guide says "make a note," it means exactly that--add note. I've pre-built the ones with anything tricky inside (the Dataview views), so you usually just drop ours in.
2. **Tags have to live in a note's Properties, not typed loose in the body.** Substrate's whole "gather everything about Gary" trick depends on the tag being in the `tags:` Properties field. A `#gary` typed in the middle of your text won't be found. The Substrate templates already put tags in the right place, so if you use them you're fine.
3. **The AI lives in a side panel (the Copilot plugin) and never acts on its own.** You run a prompt already written for you (sometimes you edit a placeholder word or two); its answer appears in the Copilot panel; you copy what you want from the result into a note. Copilot never edits or overwrites your pages behind your back.

---

## What you can make (your tools at a glance)

Before any setup, here's the whole toolkit — everything Substrate can produce for you, in plain terms. The rest of the manual is just how to make each one.

- **Spark** — a single captured idea. *For:* never losing a thought, no matter how or when it hits you. *How:* new note, type it, tag it. (Five seconds.)

**A thought about catching ideas away from the desk.** Your best ideas might ambush you in the shower, arrive in a dream, sneak up on you while walking. You might catch them on your phone, or a legal pad, or a Moleskine notebook. That's fine. Substrate includes a way to bulk-import a backlog of old notes (see §8 B). As a creative, capturing your ideas is a recurring task, not a one-time event, so many creatives will probably use bulk import semi-frequently.

- **Canonical note** — your settled, official answer about one thing: a character, a place, a magic rule, a faction. *For:* the page you actually write from; it keeps your details from drifting mid-draft. *How:* once you've culled a topic's sparks down to your official ones (using the Spark Assembler or Catalog), Copilot creates a **report** by organizing them into a page (called **synthesis** for short). You write from the report; you don't hand-edit it — to make changes, you fix the spark and regenerate the report.

> **Tags collect, links connect.** Two ways things relate in Substrate, doing two different jobs. **Tags** (in Properties) are how Substrate *gathers*: `{#gary}` pulls every Gary spark into a synthesis. **Links** (`[[Gary]]`) are how you *navigate* between finished pages — Obsidian tracks them as backlinks automatically. Tag to collect; link to connect.

- **Spark Assembler** — a reviewer that lists a topic's sparks grouped into categories called **aspects** (for a character it might be appearance, mannerisms, relationships…). You can click these summary lines to reach the underlying spark. *For:* reviewing and making creative decisions about a topic before you synthesize. *How:* open it, set a topic, put a `#rejected` in the tags of ideas you don't want. Maybe break them into multiple sparks and just `#rejected` part of a spark.

- **Spark Catalog** — a page that shows you the full text of every *raw* spark on a topic in one place (or every one you *rejected*). *For:* brainstorming against your unfiltered pile, or reviewing what you cut. *How:* open the Spark Catalog and type the topic in the front matter.

- **Scene Cheat Sheet** — build a tight one-pager for the exact scene you're about to write: just the people, places, and rules in play. *For:* keeping continuity while you draft (in Scrivener, Word, or right in Obsidian). *How:* run the scene prompt, fill in who/where/when.

- **Book Bible** — a per-book or per-series view that lists everything settled in that book: characters grouped by **priority** (Primary, Secondary, Tertiary) with the option of adding role (Protagonist, Antagonist, Guide, etc.), or posture (Believer, Deflector, etc.), everything else by type — all clickable; plus a full-text **export** version with a table of contents. *For:* seeing/sharing a whole project's world. *How:* open it, set `series` or `book` — it builds itself.

- **Export** — any canonical page, or a whole book's bible, turned into a PDF or Word file. *For:* reading your story bible offline — on your phone, in print, on a plane. *How:* one click ("Export to PDF") on a page, or the Book Bible Export note for a whole book.

- **The Rejected Pile** — ideas you killed but Substrate keeps around. *For:* nothing you write is ever truly gone; you can revisit or resurrect it. *How:* tag a spark `#rejected` and it files itself away, out of your synthesis but still there.

What you'll actually *do*, if you like the workflow: 
**capture** ideas (or bulk-import old ones), 
**review and decide about** a topic in the Spark Assembler. That's where you keep or reject,
**synthesize** the survivors into a report page, and then 
**write** with your canonical pages and scene sheets handy. 

§8 walks each of these click-by-click.

---

## 1. Intentionally left blank.

---

## 2. Vault structure

I like to create **one vault per story universe** — one connected world, however many books or stories live in it — so that everything in that world can cross-pollinate. (More on that in §11.) Inside the vault:

```
UniverseVault/              ← one world, however many projects share it
├── Sparks/                 ← every spark ever, in one flat pile
│
├── Canonical/              ← your settled reports — FLAT, named Type_Name (e.g. Character_Gary)
│   ├── _Canonical Index.md ← browse reports by type + a "not in any synthesis yet" list
│   ├── _Book Bible.md      ← live series/book bible, organized and linked 
│   └── _Book Bible Export.md ← full-text + table of contents, for PDF/Word export
│
├── Themes/                 ← reports on the motifs in your notes (one report per recurring theme)
├── Rejected/               ← killed ideas, kept so you can still browse them
├── SceneReports/           ← the scene cheat sheets you can generate
├── Exploratory Prose/      ← raw prose you want to harvest sparks from
├── Spark Catalog.md        ← every last spark on a topic, full text, includes rejected
├── Spark Assembler.md      ← review a topic's sparks, categorized, linked, headers only
├── _Prompts/               ← shipped prompts — copy into Copilot's folder
├── _External AI Prompts/   ← OCR / Bulk Import / Big-Topic prompts for AIs outside Obsidian (optional)
├── _Templates/             ← Substrate templates: Spark, Canonical, Theme, Loose Threads, Scene Report
├── _tags.md                ← the master tag list
└── MANUAL.md · INSTALL.md · README.md · CHANGELOG.md · LICENSE  ← docs
```
Each folder also holds a small README.

- **`Sparks/` stays flat — no sub-folders.** You find sparks by tag and by search, not by browsing.
- **`Canonical/` also flat** Each page is a single `.md` named `Type_Name` (e.g. `Character_Gary`, `Magic_Stonebinding`) with an `aliases:` of the bare name so `[[Gary]]` links still resolve. You **browse by the `_Canonical Index`**, which groups pages by their `type:` property — so categories are *emergent* (a new `type: dark events` just appears, no folder needed). Make a sub-folder for your own comfort if you like; the Index ignores folders entirely.
- **`Rejected/`** is browsing convenience only — the `#rejected` *tag* is what keeps ideas out of synthesis, not the folder.

---

## 3. How Substrate knows what belongs to which book

Here's the **`_Book Bible`** picture: say you write in one world, but one series is set in the deep past, another in the far future, plus a few unrelated short stories in between. You **don't** make a folder per series or per book. Every character from every story starts life as a spark. Each becomes a canonical page in `Canonical/`. And when you want to see just one project's world, you open the **`_Book Bible`** and set its `book` (or `series`) field to the book or series of your choice. 

Which book a character belongs to isn't a folder and isn't a tag on the spark. Book Bibles only contain your decided canon, not sparks that have yet to be finalized. Two labels make it work, and comprise the whole convention:

- **On a canonical note:** You set the `series:` and `book:` labels in its Properties — `book: PastBook` or, if a character appears in both, `book: [Book One, Book Two]`. This is the *only* place book membership lives, and it's what the Book Bible reads to assemble each project. You set it when you finish the page, not before.

- **On a spark:** just `#tags` for what it's about (`#gary`, `#magicprinciples`). A spark never needs a book label — you often don't even know which book a shower-thought belongs to yet, and one idea can feed several books at once.

That's it: **canonical notes carry `series:`, `book:`, and `type:`; sparks carry tags.** (A character in a series gets the series on its page, and a `book:` list — `[Book 1, Book 2]` — if it appears in more than one.)

---

## 4. The plugins you'll install

All from **Settings → Community plugins → Browse**. Here's what each one does *for you* — you don't need to know how they work.

| Plugin | What it does for you |
|---|---|
| **Copilot** (by Logan Yang) | The AI you talk to inside Obsidian. It reads your tagged notes and reports the reference pages and scene sheets. Needs an API key (see §5). Note: several plugins are named "Copilot" — install this author's. |
| **Dataview** | Powers the auto-updating views — the Book Bible, the Canonical Index, the Spark Assembler, and the Spark Catalog. You'll use the ones we provide; you won't write any of it. (Turn on its **JavaScript Queries** — INSTALL.) |
| **Smart Connections** | Surfaces related sparks you'd forgotten while you're planning a scene — your "you also thought about this" helper. Runs privately on your own machine; just let it index once. |
| **Templater** | Runs the templates — they *prompt* you for each page's fields (Spark, Canonical, Theme, Loose Threads, Scene Report). Make pages with "Templater: Create new note from template." |
| **Auto Note Mover** | The moment you tag a spark `#rejected`, it moves it into `Rejected/` for you. Set **one** rule only: tag `#rejected` → folder `Rejected/`. |
| **Advanced Merger** | Glues a folder of pages into one document for export (right-click folder → merge). |
| **Note Composer** (built-in) | Lets you hand-split a note that got merged wrong during import. Turn it on in core plugins. |

---

## 5. Setting up AI

You'll use an AI for three things: **building reference pages** (ongoing, inside Obsidian), **capturing ideas from hard-copy** (now and then), and **bulk-importing old notes** (now and then). I find using Copilot in Obsidian and an AI of your choice outside Obsidian for different tasks works well.

**Inside Obsidian — Copilot with an API key.** Copilot signs in with an API key (made at the AI provider's website), which is separate from any ChatGPT or Claude subscription and bills as you go. For this kind of use it's cheap — usually pennies per page. The one thing that can cost real money is rebuilding a *huge* topic (a main character with hundreds of sparks) in a single go, which is better handled outside Copilot. Don't worry, §8's note on big topics covers that. 

Privacy: API text generally isn't used to train the model, but check your provider's current terms.

**For heavy lifting — An AI like Claude Code, Cowork Codex, ChatGPT Claude.** The advanced ones, like the coding models, can read and write files directly, with no per-use billing, so if you already have a subscription, they're the right tool for reading handwriting and importing piles of old notes. 

### Reading your handwriting with Claude
Modern AI reads messy handwriting surprisingly well, because it uses context to figure out a scrawl instead of matching letter by letter.

1. **Photograph the pages** — phone camera, good light, one page per shot.
2. **A few pages?** Open the Claude app, attach the photos, paste the OCR prompt (§9c), and copy out the text. 
3. **A lot of pages?** Use Cowork: point it at a folder of photos and ask it to transcribe each one into its own text file.
4. **Proofread.** This is the one step you can't skip — it's good, not perfect, especially on cursive.
5. **Truly awful cursive** Claude can't crack? A specialist service like handwritingocr.com (~$0.12–0.15/page) might work. I always try the free or piggyback route first.
6. Drop the cleaned text into your spark folder; it's ready for §8 B.

---

## 6. The Core Workflow

In one breath, with a little more detail:

Drop ideas into a note in the Sparks/ folder as they hit → open Copilot and run `/Tag Spark` → when a topic reaches critical mass, or whenever you like really, **review and reject** it in the Spark Assembler or Catalog → **synthesize** the survivors into a report (the canonical page) → **write** from your canonical pages and scene sheets → if something's wrong or you change your mind, fix the spark and re-synthesize. That's the whole rhythm. §8 is the click-by-click version.

**Beyond that core workflow**, three things sit *outside* capture→write — each a deliberate, on-demand step that depends on you having synthesized pages first:

- **The Book Bible** (§8 E) is a *view over your synthesized canonical pages*, not part of capture. Once you've settled some pages, set a `series`/`book` and it assembles them for browsing, or exports them as one full-text document. It comes into play when you want to *see or share* a whole book. Empty until you have canonical pages.

- **Scene Reports** (§8 G) are generated *on demand, right before you write a scene*, from your *canonical pages* (not raw sparks) — so they're downstream of the cull.

- **Themes** (§8 H) are *not automatic, by design*. A periodic pass: Theme Discovery proposes motifs, you ratify, you tag the embodying sparks, a theme page gathers them. Themes lag the pile because a theme is an interpretation that needs your yes.

---

## 7. Intentionally left blank.

---

## 8. How to use it — step by step

This is the part to actually follow (plugins installed per §4, starter dropped in per §13). It walks the loop in order — **capture → tag → review & cull (decide) → synthesize (report) → write** — and then the views you reach for around it.

### A. Capture a spark (5 seconds)
1. Run **"Templater: Create new note from template" → Spark** (set `Sparks/` as your default new-note folder so it lands there). It prompts you for the idea — that text becomes the note's body *and* names the note — and optionally a tag or two; leave tags blank to add them next.
2. Run **`/Tag Spark`** in Copilot with the note open. In one pass it adds any entity tags you missed, the **aspect tags** that say which facets the spark touches (`aspect/appearance`, `aspect/relationships`…), and a one-line `summary:`. Paste its frontmatter block over the note's top. Those aspects and that summary are what make step C readable later — don't skip it if you'll ever review this topic.
3. Close it. Keep capture that cheap.

### B. Bulk-import a backlog (once per pile)
Done *outside* Obsidian, in Claude Code or Cowork (they write files), then dragged in — it turns a heap of old notes into proper, tagged, summarized sparks without retyping.
1. Gather your raw material — exported phone/Kindle notes, transcribed handwriting (§5) — into one folder outside the vault.
2. Run the **Import prompt** (§9d) on **one project first**. It splits the material into one spark per idea — each dated, tagged, aspect-tagged, summarized — and pauses to show samples plus the tag list it used.
3. **Check the first batch:** tags sensible and consistent? Fix the list, and save the agreed spellings into `_tags.md`.
4. Drag the finished notes into `Sparks/`.
5. Run the rest, pasting `_tags.md` into the prompt so it reuses your spellings instead of coining new ones.

After this you're in normal mode — new sparks arrive one at a time via step A. You only re-import when you onboard a brand-new pile.

### C. Review & cull a topic — *this is the deciding* (the Spark Assembler)
When a topic has piled up and you're thinking of settling it, this is the step that matters. Open the **Spark Assembler** and set `topic: gary`. It lists every Gary spark **grouped by aspect**: all the appearance ideas together, all the relationships together, each a one-line summary you click to open. Because same-facet sparks sit together, a contradiction (blonde vs ginger) is impossible to miss — open the loser and tag it `#rejected`. A spark that no topic fits gets `#misc` (see §8 I). Working through the pile — keeping what's true, killing what's wrong — *is* the deciding, and it's what burns the world into your memory. When the pile reads clean, the hard part is done; synthesis just reports what survived.

### D. Synthesize — report the page (the main event)
You do this when a topic's cull is clean. The order matters: you make the page **first**, then report into it.

1. **Make the page.** Run **"Templater: Create new note from template" → Canonical** and name it `Character_Gary`. The template fills the frontmatter for you — it derives `type: character`, `aliases: [Gary]`, and `topic: gary` from the name, dates it, prompts you for `series`/`book`, and offers **skippable** pickers for `priority` / `role` / `posture` (characters only). Move it into `Canonical/`, leave the body empty. (`topic: gary` drops Gary off the "To Synthesize" queue; `type: character` is what makes the report organize by aspect.)
2. Open the **Copilot** chat panel, type `/`, pick your **Synthesis** prompt. At the **bottom** of the prompt, set **`TYPE:`** to `character` (the page's type) and the **`{#TAG}`** line to Gary's tag (`{#gary}`). Leave **PRIOR BODY** blank the first time.
3. Send. The AI pulls the full text of every (non-rejected) Gary spark and reports them as the page body — an **Overview** line, then the **aspects** present (Appearance, Mannerisms, Personality, Powers, Backstory, Relationships, Possessions), with Connections / Gaps / Likely Duplicates / Open Contradictions as appendices at the bottom (only the ones that have content). It lands **in the chat panel**.
4. **Drop the report into the page.** On **free Copilot**: open `Character_Gary`, click in the empty body, hover the reply, click **"Insert into document."** (File-path auto-write only works on paid **Plus/Agent**.) You don't edit what it wrote — it's a report. That page *is* canon.
5. **Re-synthesizing later.** When sparks change, fix the spark first, then re-run — but this time paste the page's *current body* into the **PRIOR BODY** slot. The prompt preserves unchanged passages verbatim, updates only what a changed spark affects, and lists what it touched under `## Changed this pass`. Replace the body with the new report. (Never patch the page by hand — the next re-synthesis would overwrite it. Fix the spark.)

> **If a topic is too big** for one pass (a main character with hundreds of sparks), hand that one tag to **Claude Code** pointed at your vault and have it read the sparks in batches. Only your biggest two or three topics, if any.

### E. See a whole project — the Book Bible
Open **`Canonical/_Book Bible`** and set `series` (the whole series) or `book` (one book). It assembles every *finished* page in scope: characters under **Primary / Secondary / Tertiary** with role · posture, everything else by **type**, all clickable, plus a "still needs review" list. Set its optional `type` to narrow to one category — just the cast, or just settings. It rebuilds itself; you never maintain it. (This replaces the old per-book Dashboard.)

- **To export a self-contained bible:** open **`_Book Bible Export`**, set the same scope — a table of contents followed by the *full text* of every page. Export to PDF/Word. (No live links once exported, and no AI — straight assembly.)
- **To navigate across books, or see what's left to build:** the **`_Canonical Index`** lists every page by `type`, flags unreviewed ones, and shows a **To Synthesize** queue — topics with sparks but no page yet, so you never have to remember the cast.

### F. Read the raw pile — the Spark Catalog
`Spark Catalog.md` (vault root). Set `topic` (a tag) and `mode`: `active` shows every live spark on that topic in full; `rejected` shows everything you killed. For brainstorming against unfiltered material or reviewing cuts. (For a *sorted*, cull-as-you-go view instead of a raw dump, use the Spark Assembler — §8 C.)

### G. Scene cheat sheet — right before you write
Run your **Scene Report** prompt in Copilot and fill in who/where/when. It pulls only from your *finished canonical pages* (not raw sparks) and returns a tight one-pager. Make a landing note with **"Templater: Create new note from template" → Scene Report** (it prompts for the scene title and dates it), drop the cheat sheet into the body, and keep it open while you draft — it lives in `SceneReports/`. Re-run before a session as a memory refresh.

### H. Build a theme page (a motif bible)
The themes your book is *about* — trust, a parent's sins, hiding yourself — cut across characters, scenes, and the magic, and they're usually worded so differently that tags and Smart Connections both miss them. The LLM doesn't. So:

1. **Discover (the AI hunts).** In Copilot, run the **Theme Discovery Prompt** (§9f) over a scope of sparks — a character's tag, a few tags, a book's worth. (For the *whole* story at once, run it in Claude Code so it can read everything in batches.) It reads for meaning and proposes candidate motifs plus the specific sparks that embody each.
2. **Ratify (you decide).** Keep the motifs that are really your book's; drop the rest. The AI suggests; you choose.
3. **Tag only the confirmed sparks.** Add the theme tag — **namespaced** as `#theme/...` (e.g. `#theme/redemption`) — to *just* the sparks you approved. The `theme/` prefix groups all your motifs together so you can find them later (see below). **This is the one place theme tags get made — a tiny, earned set for the 5–15 themes that matter, not a taxonomy.**
4. **Make the page.** Run **"Templater: Create new note from template" → Theme** (in `Themes/`). It prompts for the theme name, its tag (e.g. `redemption` → `#theme/redemption`), and the book/series — and wires that tag straight into the page's Dataview block, so there's no `CHANGEME` to edit. The page then auto-collects every spark carrying that tag (and new ones you tag later); you write the "how this motif plays out" section and link the canonical pages it touches (`[[Gary]]`, `[[Stonebinding]]`).

The result is a living **motif bible**: the sparks that embody the theme, plus your read of what it's doing across the story — the connection view that actually helps you write, without a thousand tags.

**Finding your themes later** (you won't remember them all): open **`Themes/_Themes Index`** — a Dataview list of every `#theme/...` tag and how many sparks carry it — or expand **`theme`** in Obsidian's Tag pane. Both show you every motif you've tagged, so you can see what's accrued enough material to deserve a page. The namespace *is* your index.

### I. Loose threads — sparks that don't fit a page
Some sparks are true for the story but don't belong to any character, setting, or magic page — they just don't fit a neat category. Don't lose them:

1. **Tag the homeless ones `#misc`.** A spark earns `#misc` only when no other topic fits. Open `_tags.md` and its "untriaged orphans" query lists every live `#misc` spark — your inbox.
2. **Route each to a book.** Decide which book a `#misc` spark belongs to and swap `#misc` for that book's loose tag, e.g. `#book1-misc`. (Not sure yet? Leave it `#misc`.)
3. **Build a Loose Threads page per book.** Run **"Templater: Create new note from template" → Loose Threads** (in `Canonical/`). It prompts for the book and the loose-tag slug, names the page `Misc_<Book> Loose Threads`, and wires `#<slug>-misc` into its Dataview block. Then run Synthesis on `{#book1-misc}` (TYPE: `loose-threads`) to report its sparks into the body. It shows on that book's Bible like any other page — gated the same way (only what you accepted counts as in the book).

### Keeping tags tidy (do this now and then)
Everything depends on tag spellings matching exactly, so `#magicsystem` and `#magic-system` quietly split a topic in two. Once in a while, open `_tags.md` and run the little audit list in it — near-duplicate spellings show up next to each other so you can merge them. Do this in a batch, never while capturing.

---

## 9. The prompts and templates (reference)

> **You don't have to build any of this by hand.** This vault already includes every template and prompt below, filled in and in the right folders. The listings here are just so you can see and tweak them.

### 9a. Synthesis prompt (reports a canonical page)

The full prompt ships in **`_Prompts/Synthesis Prompt.md`** (and is what `/Synthesis` runs). Rather than reprint it here (it'd drift), here's what it does: you fill three spots at the **bottom** — **`TYPE:`** (`character` → aspect-organized body; anything else → emergent), the **`{#TAG}`** gather line, and an optional **PRIOR BODY** (paste the page's current body to re-synthesize; leave blank the first time). It then reports the topic's non-rejected sparks as the page body — an **`## Overview`**, then (for a character) the aspects present (Appearance · Mannerisms · Personality · Powers · Backstory · Relationships · Possessions), with **Connections / Gaps / Likely Duplicates / Open Contradictions as appendices at the bottom, each omitted when empty**. It never invents, flags conflicts under a `⚠️ CONFLICT` callout, and on a re-synthesis preserves unchanged passages verbatim and lists what changed under `## Changed this pass`.

The `{#TAG}` line is what does the gathering — Copilot swaps it for the full text of every spark with that tag (`{#gary}`). To rebuild a topic that spans facets, use `{#gary, #magicprinciples}`.

### 9b. Scene cheat-sheet prompt

```
Build me a scene crib sheet. The scene:
- WHO: [Gary, Sabel]   - WHERE: [the river temple]
- WHEN: [act 2, after the betrayal]
- WHAT/HOW/WHY: [Gary infiltrates to steal the binding stone; soul-power magic]

Pull ONLY from my canonical notes for these entities (not raw sparks):
{[[Gary]]} {[[Sabel]]} {[[River Temple]]} {[[Book A Magic]]}

Produce a single-page reference: each character's relevant traits, voice, and
current state; the location's relevant details; the rules of any magic in play;
and any contradictions to watch. Keep it tight. Output Markdown.
```

### 9c. Handwriting prompt (run in the Claude app/Cowork)

```
You are an OCR engine. Transcribe the handwriting in this image EXACTLY as
written. Preserve line breaks. Mark any word you cannot read with [?]. Do not
paraphrase, correct, or interpret — transcribe. Output plain text only.
```

### 9d. Import prompt (run in Claude Code/Cowork, not the chat app)

```
I have a folder of messy story/worldbuilding notes at [PATH] — some may be voice-dictated and
garbled, some near-empty templates, some duplicates or different file types. Turn the real
content into individual Markdown "spark" files, written to [OUTPUT PATH]. I'll review them,
then drop them into my Obsidian Sparks/ folder.

WHAT TO SKIP:
- Empty files, and unfilled template sections (blank headings like "Goal:" / "Personality:"
  with nothing under them). Never manufacture a spark from a blank heading.
- Exact-duplicate files — make the spark once.
- Set fully-written, connected narrative prose ASIDE — don't atomize it now; flag it for me to
  handle separately. (Short, unconnected bits of prose are fine — see SCENES.)

Each file, exactly:
  ---
  created: [date from the source if known, else today, as YYYY-MM-DD]
  tags: [entity/topic tags PLUS aspect/... tags (see ASPECTS) — lowercase, NO leading #]
  summary: "[one line, <= 20 words, my wording — see SUMMARY]"
  ---
  <the idea, in my wording>

In the tags list, write every tag WITHOUT a leading # (frontmatter tags omit it): aspect/powers,
not #aspect/powers. A # in the list starts a YAML comment and breaks the note.

GRANULARITY — one COHERENT idea per file, NOT one sentence:
- A spark should hold enough to see the full shape of its idea. Group tightly-related material;
  don't fragment below the point where the context to understand it is lost. When in doubt, chunkier.
- These notes are often half-assembled narrative wholes, so PRESERVE CAUSAL THREADS, not just
  topics. If a detail is doing narrative work (X leads to Y leads to Z), do NOT rip it out into a
  topical spark — that guts the chain. You may COPY the detail into a topical spark, but never
  REMOVE it from the spark where it carries the throughline. Duplication is fine; gutting context is not.

WORDING — keep mine; fix only obvious transcription noise:
- Lightly fix obvious dictation/transcription errors (homophones, run-on punctuation, clear
  mis-hearings). Do NOT rewrite, polish, summarize, or "improve" my ideas or phrasing.
- If a phrase reads as unconventional or a deliberate play on a common expression, transcribe it
  EXACTLY and flag it — do NOT "correct" it to the idiom.
- Where the dictation is too garbled to recover, mark it [?]. Never invent content, names, or plot.
- If the source names the same entity inconsistently (different spellings or names), tag it
  CONSISTENTLY but preserve the variants in the body and FLAG the conflict for me — don't pick one.

TAGS — specific, consistent, never broad:
- Tag by concrete entities and topics. Be SPECIFIC: a tag should name ONE thing, not a category.
- Don't label a relational or sub-entity with a bare generic noun (a character's relative, a
  faction's resource, etc.) — scope it so it's unique (owner + relation). For a person known by a
  nickname/alias, combine name + nickname so two people who share a first name don't merge.
- Do NOT use broad catch-all tags that would match half the pile ("worldbuilding", "writing", "notes").
- Use ONE consistent name per entity — reuse it, never coin a synonym.
- When something is a sub-type of a broader topic, tag BOTH — the broad and the specific.
- Material that belongs to a DIFFERENT project, story, or installment/sequel gets its own distinct
  tag so it won't pollute the main work (e.g. a #sequel tag for sequel ideas).
- Keep notes-to-self and open questions as their own sparks, tagged by their real subject.
- [If I gave you a tag list, use ONLY those where they fit, and propose any new ones separately
  for my approval before using them.]

SUMMARY — one line per spark:
- Add a summary: of <= 20 words capturing the spark's gist, in MY wording, double-quoted (escape
  any inner double-quote as \"). It's what the Spark Assembler shows as the clickable line.

ASPECTS — which facets each spark touches (multi-label):
- Beyond the entity/topic tags, add an aspect/... tag for EVERY facet the spark touches, from
  exactly this set: appearance, mannerisms, personality, powers, backstory, relationships, possessions.
    - voice / how-they-sound -> mannerisms (there is no "voice" aspect).
    - plot is NOT an aspect — if a spark carries plot, use the plot entity tag, not an aspect.
    - possessions = specific objects of specific meaning (a gun, a signature car, a memento) — NOT generic clothing.
    - mannerisms = habitual, characteristic behaviors ("always chews a toothpick"), not one-off acts.
    - appearance includes strength/features described physically (e.g. "knuckles like silver dollars").
- A spark with no character facet (a pure setting or magic-rule note) may carry no aspect tag — that's fine.

SCENES — use a namespaced scene/ family (bare, no #):
- scene/[position] (opening, midpoint, transition, climax, denouement) when the idea is FOR a
  specific structural spot in the story.
- scene/beat when it's an idea that should happen "somewhere," with no fixed position
  ("would be cool if…") — an idea, not written prose.
- scene/snippet for a SHORT, unconnected bit of prose (a stray line of dialogue, a description)
  — a daydream caught in text, not tied into the larger narrative.
- A beat or snippet WITH a known position gets the position tag too.
- (Full, connected narrative prose is set aside — see WHAT TO SKIP.)

THEMES — propose, don't impose:
- As you go, watch for recurring motifs/themes across the notes (e.g. trust, a parent's sins,
  hiding your true self). Do NOT add theme tags by default.
- When you stop for review each batch, also give me a short list of candidate themes you noticed
  and which sparks embody each. I'll tell you which are real.
- For themes I approve, add that theme tag — namespaced as theme/<name> (e.g. theme/trust) — to
  ONLY the sparks I confirmed. Never apply a theme tag without my approval.

PROCESS:
- Work in BATCHES (one source file or section at a time). After each batch, STOP and show me a
  couple of sample spark files plus the FULL tag list you've used so far, and WAIT for me to OK
  the granularity and the tags before continuing. Surface name conflicts and anything ambiguous.
- Also flag, by spark filename, any duplicate-clusters or contradictions you noticed WITHIN this
  batch, so I can cull them now. (A full topic-wide conflict pass happens separately, later.)

--- MY EXISTING TAGS (later runs only) ---
Reuse these; propose any new ones separately for my approval. First run: leave blank.
Later runs: paste your tag list from _tags.md here.
```

> **Tip — talk to the AI about the result.** It's worth discussing with your AI model how it turned the notes into sparks and how it tagged them. It's usually easier to have the AI change the tags on the new `.md` files *before* you move them into Obsidian than to fix them by hand afterward. You can also ask the AI to write your finalized tag list straight into `_tags.md` in your vault.

### 9e. The templates (Spark / Canonical / Loose Threads / Theme / Scene Report)

All five live in `_Templates/` and run on **Templater** — they *prompt* you for what they need and write the frontmatter, so you're not hand-filling fields. Create any of them with **"Templater: Create new note from template."** (The core Templates plugin can't run them — they use Templater's prompts.)

- **Spark** — one prompt for the idea (which also names the note) and an optional tag or two; `created` is dated. Then run `/Tag Spark`.
- **Canonical** — you name the note `Type_Name` (e.g. `Character_Gary`); it derives `type` (the prefix), `aliases` (the bare name), and a `topic` guess from the name, prompts for `series`/`book`/`topic`, and — if the type is `character` — offers **skippable** pickers for the fixed lists: `priority` = Primary/Secondary/Tertiary; `role` = Protagonist/Antagonist/Contagonist/Guide/Sidekick/Love_Interest/Temptress; `posture` = Protector/Deflector/Believer/Doubter/Thinker/Feeler. `review` starts `unreviewed`; the body is left empty for synthesis. (`topic:` drops the page off the "To Synthesize" queue; the Index/Bible surface anything not `reviewed`.)
- **Loose Threads** — a canonical page for accepted ideas that fit nothing else. Prompts for the book and the loose-tag slug, names the page `Misc_<Book> Loose Threads`, and wires `#<slug>-misc` into its Dataview block; synthesize it (`TYPE: loose-threads`) like any page. See §8 I.
- **Theme** — prompts the theme name, its tag, and the book, and wires `#theme/<tag>` straight into its Dataview block (no `CHANGEME`). You hand-write the "how this motif plays out" section. See §8 H.
- **Scene Report** — prompts the scene title and dates a landing note in `SceneReports/` for the pasted cheat sheet. See §8 G.

*The old per-book Book Dashboard template is gone — the live `_Book Bible` does its job (set its `book`).*

### 9f. Theme Discovery prompt (find motifs — run in Copilot, or Claude Code for the whole vault)

```
You are helping me find the recurring THEMES / motifs in my story notes so I can build theme
pages. Below the marker I've injected a body of sparks.

Read them for MEANING, not keywords. Find the motifs that echo across different characters,
scenes, and systems even when worded completely differently (e.g. trust/betrayal, a parent's
sins passed down, hiding your true self).

For each candidate theme give me:
1. A short name + one-line description of the motif.
2. The specific sparks that embody it (quote a few words from each so I can find them).
3. One sentence on the rhyme — why they belong together / what it reveals about the story.

Propose; do not decide. List clearest-first. Do NOT tag anything — just surface candidates so
I can pick which are real. End by asking which themes I want to keep.

--- SPARKS ---
{#gary}
```

Swap `{#gary}` for whatever scope you want to hunt within (a character, a few tags, a book's worth). For the **whole story at once**, run this in Claude Code instead, so it can read every spark in batches.

---

## 9.5. Smoke test — prove the gather works (5 minutes)

Do this **once**, before you import your real notes. It checks the one thing everything depends on: that a synthesis pulls *every* note carrying a tag and skips the rejected ones. **The fixtures are already in the vault** — three demo sparks in `Sparks/`:

- `DEMO - gary red boot` — `tags: [gary]`
- `DEMO - gary water` — `tags: [gary]`
- `DEMO - gary king rejected` — `tags: [gary, rejected]`

Steps:

1. Create a blank scratch note anywhere and keep it open (so Copilot's "current note" context can't interfere). Then open a **new** Copilot chat.
2. Type `/` → pick **Smoke Test Prompt** → send. It's already filled in (topic Gary, tag `{#gary}`) — nothing to edit. Hit Chat to send the prompt. *(Don't see it in the `/` list? Reload Copilot — toggle the plugin off/on in Settings → Community plugins, or restart Obsidian — then try again.)* (The full **Synthesis Prompt** is the same thing with blanks you fill per topic; the Smoke Test one is just pre-filled for the demo.)
3. Check two things in the report:
   - It includes **both** the red boot **and** the fear of water → the gather grabbed every `gary` note. ✓
   - It does **not** mention the "lost king" → the rejected note was correctly excluded. ✓
4. **If a note is missing** (e.g. the red boot doesn't show up), the gather isn't pulling everything. Quit and reopen Obsidian so its index refreshes, confirm Copilot has finished indexing, and re-run in a new chat. To prove whether it's Copilot or your notes: open the **Spark Catalog**, set `topic: gary` — Dataview scans the folder directly and can't miss, so it should show all three (the king only in `rejected` mode). If the Spark Catalog shows all three but Copilot's `{#gary}` doesn't, the weak link is Copilot's gather — use the Spark Catalog's output, or the **Big-Topic Synthesis Prompt** in Claude Code, in place of `{#gary}`.
5. When it passes, delete the demo content: the three `DEMO - gary…` sparks **and** the demo cast (every page tagged `zzdemo` — the `Character_*`, `Magic_`, and `Setting_` demo pages in `Canonical/`). Tip: search the vault for `zzdemo` to select them all at once. Then blank the `_Book Bible`'s `series` so it's empty for your own world.

> This won't tell you how big a topic can get before it overflows one pass — you only hit that on a giant topic, and the §8 "too big" note is the fix.

---

## 10. Exporting, in detail

Covered as a task in §8 E. In short: a single page exports to PDF with one click; a whole book is the **`_Book Bible Export`** note (set its scope) then Export to PDF. Use the **Book Bible** to move *around* your world inside Obsidian; use export to *take it with you*.

---

## 11. Vaults, mobile capture, and backup

**One vault per universe.** A connected world — a trilogy, a series, a shared-world set — is one vault, so its books can share characters and lore. A standalone novel in its own world gets its own vault. Notes *about writing craft* are a separate vault from your fiction. (One trade-off, named once: keeping craft notes separate means a craft idea won't surface alongside the story idea it might have cross-pollinated. Your call.)

**Catching ideas on your phone.** Keep one plain capture file — your phone's Notes app, or an `inbox.md` synced on its own, separate from the live vault. Jot ambush-ideas there; at the desk, turn each into a spark and clear the inbox. This gives you mobile capture without syncing the whole working vault to your phone (which can cause file clashes).

**Backup.** Run the vault locally and back it up to a cloud folder (Dropbox, etc.) rather than live-syncing the vault itself. Tell your cloud tool to skip the plugins' index caches (Smart Connections' `.smart-env/` and Copilot's index) so they don't bloat backups — they rebuild themselves. Your notes are plain text, so they'll outlive any app; keep an occasional zipped copy too.

---

## 12. Easy to forget

- **Tags go in Properties, not loose in the text.** The one habit the whole thing depends on.
- **Tidy your tags now and then** (§8). A misspelled tag silently hides notes from a topic — the most likely way this quietly lets you down.
- **Name people and places consistently.** `[[Sabel]]` only links to a note actually named `Sabel`. A "hollow" link is just a to-do: make that note and the link lights up.
- **The AI proposes; you ratify.** Always eyeball its links and its contradiction/duplicate flags when you decide.
- **Re-run a scene sheet before a session** as a memory refresh — your canonical page may have changed since last time.
- **Importing old notes is a recurring chore,** not a one-and-done.

---

## 13. Quick-start checklist

1. Open this `SubstrateVault` folder as a vault in Obsidian (or copy its folders into an existing vault). Everything's already laid out.
2. Install the plugins (§4): Copilot, Dataview, Smart Connections, Templater, Auto Note Mover (one rule: `#rejected` → `Rejected/`), Advanced Merger, and core Note Composer.
3. Connect the AI (§5): add your **API key** in Settings → Copilot (or set a local model). Confirm Claude Code/Cowork for handwriting + imports.
4. Point Templater at `_Templates/`; **copy** the Copilot prompts from `_Prompts/` (Synthesis, Scene Report, Smoke Test, Theme Discovery, Tag Spark) into Copilot's own `copilot-custom-prompts/` folder (don't re-point Copilot's setting at `_Prompts/`, or you'll hide its built-ins), then **reload Copilot** (toggle the plugin off/on, or restart Obsidian) so it sees them; turn on Dataview's JavaScript queries; let Smart Connections index once.
5. **Run the smoke test (§9.5)** using the demo sparks already in the vault — also your first look at the prompt, the bible, and the Spark Catalog. Don't skip it. Delete the DEMO files only after it passes.
6. Set up your phone capture inbox (§11).
7. Import your backlog (§8 B), one project at a time, settling your tag spellings as you go.
8. To see a project's world, open the **`_Book Bible`** and set its `series`/`book`; the **`_Canonical Index`** shows what's built and what's still to synthesize.
9. Start capturing. Day to day, you live in §8: capture, synthesize a ripe topic, decide, write.

---

## 14. Glossary

- **Spark** — one idea, captured as it arrives, tagged for what it's about, living in `Sparks/`.
- **Aspect** — a facet tag on a spark (`aspect/appearance`, `aspect/relationships`, …); multi-label. Lets the Spark Assembler group a topic's sparks by facet.
- **Summary** — a one-line gist on a spark, shown as its clickable line in the Spark Assembler.
- **Canonical note** — the report synthesis writes from a topic's approved sparks; what you write from. You don't hand-edit it — fix a spark and re-synthesize. Named `Type_Name`, lives flat in `Canonical/`.
- **Synthesis** — having the AI gather a topic's approved sparks and report them into its canonical page.
- **The cull ("deciding")** — your judging of which sparks are true, done in the Spark Assembler (keep/reject); the one step you never automate, and how you memorize your world.
- **Spark Assembler** — review surface: a topic's sparks grouped by aspect, for culling before synthesis.
- **Spark Catalog** — a page that shows every raw (or every rejected) spark on a topic, in full.
- **Canonical Index** — navigator: all canonical pages by type, plus a "to synthesize" queue.
- **Book Bible** — a per-book/series view of finished pages (cast by priority, others by type); a companion Export version renders full text + TOC.
- **Scene cheat sheet** — a one-page reference for a specific scene, pulled from canonical pages.
- **Rejected** — a spark you've set aside; kept and browsable, but ignored by synthesis.
- **`#misc` / Loose Threads** — homeless sparks routed to a per-book "Loose Threads" canonical page.

---

*"The Substrate Method" is just a name — rename it to whatever you like. The way of working is the point.*
