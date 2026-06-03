---
book:
---
# Canonical Index

**How to use:** leave `book` (above) **blank** to browse *everything* by type — all your characters, all your settings, all your magic, whatever types have emerged. **Set `book`** to a book or series name to get just that book's world. Each entry links to the canonical page — click it to open the report. Types are data-driven: any new `type:` you put on a canonical page shows up here on its own.

Requires Dataview with **Enable JavaScript Queries** ON.

```dataviewjs
const BOOK = dv.current().book;
const inBook = (p) => {            // exact match — single value OR a list; no substring collisions
  const b = p.book; if (b == null) return false;
  return Array.isArray(b) ? b.map(String).includes(BOOK) : String(b) === BOOK;
};
let pages = dv.pages('"Canonical"')
  .where(p => p.file.path !== dv.current().file.path)  // skip THIS index note
  .where(p => !p.file.name.startsWith("_"))            // skip READMEs/templates
  .where(p => !p.file.path.includes("_Dashboards"));  // skip dashboard notes
if (BOOK) pages = pages.where(inBook);

const groups = {};
for (const p of pages) {
  const t = (p.type ?? "(untyped)").toString();
  (groups[t] ??= []).push(p);
}

for (const t of Object.keys(groups).sort()) {
  const list = groups[t].sort((a,b) => a.file.name.localeCompare(b.file.name));
  dv.header(2, t.replace(/^\w/, c => c.toUpperCase()) + `  (${list.length})`);
  dv.list(list.map(p => p.file.link));
}
```
## ⚠️ Canonical pages still needing review
```dataviewjs
const BOOK = dv.current().book;
const inBook = (p) => {
  const b = p.book; if (b == null) return false;
  return Array.isArray(b) ? b.map(String).includes(BOOK) : String(b) === BOOK;
};
let pages = dv.pages('"Canonical"')
  .where(p => !p.file.name.startsWith("_") && !p.file.path.includes("_Dashboards"))
  .where(p => p.review && p.review !== "reviewed");
if (BOOK) pages = pages.where(inBook);
dv.list(pages.sort(p => p.file.name).map(p => p.file.link));
```

## To Synthesize
### Topics with sparks but no canonical page yet

Each is a `{#tag}` you haven't synthesized into a canonical page (characters, setting locations, etc.)
```dataviewjs
const counts = {};
for (const p of dv.pages('"Sparks"')) {
  if (p.file.tags.includes("#rejected")) continue;
  for (const t of (p.file.tags ?? [])) {
    if (t.startsWith("#aspect/") || t.startsWith("#scene") || t.startsWith("#theme")) continue;
    const n = t.replace(/^#/, ""); counts[n] = (counts[n] ?? 0) + 1;
  }
}
const done = new Set();
for (const p of dv.pages('"Canonical"')) {
  if (!p.topic) continue;
  (Array.isArray(p.topic) ? p.topic : [p.topic]).forEach(t => done.add(String(t)));
}
const todo = Object.entries(counts)
  .filter(([t]) => !done.has(t))
  .sort((a,b) => b[1]-a[1] || a[0].localeCompare(b[0]));
dv.paragraph(`${todo.length} topics that still might need a canonical page.`);
dv.list(todo.map(([t,c]) => `${t}  —  ${c} sparks`));
```
