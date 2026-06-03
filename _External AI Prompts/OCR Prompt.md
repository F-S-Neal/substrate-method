# OCR prompt — run in Claude (chat for a few pages, Cowork for bulk)

Photograph your handwritten pages. For a few pages, attach them in the Claude chat
app. For many, use Claude Cowork pointed at a folder of photos and ask it to write
one Markdown file per page into an output folder. Paste this as the instruction:

---

You are an OCR engine. Transcribe the handwriting in this image EXACTLY as
written. Preserve line breaks. Mark any word you cannot read with [?]. Do not
paraphrase, correct, or interpret — transcribe. Output plain text only.

---

Proofread the result — this is the one unavoidable manual step. Then put the
transcripts in the same working folder as your other raw notes, ready for Atomize.
