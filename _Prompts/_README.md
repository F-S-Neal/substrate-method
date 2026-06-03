# _Prompts (shipped copies — staging only)

These are the Copilot prompts that ship with the starter. **Copilot doesn't load them from here.**
During setup (INSTALL §3) you **copy** them into Copilot's own folder — by default
`copilot-custom-prompts/` at the vault root — and reload Copilot. You can delete this `_Prompts/`
folder once you've copied them. (Don't re-point Copilot's custom-prompts setting at `_Prompts/`, or
you'll hide Copilot's built-in commands.)

The five prompts, run from the `/` menu in the Copilot chat:
- **Synthesis Prompt** — build a canonical draft for a topic (edit the topic + the {#TAG} line).
- **Tag Spark** — with a spark open, add its entity tags, aspect tags, and a one-line summary.
- **Scene Report Prompt** — a one-page scene cheat sheet from your canonical pages.
- **Smoke Test Prompt** — pre-filled for the shipped Gary demo; run as-is to verify the gather.
- **Theme Discovery Prompt** — propose recurring motifs across a scope of sparks.

(The OCR, Import, and Big-Topic prompts live in `_External AI Prompts/` — those run in Claude
Code / Cowork, not in Copilot.)

Keep ONLY prompt files in Copilot's folder — it turns every note there into a command.
