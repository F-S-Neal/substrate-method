---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 0
copilot-command-model-key: ""
copilot-command-last-used: 1780452658381
---
You are helping me turn scattered worldbuilding sparks into a single working
reference page about ONE topic. The page is a REPORT generated from my approved
sparks: I write from it, I do not hand-edit it. When something is wrong I fix the
underlying spark and re-run you — so reflect the sparks faithfully, don't improve
them. Output the report only.

Rule 0 (EXCLUSION): Ignore any fragment whose properties/frontmatter include
`#rejected`. Do not use rejected fragments at all.

WHAT TO BUILD (I set TYPE at the bottom):
- TYPE: character → a CHARACTER body (ORGANIZATION 1–2).
- Any other TYPE (setting, magic, faction, theme, …) → an EMERGENT body (ORGANIZATION 3).
- If I pasted a PRIOR BODY at the bottom → this is a RE-SYNTHESIS, follow INCREMENTAL.
  If the PRIOR BODY slot is empty → this is the FIRST synthesis: fresh body, and do
  NOT include a "Changed this pass" line.

ORGANIZATION
1. CHARACTER body, in this order:
   - ## Overview — 1–2 sentences: who this character is at a glance.
   - then the aspect facets PRESENT on the sparks, these exact headings in this order,
     omitting any with no material (never an empty heading, never an invented facet):
     Appearance · Mannerisms · Personality · Powers · Backstory · Relationships · Possessions
   Narrative prose under each, not bullet fragments.
2. EXCLUDE non-facet material from a character page. Plot, conflicts, scene ideas,
   story role, arc, and turning points carry no aspect and do NOT belong here. A
   character page answers WHO they are, not what happens to them.
3. NON-CHARACTER body: start with ## Overview (1–2 sentences), then emergent headings
   the material suggests. No fixed schema.

INCREMENTAL (only when a PRIOR BODY is pasted)
4. Treat the prior body as the baseline. Reproduce any passage whose supporting sparks
   are UNCHANGED verbatim — do NOT re-paraphrase. Revise/add/remove only what a changed
   spark forces. Keep the section structure; add a section only if a spark needs a new home.
5. Begin the output with `## Changed this pass` — each change + the spark that caused it.
   No material change → reproduce the prior body verbatim and write only:
   "Changed this pass: no material change."

APPENDICES — put these LAST, in this order, and OMIT ANY THAT WOULD BE EMPTY (no empty headings):
6. ## Connections — link the first mention of any other entity/place/concept as a [[wikilink]].
7. ## Gaps / To Decide — important things the sparks are missing (only if any).
8. ## Threads to Follow — "this connects to X" notes-to-self (only if any).
9. ## Likely Duplicates — near-identical fragments to merge or cull (only if any).
10. ## ⚠️ Open Contradictions — every unresolved conflict, each kept under a
    ">  ⚠️ CONFLICT" callout; never silently pick a winner (only if any).

═══════════════════ FILL IN BELOW ═══════════════════

TYPE: character

TAG (the gather — change to your topic's tag):
{#TAG}

PRIOR BODY (paste the current page's body to re-synthesize; leave blank the first time):


─────────────────────────────────────────────────────
OPTIONAL (Copilot Plus / Agent Mode only — free Copilot: ignore and click "Insert into
document" to drop the report into the page body):
"Write this report to Canonical/<Type>_<Entity>.synthdraft.md (e.g.
Canonical/Character_Gary.synthdraft.md), leaving the live note untouched, so I can diff
it before replacing the body." The page is a report — you replace its body with the new
one, you don't hand-merge; when it's wrong, fix the spark and re-run.
