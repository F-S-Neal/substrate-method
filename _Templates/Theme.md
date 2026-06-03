<%*
// Theme / motif page. Frontmatter + the theme tag are prompted; the Dataview block is wired
// to your tag automatically. The "How this motif plays out" section you write by hand.
const raw = (await tp.system.prompt("Theme name (e.g. Redemption):", "")) ?? "";
const themeName = (raw.trim() || tp.file.title);
if (themeName && themeName !== tp.file.title) { await tp.file.rename(themeName); }
const tagGuess = themeName.toLowerCase().replace(/[^a-z0-9]+/g, "");
const tag = ((await tp.system.prompt("Theme tag slug (used as #theme/<slug>):", tagGuess)) ?? tagGuess).trim();
const book = (await tp.system.prompt("Book / series this theme belongs to:", "")) ?? "";
tR += "---\n";
tR += `created: ${tp.date.now("YYYY-MM-DD")}\n`;
tR += "type: theme\n";
tR += `book: ${book}\n`;
tR += "---\n\n";
tR += `# ${themeName} — Theme\n\n`;
tR += "## How this motif plays out\n\n";
tR += "## Sparks that embody it\n";
tR += "```dataview\n";
tR += "LIST\n";
tR += "FROM \"Sparks\"\n";
tR += `WHERE contains(file.tags, "#theme/${tag}") AND !contains(file.tags, "#rejected")\n`;
tR += "SORT created ASC\n";
tR += "```\n\n";
tR += "## Connections\n";
%>
