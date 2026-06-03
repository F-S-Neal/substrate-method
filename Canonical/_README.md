# Canonical
Your settled pages — one per character, place, magic rule, faction, theme, etc. They live **flat
in this folder**, each named `Type_Name` (e.g. `Character_Gary`, `Magic_Stonebinding`), with the
bare name in `aliases:` so `[[Gary]]` links still resolve.

You don't browse by folder — you browse by the **`_Canonical Index`** (groups pages by their
`type:` property, so categories are emergent: a new `type: dark events` just appears) and the
**`_Book Bible`** (a per-series/book view; characters by priority, everything else by type). The
**`_Book Bible Export`** renders a scope as full text + a table of contents for PDF/Word.

Make a sub-folder for your own comfort if you like; the Index and Bible ignore folders entirely —
they read the `type:`, `series:`, and `book:` properties.
