<%*
// Name → type/aliases/topic. Name the note "Type_Name" (e.g. Character_Gary).
const raw = (await tp.system.prompt("Name this page  (Type_Name — e.g. Character_Gary):", "")) ?? "";
const title = (raw.trim() || tp.file.title);
if (title && title !== tp.file.title) { await tp.file.rename(title); }
const idx = title.indexOf("_");
let type = "", name = title;
if (idx > -1) { type = title.slice(0, idx).toLowerCase().trim(); name = title.slice(idx + 1).trim(); }
const topicGuess = name.toLowerCase().replace(/[^a-z0-9]+/g, "");

const series = (await tp.system.prompt("Series (blank to skip):", "")) ?? "";
const book   = (await tp.system.prompt("Book (blank to skip):", "")) ?? "";
const topic  = ((await tp.system.prompt("Topic — the spark tag this page is built from:", topicGuess)) ?? topicGuess).trim();

// Character-only fields — pickers, all skippable (pick "— skip —" or press Esc).
let charFields = "";
if (type === "character") {
  const pr = (await tp.system.suggester(["— skip —","Primary","Secondary","Tertiary"],
              ["","Primary","Secondary","Tertiary"], false, "Priority? (skip = leave blank)")) ?? "";
  const ro = (await tp.system.suggester(["— skip —","Protagonist","Antagonist","Contagonist","Guide","Sidekick","Love_Interest","Temptress"],
              ["","Protagonist","Antagonist","Contagonist","Guide","Sidekick","Love_Interest","Temptress"], false, "Role? (skip = leave blank)")) ?? "";
  const po = (await tp.system.suggester(["— skip —","Protector","Deflector","Believer","Doubter","Thinker","Feeler"],
              ["","Protector","Deflector","Believer","Doubter","Thinker","Feeler"], false, "Posture? (skip = leave blank)")) ?? "";
  charFields = `priority: ${pr}\nrole: ${ro}\nposture: ${po}\n`;
}

tR += "---\n";
tR += `created: ${tp.date.now("YYYY-MM-DD")}\n`;
tR += `aliases: [${name}]\n`;
tR += `series: ${series}\n`;
tR += `book: ${book}\n`;
tR += `type: ${type}\n`;
tR += `topic: ${topic}\n`;
tR += "review: unreviewed\n";
tR += charFields;
tR += "---\n";
%>
