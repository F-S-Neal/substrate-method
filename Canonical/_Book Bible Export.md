---
series: 
book: 
---

# Book Bible Export

**How to use:** set **`series`** or **`book`** above. This builds a Contents list followed by the **full text of every canonical page** for that scope (characters by priority first, then other types). Then **Export to PDF** (or to Word via a plugin) for a self-contained bible — no live links needed, the text is all here. No AI is used; this is straight assembly of your canonical pages.

Requires Dataview with **Enable JavaScript Queries** ON.

> Heads-up: rendering many full pages can be heavy, and Dataview-in-PDF export can be finicky — if the export looks off, export in smaller scopes (one book at a time) and confirm in Reading view first.

```dataviewjs
const SERIES = dv.current().series, BOOK = dv.current().book;
const match = (val, want) => val == null ? false
  : (Array.isArray(val) ? val.map(String).includes(want) : String(val) === want);
const aliasOf = (p) => (p.aliases && p.aliases[0]) ? String(p.aliases[0]) : p.file.name;
const byName = (a,b) => aliasOf(a).localeCompare(aliasOf(b));

let pages = dv.pages('"Canonical"')
  .where(p => !p.file.name.startsWith("_") && !p.file.path.includes("_Dashboards"))
  .where(p => p.file.path !== dv.current().file.path);
if (BOOK)        pages = pages.where(p => match(p.book, BOOK));
else if (SERIES) pages = pages.where(p => match(p.series, SERIES));
else { dv.paragraph("⚠️ Set `series` or `book` in this note's Properties."); }

if (BOOK || SERIES) {
  // order: characters by priority, then everything else by type
  const order = ["Primary","Secondary","Tertiary"];
  const priRank = (p) => { const i = order.indexOf(String(p.priority)); return i<0 ? 99 : i; };
  const chars = pages.where(p => String(p.type).toLowerCase() === "character").array()
    .sort((a,b) => priRank(a)-priRank(b) || byName(a,b));
  const others = pages.where(p => String(p.type).toLowerCase() !== "character").array()
    .sort((a,b) => String(a.type||"").localeCompare(String(b.type||"")) || byName(a,b));
  const ordered = [...chars, ...others];

  dv.header(1, "Contents");
  dv.list(ordered.map(p => dv.fileLink(p.file.path, false, aliasOf(p))));

  for (const p of ordered) {
    dv.header(2, aliasOf(p));
    let body = await dv.io.load(p.file.path);
    body = body.replace(/^---[\s\S]*?---\s*/, "");   // strip frontmatter
    body = body.replace(/^#\s+.*\r?\n/, "");          // strip the page's own H1 (we print the alias as H2)
    dv.paragraph(body.trim());
  }
}
```
