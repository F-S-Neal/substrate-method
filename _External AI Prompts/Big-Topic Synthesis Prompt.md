# Big-Topic Synthesis Prompt — run in Claude Code / Codex, inside the vault folder

Use this only when one topic has so many sparks that Copilot's {#tag} won't take
them in one pass. Open a terminal, cd into the vault, start your agent, paste this.

---

You are working inside my Obsidian vault (the current folder). I want a synthesis
REPORT for ONE topic: [Gary], tag `#gary`. The canonical page is a report generated
from my approved sparks — I write from it, I do not hand-edit it. Reflect the sparks
faithfully; don't improve them.

READ THE PAGE FIRST:
- The canonical note is Canonical/<Type>_<Entity>.md (flat folder, e.g.
  Canonical/Character_Gary.md). Read its frontmatter `type:`.
  - type: character → build a CHARACTER body (ORGANIZE 1–2).
  - any other type (setting, magic, faction, theme) → build an EMERGENT body (ORGANIZE 3).
- If the note has only frontmatter (no body), this is the FIRST synthesis: write a
  fresh body, no "Changed this pass" line. If it already has a body, treat that body
  as the prior report and re-derive INCREMENTALLY: reproduce unchanged passages
  verbatim, change only what a changed spark forces, and start the output with
  "## Changed this pass" listing each change + its spark ("no material change" →
  reproduce the prior report verbatim).

GATHER (be exhaustive — this is the whole point):
- Read EVERY note in Sparks/ whose frontmatter `tags` include "gary".
- EXCLUDE any note whose tags include "rejected".
- Use the note bodies, not just titles. Don't sample — all of them.
- Too many to hold at once? Process in batches, write a partial report per batch,
  then combine the partials into one.

ORGANIZE:
1. CHARACTER body, in order: a `## Overview` (1–2 sentences, who they are at a glance), then
   the aspect facets PRESENT on the sparks — these exact headings, in order, omitting any with
   no material: Appearance · Mannerisms · Personality · Powers · Backstory · Relationships · Possessions.
   Narrative prose under each, not fragments.
2. EXCLUDE non-facet material from a character page (plot, conflicts, scene ideas,
   role, arc) — it belongs elsewhere. A character page is WHO they are, not what
   happens to them.
3. NON-CHARACTER body: start with `## Overview`, then emergent headings the material suggests.

APPENDICES — put these LAST, and OMIT ANY THAT WOULD BE EMPTY:
4. `## Connections` — first mention of any other entity/place/concept as a [[wikilink]].
5. `## Gaps / To Decide` — important missing things. `## Threads to Follow` — "this connects to X" notes.
6. `## Likely Duplicates` — near-identical sparks to merge or cull.
7. `## ⚠️ Open Contradictions` — every unresolved conflict, each kept under a ">  ⚠️ CONFLICT"
   callout. Use ONLY what's in the notes; don't invent. Never pick a winner.

WRITE the report to Canonical/<Type>_<Entity>.synthdraft.md (e.g.
Canonical/Character_Gary.synthdraft.md). Do NOT modify the live note or anything in
Sparks/ — I'll diff the .synthdraft against the page and replace the body myself.

When done, tell me how many sparks you gathered and how many batches you used, so I
can confirm nothing was missed.
