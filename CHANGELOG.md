# Changelog

## v1.3.1 — June 2026

### Added
- **Bulk Tag Sparks** prompt (`_External AI Prompts/`) — the batched, file-writing version of
  `/Tag Spark`: tag many existing sparks at once in Claude Code / Cowork / Copilot Agent. Keeps
  existing tags, pauses after the first 5 for review, and skips already-tagged sparks.

## v1.3 — June 2026

Makes page creation hands-off and finishes the report-model cutover. No new plugins.

### Added
- **Templater-powered templates for every page type.** Canonical, Loose Threads, Theme, Spark,
  and a new **Scene Report** template now *prompt* for what they need and fill the frontmatter
  for you. Canonical derives `type` / `aliases` / `topic` from the note's name and offers
  **skippable** pickers for priority / role / posture; Theme and Loose Threads wire your tag
  straight into their Dataview block (no more `CHANGEME`). Create them with **"Templater: Create
  new note from template."**
- **`## Overview`** — synthesis now opens every report with a 1–2 sentence "who/what at a glance."

### Changed
- **The Synthesis prompt takes a typed `TYPE:` instead of a pasted frontmatter.** All the
  fill-in spots (TYPE, the `{#tag}` gather, an optional prior body) sit at the bottom of the
  prompt for easy reach. You no longer copy Obsidian Properties.
- **Report appendices moved to the bottom and omitted when empty** — Connections, Gaps, Threads,
  Likely Duplicates, and Open Contradictions appear only if they have content.
- **Templates ship empty-bodied** (synthesis writes the body) — no skeleton sections, no
  duplicate H1 title, no instruction comments.
- **Roles are capitalized** to match postures: Protagonist, Antagonist, Contagonist, Guide,
  Sidekick, Love_Interest, Temptress.
- **A demo cast ships** (a few `zzdemo` characters covering every role and posture) so the Book
  Bible / Canonical Index are populated out of the box and the property pickers show the full set.
- Dropped the unused `tags` field from the Canonical template.

### Fixed
- Empty "Likely Duplicates" / "Open Contradictions" headings no longer appear on fresh pages
  (they came from the old template skeleton).

## v1.2 — June 2026

Reframes what a canonical page *is* and how synthesis works. No new plugins; the change is
conceptual + a rewritten Synthesis prompt. If you're on v1.1, your pages still work — but the
workflow around them changed, so read this.

### Changed
- **The canonical page is now a REPORT, not a hand-edited draft.** Synthesis generates it from
  your approved sparks; you write from it, you don't edit it. The old "convergence" (hand-editing
  the draft into canon) is gone.
- **Deciding moved upstream to the Spark Assembler.** You decide what's true by keeping/rejecting
  sparks during the cull — that's now the step you never automate and where the generation effect
  lives. Synthesis just reports whatever survived.
- **The fix loop.** When a page is wrong, you fix the underlying spark and re-synthesize — never
  patch the page (the next synthesis would overwrite it).
- **Stub-first synthesis.** You create the canonical note from the template (filling its
  frontmatter, incl. `type:`) *before* synthesizing, then paste the note into the prompt. The
  prompt reads `type:` to decide structure — so the freeform "TOPIC" line is gone. First run you
  paste frontmatter only; later runs you paste the whole page.
- **Character reports are aspect-organized.** A character page is built only from the aspect
  facets present (Appearance · Mannerisms · Personality · Powers · Backstory · Relationships ·
  Possessions); plot/conflict/scene material is excluded (it belongs elsewhere). Non-character
  topics stay fully emergent.
- **Incremental re-synthesis.** Re-running with the page pasted in preserves unchanged passages
  verbatim and reports what it touched under `## Changed this pass` (or "no material change").

### Docs
- MANUAL §1, §2, §7, §8 C/D, §9a, and the glossary rewritten to the report/cull/fix model;
  README and INSTALL updated to match.

## v1.1 — June 2026

A big pass that adds a faceted review layer, a book/series bible, and a flat canonical
structure — plus several fixes. Note: the canonical changes are **structural**; if you built
on v1.0, read "Changed" before updating.

### Added
- **Aspect tags** (`aspect/…`) — multi-label facet tags on sparks (appearance, mannerisms,
  personality, powers, backstory, relationships, possessions) so a topic's sparks can be reviewed
  grouped by facet, with contradictions sitting next to each other.
- **Per-spark `summary:`** — a one-line gist shown as the clickable line in the Spark Assembler.
- **Spark Assembler** — a review note that shows a topic's sparks grouped by aspect (summary-links,
  click to open and `#rejected`), with an `active`/`rejected` toggle, a topic picker, and optional
  `conflicts:` flagging (⚠) between contradictory sparks.
- **Tag Spark** (Copilot prompt) — one click assigns a single spark its entity tags, aspect tags,
  and summary.
- **Loose Threads** workflow — a `#misc` inbox for homeless sparks, per-book `#<book>-misc` routing,
  a Loose Threads canonical template, and an "untriaged orphans" query in `_tags.md`.
- **Canonical fields** — `series`, `topic`, and character-only `priority` / `role` / `posture`
  (fixed option lists), plus `aliases`.
- **_Canonical Index** — pages by type, a "needs review" list, and a **To Synthesize** queue
  (topics that have sparks but no canonical page yet, so you never have to remember the cast).
- **_Book Bible** — a live series/book bible: characters grouped by priority with role · posture,
  everything else by type, all linked; filter by series, book, or a single type.
- **_Book Bible Export** — a full-text + table-of-contents version for exporting a self-contained
  bible to PDF/Word.

### Changed / Renamed
- **Corpus Reader → Spark Catalog.**
- **Aspect Review → Spark Assembler.**
- **Canonical pages are now flat** in `Canonical/` (category subfolders removed), named
  **`Type_Name`** (e.g. `Character_Gary`) with an `aliases:` of the bare name so `[[Gary]]` still resolves.
  Browse by the `_Canonical Index` (groups by `type`), not by folders.
- `_Exploratory Prose` folder → **Exploratory Prose**.
- **Import prompt** now also assigns aspect tags + summaries and flags within-batch duplicates/conflicts.

### Removed
- **Per-book Book Dashboard** (template + demo) — superseded by `_Book Bible` (set its `book`).
- **Canonical category subfolders** — replaced by the flat `Type_Name` convention + `type:` property.

### Fixed
- **Bare `#tags` in prose** (e.g. `#rejected` inside a prompt's instructions) were being read as live
  tags and swept into `Rejected/` by Auto Note Mover — which had silently emptied the Synthesis prompt.
  All tags in prompt/tool-note prose are now backticked so they're inert.
- **Tag Spark** was emitting aspect tags with a leading `#` (which breaks YAML frontmatter); the prompt
  now writes bare tags.
- Tool-note prose reflowed to single lines so it renders cleanly in every editor mode.
