# Bulk Tag Sparks — run in Claude Code / Cowork / Copilot Agent, inside the vault folder

The batch version of `/Tag Spark`: tags many existing sparks at once. Needs an agent that can
**write files** — Claude Code, Cowork, or Copilot Plus / Agent mode. (Free Copilot can't write
to many notes — use `/Tag Spark` one spark at a time there.) Open a terminal, cd into the vault,
start your agent, paste this.

---

You are working inside my Obsidian vault (the current folder). Bulk-tag my sparks.

SCOPE: process every note in `Sparks/` that is NOT yet tagged — i.e., it has no `aspect/…` tag
OR no `summary:` in its frontmatter. Skip notes that already have both, unless I explicitly say
"re-tag everything." (If I name a subfolder or an existing tag above this line, limit to that.)

FOR EACH spark in scope, update ONLY its frontmatter — never touch the body:
- KEEP every existing tag. Add any missing ENTITY tags (who/what it's about: characters, places,
  factions, themes). Reuse the spellings in `_tags.md`; don't coin synonyms.
- Add ASPECT tags — multi-label, ALL that apply — namespaced `aspect/...`, from exactly this set:
  appearance, mannerisms, personality, powers, backstory, relationships, possessions.
    - voice / how-they-sound → mannerisms (there is no `voice` aspect).
    - plot is NOT an aspect — if the spark carries plot, use the `plot` ENTITY tag, not an aspect.
    - possessions = specific objects of specific meaning (a gun, a signature car), not generic clothing.
    - mannerisms = habitual, characteristic behaviors, not one-off acts.
    - appearance includes strength/features described physically.
- Add a one-line `summary:` (≤ 20 words, in double quotes; escape any inner quote as \").
- Leave `created:` exactly as it is.
- CRITICAL: in the `tags:` list write EVERY tag WITHOUT a leading `#` (a `#` starts a YAML comment
  and breaks the note). Write `aspect/powers`, NOT `#aspect/powers`.

WORK IN BATCHES so I can catch drift early:
1. Do the FIRST 5 sparks in scope, write them, then STOP and show me what you tagged each
   (filename → tags + summary) plus the list of entity tags you used. Wait for my OK.
2. On my approval, do the rest. If I fix the tag list, use my corrections and add any newly
   agreed spellings to `_tags.md`.

When done, report: how many sparks you tagged, how many you skipped (already tagged), and any
you were unsure about so I can check them.
