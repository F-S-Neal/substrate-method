---
topic: gary
mode: active
---

# Spark Assembler

**How to use:** set `topic` above to a tag without the `#` (e.g. `gary`), and `mode` to `active` (hides `#rejected` — your normal review) or `rejected` (shows only the sparks you've killed). View this note in Reading or Live Preview. Under each aspect heading it shows one clickable line per spark — the spark's one-line `summary`, not its full text — and a spark with several `#aspect/...` tags appears under each group. Click a line to open the spark, add `#rejected`, and it drops out (Cmd-click or middle-click opens it in a side pane). Sparks with no aspect tag land under **(unaspected)**; ones with no `summary` show their filename instead.

Requires Dataview with **Enable JavaScript Queries** ON.

**Topics in this vault** (pick one, type it into `topic` above):
```dataviewjs
const counts = {};
for (const p of dv.pages('"Sparks"')) {
  if (p.file.tags.includes("#rejected")) continue;
  for (const t of (p.file.tags ?? [])) {
    if (t.startsWith("#aspect/") || t.startsWith("#scene")) continue;
    const name = t.replace(/^#/, "");
    counts[name] = (counts[name] ?? 0) + 1;
  }
}
const rows = Object.entries(counts).sort((a,b) => b[1]-a[1] || a[0].localeCompare(b[0]));
dv.paragraph(rows.map(([t,c]) => `${t} (${c})`).join("  ·  "));
```

```dataviewjs
const TOPIC = "#" + dv.current().topic;
const MODE = dv.current().mode ?? "active";        // active = hide rejected; rejected = only rejected
const pages = dv.pages('"Sparks" or "Rejected"')   // include Rejected/ so killed sparks are found
  .where(p => p.file.tags.includes(TOPIC))
  .where(p => MODE === "rejected" ? p.file.tags.includes("#rejected")
                                  : !p.file.tags.includes("#rejected"));

const groups = {};
for (const p of pages) {
  const aspects = p.file.tags.filter(t => t.startsWith("#aspect/"));
  const keys = aspects.length ? aspects : ["#aspect/(unaspected)"];
  for (const k of keys) (groups[k] ??= []).push(p);
}

const order = Object.keys(groups).sort((a,b) => {
  if (a.includes("(unaspected)")) return 1;      // unaspected last
  if (b.includes("(unaspected)")) return -1;
  return a.localeCompare(b);
});

for (const key of order) {
  const list = groups[key];
  dv.header(2, key.replace("#aspect/","").replace(/^\w/, c=>c.toUpperCase()) + `  (${list.length})`);
  // one clickable line per spark: its one-line summary, plus a ⚠ flag if it conflicts with another spark
  const items = list.map(p => {
    let line = `[[${p.file.name}|${p.summary ?? p.file.name}]]`;
    if (p.conflicts) {
      const arr = Array.isArray(p.conflicts) ? p.conflicts : [p.conflicts];
      line += "  ⚠️ vs " + arr.map(n => `[[${n}]]`).join(", ");
    }
    return line;
  });
  dv.list(items);
}
```
