# Tag vocabulary

Your master list of tag spellings. Use a tag from this list when you tag a spark, and paste the
copy-ready line (bottom) into the Import Prompt's "MY EXISTING TAGS" slot so the AI reuses these
instead of coining synonyms. Lowercase, no spaces, no leading #. One canonical spelling per thing.

This ships nearly empty on purpose — it's *your* list. The one demo entry below shows the format;
delete it and add your own as you go. (Obsidian also autocompletes existing tags as you type.)

## People
- gary — the demo character used by the smoke test and the manual's examples (delete once you start)
<!-- add your own: one line per character, `tag — who they are` -->

## Factions & orgs
<!-- e.g.  thecrown — the ruling house  -->

## Magic & world
<!-- e.g.  stonebinding — the demo magic system; magicsystem — how magic works (broad) -->

## Story structure
- plot — plot beats, structure, turning points
- backstory — a character's history / origin
- pitch — loglines, premise, elevator-pitch beats
- sequel — ideas for sequels (kept OUT of main-plot synthesis)
- scene/[position] — opening / midpoint / transition / climax / denouement (scene idea FOR a spot)
- scene/beat — a scene idea with no fixed position ("would be cool if…")
- scene/snippet — short, unconnected bits of prose

## Themes (story-level — #theme/...)
<!-- A tiny, earned set (5–15), made only via the Theme Discovery pass. e.g. theme/redemption -->

## Aspects (character facets — #aspect/...)
Which facets of a topic a spark touches, so review can group sparks. Multi-label — a spark carries
as many as apply. Used for grouping/relevance, not for the {#tag} gather. (plot is NOT an aspect —
it stays the #plot tag. No "voice" aspect — it folds into mannerisms.)
- aspect/appearance — how they look (incl. strength described physically, e.g. "knuckles like silver dollars")
- aspect/mannerisms — habitual, characteristic behaviors ("always chews a toothpick"); how-they-sound folds in here
- aspect/personality — temperament, worldview, values
- aspect/powers — unusual / supernatural abilities or feats
- aspect/backstory — history, origin, one-time biographical facts
- aspect/relationships — ties to other characters
- aspect/possessions — specific objects of specific meaning (a gun, a signature car, a memento); NOT generic clothing

## Canonical page fields (frontmatter, not tags)
- series: — the series a page belongs to (every book in the series shares it)
- book:   — the specific book
- type:   — category the Index/Bible group by (character, magic, setting, …; emergent)
- topic:  — the spark tag this page was synthesized from
- Character-only, fixed lists:
  - priority: Primary | Secondary | Tertiary
  - role:     Protagonist | Antagonist | Contagonist | Guide | Sidekick | Love_Interest | Temptress
  - posture:  Protector | Deflector | Believer | Doubter | Thinker | Feeler

## Settings / places
- setting — a location type or place note
<!-- add named places as you coin them, e.g.  rivertemple — the demo location -->

## Meta / other
- rejected — (hand-set) a killed spark; excluded from synthesis
- misc — (hand-set) a "homeless" spark: nothing else fits. The untriaged-orphan inbox. To file it, swap `#misc` for a book's `#<book>-misc`.
- <book>-misc — a book's loose-ends routing tag (e.g. `#book1-misc`). Feeds that book's "<Book> — Loose Threads" canonical page. Book membership still comes from that page's `book:` property, not this tag.

## Tag audit (lists every tag in Sparks/ with counts — spot drift/synonyms)
```dataview
TABLE length(rows) AS count
FROM "Sparks"
FLATTEN file.tags AS tag
GROUP BY tag
SORT count ASC
```

## Untriaged orphans (#misc — route each to a book's #<book>-misc)
```dataview
LIST
FROM "Sparks"
WHERE contains(file.tags, "#misc") AND !contains(file.tags, "#rejected")
SORT created ASC
```

## Copy-ready tag list (for the Import Prompt)
Select the line this renders and paste it into the Import Prompt's "MY EXISTING TAGS" slot.
Entity/topic tags only — theme/ and scene/ tags are excluded (those get applied by their own rules).
```dataviewjs
const tags = new Set();
for (const p of dv.pages('"Sparks"'))
  for (const t of (p.file.tags ?? [])) {
    if (t.startsWith("#theme") || t.startsWith("#scene") || t.startsWith("#aspect")) continue;
    tags.add(t.replace(/^#/, ""));
  }
dv.paragraph([...tags].sort().join(", "));
```
