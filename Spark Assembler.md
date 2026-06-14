---
topic:
mode: active
group: topic
order: asc
---

# Spark Assembler · Chrono ⇄ Topic

Pick a tag in **Topics**, then choose how to look at it:
- **Topic** view — the topic's sparks grouped by facet (appearance, mannerisms…), as one-line summaries.
- **Chrono** view — the flat stream, in the order you wrote them (oldest or newest first).

Click the **View** button to switch. Click a spark's **▸** to reveal its full text inline (the summary stays a link — click it to open the spark). **Expand all** opens everything at once. Leave `topic` blank to see every spark; click **unaspected** to find sparks that still need aspect tags.

Requires Dataview with **Enable JavaScript Queries** ON.

**Topics** (click one to load it):
```dataviewjs
const counts = {};
let unaspected = 0;
for (const p of dv.pages('"Sparks"')) {
  if (p.file.tags.includes("#rejected")) continue;
  const tags = p.file.tags ?? [];
  for (const t of tags) {
    if (t.startsWith("#aspect/") || t.startsWith("#scene")) continue;
    const name = t.replace(/^#/, "");
    counts[name] = (counts[name] ?? 0) + 1;
  }
  if (!tags.some(t => t.startsWith("#aspect/"))) unaspected++;
}
counts["unaspected"] = unaspected;
const rows = Object.entries(counts).sort((a, b) => a[0].localeCompare(b[0]));
const file = app.vault.getAbstractFileByPath(dv.current().file.path);
const box = dv.el("div", "");
box.style.lineHeight = "2";
rows.forEach(([t, c], i) => {
  const a = box.createEl("span", { text: `${t} (${c})` });
  a.style.cssText = "cursor:pointer; color:var(--link-color); text-decoration:underline;";
  a.onclick = async () => { await app.fileManager.processFrontMatter(file, fm => { fm.topic = t; }); };
  if (i < rows.length - 1) box.createSpan({ text: "  ·  " });
});
```

```dataviewjs
const file = app.vault.getAbstractFileByPath(dv.current().file.path);
const TOPIC = dv.current().topic;
const MODE = dv.current().mode ?? "active";
const CHRONO = (dv.current().group ?? "topic") === "chrono";   // anything not "chrono" = Topic view
const ORDER = dv.current().order ?? "asc";
const T = (TOPIC && String(TOPIC).trim()) ? String(TOPIC).trim() : null;
const live = p => MODE === "rejected" ? p.file.tags.includes("#rejected") : !p.file.tags.includes("#rejected");

let pages = dv.pages('"Sparks" or "Rejected"').where(live);
if (T === "unaspected") pages = pages.where(p => !p.file.tags.some(t => t.startsWith("#aspect/")));
else if (T) pages = pages.where(p => p.file.tags.includes("#" + T));

const bar = dv.el("div", "");
bar.style.cssText = "display:flex; gap:10px; align-items:center; flex-wrap:wrap; margin:6px 0 14px;";
const lab = bar.createSpan({ text: `${pages.length} ${MODE} spark${pages.length === 1 ? "" : "s"} · ${T ? T : "all topics"}` });
lab.style.fontWeight = "600";
const gBtn = bar.createEl("button", { text: CHRONO ? "View: Chrono ⇄" : "View: Topic ⇄" });
gBtn.onclick = async () => { await app.fileManager.processFrontMatter(file, fm => { fm.group = CHRONO ? "topic" : "chrono"; }); };
if (CHRONO) {
  const oBtn = bar.createEl("button", { text: ORDER === "asc" ? "↑ Oldest first" : "↓ Newest first" });
  oBtn.onclick = async () => { await app.fileManager.processFrontMatter(file, fm => { fm.order = ORDER === "asc" ? "desc" : "asc"; }); };
}
const xBtn = bar.createEl("button", { text: "Expand all" });

const ctl = [];
function renderSpark(parent, p) {
  const row = parent.createDiv();
  row.style.cssText = "display:flex; align-items:baseline; gap:8px; margin:3px 0;";
  const arrow = row.createSpan({ text: "▸" });
  arrow.style.cssText = "cursor:pointer; font-size:1.35em; line-height:1; color:var(--text-accent); user-select:none; flex:0 0 auto; width:1em; text-align:center;";
  const textWrap = row.createDiv();
  textWrap.style.cssText = "flex:1 1 auto; min-width:0;";
  textWrap.createEl("a", { text: p.summary ?? p.file.name, cls: "internal-link", attr: { "data-href": p.file.name, href: p.file.name } });
  if (p.conflicts) {
    const arr = Array.isArray(p.conflicts) ? p.conflicts : [p.conflicts];
    const cw = textWrap.createSpan();
    cw.style.color = "var(--text-error)";
    cw.appendText("  ⚠️ vs ");
    arr.forEach((n, i) => {
      const name = (n && n.path) ? n.path.replace(/\.md$/, "").split("/").pop()
                                 : String(n).replace(/^\[\[|\]\]$/g, "").split("|")[0].trim();
      const a = cw.createEl("a", { text: name, cls: "internal-link", attr: { "data-href": name, href: name } });
      a.style.color = "var(--text-error)";
      if (i < arr.length - 1) cw.appendText(", ");
    });
  }
  const body = parent.createDiv();
  body.style.cssText = "display:none; margin:2px 0 12px 2.1em; padding-left:10px; border-left:2px solid var(--background-modifier-border); white-space:pre-wrap;";
  let loaded = false;
  async function open() {
    if (!loaded) { const t = await dv.io.load(p.file.path); body.textContent = t.replace(/^---[\s\S]*?---\s*/, ""); loaded = true; }
    body.style.display = "block"; arrow.textContent = "▾";
  }
  function close() { body.style.display = "none"; arrow.textContent = "▸"; }
  arrow.onclick = () => { body.style.display === "none" ? open() : close(); };
  ctl.push({ open, close });
}

const container = dv.el("div", "");
if (CHRONO) {
  for (const p of pages.sort(x => x.created, ORDER)) renderSpark(container, p);
} else {
  const groups = {};
  for (const p of pages) {
    const aspects = p.file.tags.filter(t => t.startsWith("#aspect/"));
    const keys = aspects.length ? aspects : ["#aspect/(unaspected)"];
    for (const k of keys) (groups[k] ??= []).push(p);
  }
  const order = Object.keys(groups).sort((a, b) => a.includes("(unaspected)") ? 1 : b.includes("(unaspected)") ? -1 : a.localeCompare(b));
  for (const key of order) {
    container.createEl("h2", { text: key.replace("#aspect/", "").replace(/^\w/, c => c.toUpperCase()) + `  (${groups[key].length})` });
    for (const p of groups[key]) renderSpark(container, p);
  }
}

let allOpen = false;
xBtn.onclick = async () => {
  allOpen = !allOpen;
  for (const r of ctl) { if (allOpen) await r.open(); else r.close(); }
  xBtn.textContent = allOpen ? "Collapse all" : "Expand all";
};
```
