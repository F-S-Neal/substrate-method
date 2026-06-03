# Import Prompt — run in Claude Code or Cowork (they can write files)

Point Claude Code/Cowork at your working folder of exported + transcribed notes. On the
FIRST project, omit the tag list so it proposes one; review it and save it into _tags.md.
On LATER projects, paste your _tags.md tags into the slot at the bottom so it reuses them.

---

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
  tags: [lowercase, NO leading #, in the Properties block — entity/topic tags PLUS aspect/... tags (see ASPECTS)]
  summary: "[one line, <= 20 words, my wording — see SUMMARY]"
  ---
  <the idea, in my wording>

CRITICAL: in the `tags:` list write EVERY tag WITHOUT a leading `#` (e.g. `gary, aspect/appearance`).
A `#` in that list starts a YAML comment and silently breaks the note's tags.

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
- Add a `summary:` of <= 20 words capturing the spark's gist, in MY wording, double-quoted (escape
  any inner double-quote as \"). It's what the Spark Assembler shows as the clickable line.

ASPECTS — which facets each spark touches (multi-label, namespaced `#aspect`/...):
- Beyond the entity/topic tags, add an `#aspect`/... tag for EVERY facet the spark touches, from
  exactly this set: appearance, mannerisms, personality, powers, backstory, relationships, possessions.
    - voice / how-they-sound -> mannerisms (there is no "voice" aspect).
    - plot is NOT an aspect — if a spark carries plot, use the `#plot` entity tag, not an aspect.
    - possessions = specific objects of specific meaning (a gun, a signature car, a memento) — NOT generic clothing.
    - mannerisms = habitual, characteristic behaviors ("always chews a toothpick"), not one-off acts.
    - appearance includes strength/features described physically (e.g. "knuckles like silver dollars").
- A spark with no character facet (a pure setting or magic-rule note) may carry no aspect tag — that's fine.

SCENES — use a namespaced `#scene`/ family:
- `#scene`/[position] (opening, midpoint, transition, climax, denouement) when the idea is FOR a
  specific structural spot in the story.
- `#scene/beat` when it's an idea that should happen "somewhere," with no fixed position
  ("would be cool if…") — an idea, not written prose.
- `#scene/snippet` for a SHORT, unconnected bit of prose (a stray line of dialogue, a description)
  — a daydream caught in text, not tied into the larger narrative.
- A beat or snippet WITH a known position gets the position tag too.
- (Full, connected narrative prose is set aside — see WHAT TO SKIP.)

THEMES — propose, don't impose:
- As you go, watch for recurring motifs/themes across the notes (e.g. trust, a parent's sins,
  hiding your true self). Do NOT add theme tags by default.
- When you stop for review each batch, also give me a short list of candidate themes you noticed
  and which sparks embody each. I'll tell you which are real.
- For themes I approve, add that theme tag — namespaced as `#theme`/<name> (e.g. `#theme/trust`) — to
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
