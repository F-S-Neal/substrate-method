<%*
// Fast capture. One prompt for the idea (also names the note); tags optional — /Tag Spark fills them.
const idea = (await tp.system.prompt("Spark — the idea (one per note):", "")) ?? "";
const tagsRaw = (await tp.system.prompt("Tags now? (comma-separated, or blank to add with /Tag Spark):", "")) ?? "";
const tags = tagsRaw.split(",").map(t => t.trim()).filter(Boolean).join(", ");
if (idea && tp.file.title.toLowerCase().startsWith("untitled")) {
  const fname = idea.slice(0, 80).replace(/[\\/:*?"<>|#^\[\]]+/g, "").trim();
  if (fname) await tp.file.rename(fname);
}
tR += "---\n";
tR += `created: ${tp.date.now("YYYY-MM-DD")}\n`;
tR += `tags: [${tags}]\n`;
tR += "---\n";
tR += idea ? idea + "\n" : "";
%>
