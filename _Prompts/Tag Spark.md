---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 0
copilot-command-model-key: ""
copilot-command-last-used: 1780410367635
---
You tag ONE spark for a Substrate worldbuilding vault. The spark note is given at the bottom
(its current frontmatter + body).

Return ONLY a new frontmatter block — between `---` lines, nothing before or after — that I will
paste over the note's current frontmatter.

Rules:
- KEEP every existing tag. Add any missing ENTITY tags (who/what the spark is about: characters,
  places, factions, themes). Reuse my existing tag spellings; don't coin synonyms.
- Add ASPECT tags — multi-label, ALL that apply — namespaced `aspect/...`, from exactly this set:
  appearance, mannerisms, personality, powers, backstory, relationships, possessions.
    - voice / how-they-sound → mannerisms (there is no `voice` aspect).
    - plot is NOT an aspect — if the spark carries plot, use the `plot` ENTITY tag, not an aspect.
    - possessions = specific objects of specific meaning (a gun, a signature car, a memento) — NOT
      generic clothing or accessories.
    - mannerisms = habitual, characteristic behaviors ("always chews a toothpick"), not one-off acts.
    - appearance includes strength/features described physically (e.g. "knuckles like silver dollars").
- Add a one-line `summary:` (≤ 20 words) capturing the spark's gist, in double quotes; escape any
  inner double-quote as \".
- Leave `created:` exactly as it is.
- CRITICAL: in the `tags:` list, write EVERY tag WITHOUT a leading `#` (frontmatter tags omit it).
  Write `aspect/powers`, NOT `#aspect/powers`. A `#` in the list starts a YAML comment and breaks the note.

Output EXACTLY this shape:
---
created: <unchanged>
tags: [<entity tags>, <aspect/... tags>]
summary: "<one line>"
---

THE SPARK:
{activeNote}
