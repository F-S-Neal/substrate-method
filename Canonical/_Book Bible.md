---
series: Demo Series
book: 
type: 
---

# Book / Series Bible

**How to use:** set **`series`** (above) to see the whole series, or **`book`** to see just one book. Optionally set **`type`** to limit to one category (e.g. `character`, `setting`). Characters appear grouped by **priority** with their *role · posture*; everything else groups by **type**. Every entry links live to its canonical page. (For a self-contained, full-text, exportable version, use **_Book Bible Export**.)

Requires Dataview with **Enable JavaScript Queries** ON.

```dataviewjs
const SERIES = dv.current().series, BOOK = dv.current().book, TYPEF = dv.current().type;
const match = (val, want) => val == null ? false
  : (Array.isArray(val) ? val.map(String).includes(want) : String(val) === want);
const aliasOf = (p) => (p.aliases && p.aliases[0]) ? String(p.aliases[0]) : p.file.name;
const link = (p) => dv.fileLink(p.file.path, false, aliasOf(p));
const byName = (a,b) => aliasOf(a).localeCompare(aliasOf(b));

let pages = dv.pages('"Canonical"')
  .where(p => !p.file.name.startsWith("_") && !p.file.path.includes("_Dashboards"))
  .where(p => p.file.path !== dv.current().file.path);

if (BOOK)        pages = pages.where(p => match(p.book, BOOK));
else if (SERIES) pages = pages.where(p => match(p.series, SERIES));
else { dv.paragraph("⚠️ Set `series` or `book` in this note's Properties to build the bible."); }

if ((BOOK || SERIES) && TYPEF)
  pages = pages.where(p => String(p.type).toLowerCase() === String(TYPEF).toLowerCase());

if (BOOK || SERIES) {
  // Cast — characters grouped by priority
  const chars = pages.where(p => String(p.type).toLowerCase() === "character").array();
  if (chars.length) {
    dv.header(1, "Cast of Characters");
    const order = ["Primary","Secondary","Tertiary"];
    const byPri = {};
    for (const p of chars) { const k = p.priority ? String(p.priority) : "(unranked)"; (byPri[k] ??= []).push(p); }
    const keys = Object.keys(byPri).sort((a,b) => {
      const ia = order.indexOf(a), ib = order.indexOf(b);
      if (ia<0 && ib<0) return a.localeCompare(b);
      if (ia<0) return 1; if (ib<0) return -1; return ia-ib;
    });
    for (const k of keys) {
      dv.header(2, k);
      dv.list(byPri[k].sort(byName).map(p => {
        const meta = [p.role, p.posture].filter(x=>x).map(String).join(" · ");
        return meta ? `${link(p)} — *${meta}*` : link(p);
      }));
    }
  }
  // Everything else — grouped by type
  const others = pages.where(p => String(p.type).toLowerCase() !== "character").array();
  const byType = {};
  for (const p of others) { const t = p.type ? String(p.type) : "(untyped)"; (byType[t] ??= []).push(p); }
  for (const t of Object.keys(byType).sort()) {
    dv.header(1, t.replace(/^\w/, c => c.toUpperCase()));
    dv.list(byType[t].sort(byName).map(link));
  }
}
```
