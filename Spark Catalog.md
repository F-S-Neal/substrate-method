---
topic: gary
mode: active
---

# Spark Catalog

**How to use:** in the Properties box above, set `topic` to a tag **without the #** (e.g. `gary`, `sabel`, `magicprinciples`) and `mode` to either `active` (hides `#rejected` sparks) or `rejected` (shows ONLY `#rejected` sparks). Then look at this note in Reading or Live Preview mode — the block below renders the full text of every matching spark. To look at a different topic, just change the `topic` property. You never edit the code.

Requires: Dataview installed, with **Settings → Dataview → Enable JavaScript Queries** turned ON.

```dataviewjs
const TAG = "#" + dv.current().topic;            // reads the `topic` property above
const MODE = dv.current().mode ?? "active";      // reads the `mode` property above
const pages = dv.pages(`"Sparks" or "Rejected"`) // both, so rejected sparks are found after auto-move
  .where(p => p.file.tags.includes(TAG))
  .where(p => MODE === "rejected" ? p.file.tags.includes("#rejected")
                                  : !p.file.tags.includes("#rejected"))
  .sort(p => p.created, 'asc');
dv.paragraph(`**${pages.length} ${MODE} sparks for ${TAG}**`);
for (const p of pages) {
  dv.header(4, p.file.name);
  dv.paragraph(await dv.io.load(p.file.path));
}
```
