<%*
// Per-book loose-threads page. Synthesis (run on #<slug>-misc) reports into the body; the
// Dataview block below lists the raw source sparks.
const book = (await tp.system.prompt("Book this loose-threads page belongs to:", "")) ?? "";
const slugGuess = book.toLowerCase().replace(/[^a-z0-9]+/g, "");
const slug = ((await tp.system.prompt("Loose-tag slug (sparks tagged #<slug>-misc, e.g. book1):", slugGuess)) ?? slugGuess).trim();
const fname = book ? `Misc_${book} Loose Threads` : tp.file.title;
if (fname && fname !== tp.file.title) { await tp.file.rename(fname); }
tR += "---\n";
tR += `created: ${tp.date.now("YYYY-MM-DD")}\n`;
tR += `aliases: [${book} Loose Threads]\n`;
tR += `book: ${book}\n`;
tR += "type: loose-threads\n";
tR += "review: unreviewed\n";
tR += "---\n\n";
tR += "## Source sparks (this book's loose pile)\n";
tR += "```dataview\n";
tR += "LIST\n";
tR += "FROM \"Sparks\"\n";
tR += `WHERE contains(file.tags, "#${slug}-misc") AND !contains(file.tags, "#rejected")\n`;
tR += "SORT created ASC\n";
tR += "```\n";
%>
