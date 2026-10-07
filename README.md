# PDF to Profile note

An AI skill that turns a long PDF about you (a personality report, assessment results, a career report) or a study guide into a short, page-cited note in your Obsidian Profile, merged with what the Profile already says.

It works with any capable AI model. The skill is a plain Markdown prompt (`SKILL.md`) in the open Agent Skills format, so nothing in it is tied to one vendor.

## What it does

It keeps scores, type codes, percentiles and named traits exactly as the report states them and cites every claim to a page, as `(p. 4)`. Its own reading of the results goes in a separate section labelled as synthesis, and a caveats section says what kind of evidence the document is (a self-report, one author's view). When a new report contradicts a note you already have, it lists the conflict and does not overwrite anything.

## How it works

| Step | What happens |
|---|---|
| 1. Read | Reads the whole PDF, tables and appendices included. Records the document type, issuer, date, framework (Big Five, MBTI, CliftonStrengths, Hogan) and every score. Says so if it had to OCR scanned pages. |
| 2. Check the Profile | Finds your `Profile/` folder and its index, reads related notes, and copies their naming and frontmatter. |
| 3. Write | Summary, results table, a condensed version of the report, practical implications, labelled synthesis, caveats. A study guide gets "Key concepts" and "How to use this" in place of results and implications. |
| 4. Merge | Saves the note, adds it to the Profile index, and proposes line edits to summary notes such as "Strengths" or "How I work". It applies those edits only after you agree. |
| 5. Report | Three lines: where the note went, the headline findings, and any conflicts or edits waiting on you. |

## Requirements

| Need | Why |
|---|---|
| An AI model that can read PDFs, including scanned pages | The PDF is the only input |
| Read and write access to your notes folder, if you want it filed for you | Steps 2 and 4 read the Profile and save the note |
| Obsidian, optional | The note uses `[[wikilinks]]` and YAML frontmatter |

No code, no API keys and no packages to install. The skill tells the model to keep personal data inside the vault, but where your PDF goes depends on the model you use, so pick one whose data terms you are happy with.

## Install

| Where you run it | How |
|---|---|
| An agent that reads skills folders (Claude Code, OpenAI Codex, Gemini CLI, GitHub Copilot, Cursor and the others listed at [agentskills.io](https://agentskills.io)) | Clone this repo into the agent's skills folder as `pdf-to-profile-note`, for example `git clone https://github.com/Vidwaansinghania/PDF-to-Profile-Note.git ~/.claude/skills/pdf-to-profile-note`. Each agent documents its own folder. |
| A chat assistant without skills (ChatGPT, Gemini, Claude.ai, a local model) | Paste everything in `SKILL.md` below the `---` header into custom instructions, a project, a Gem, or the first message, attach the PDF, and save the note it writes. |

## Using it

```
Add this Hogan report to my Profile.
```

## Licence

MIT. See [LICENSE](LICENSE).
