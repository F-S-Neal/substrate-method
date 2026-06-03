<%*
// Scene cheat-sheet landing note. Paste the Copilot Scene Report output below the header.
const raw = (await tp.system.prompt("Scene title (e.g. The Auction):", "")) ?? "";
const title = (raw.trim() || tp.file.title);
if (title && title !== tp.file.title) { await tp.file.rename(title); }
tR += "---\n";
tR += `created: ${tp.date.now("YYYY-MM-DD")}\n`;
tR += "type: scene-report\n";
tR += "---\n";
tR += `# ${title}\n`;
%>
