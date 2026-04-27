# Wiki-public — Claude operating instructions

## What this repo is
This is a personal knowledge wiki. Each folder is a topic.
Each topic has one file: index.md. Never create multiple files per topic.

## Your job
When the user issues a /wiki command:
1. git pull origin main
2. Check if the topic folder exists — create it if not
3. If new topic — add it to _index.md
4. Append new content to the correct topic/index.md
5. Update the TL;DR section of that file to reflect new content
6. git add . → git commit -m "wiki: update [topic]" → git push origin main

## File format — every index.md must follow this exactly

# [Topic name]
_Last updated: YYYY-MM-DD_
_Visibility: public_

## TL;DR
One paragraph summary. Updated on every write. Never skip this.

## [Section]
Content.

---
_Sources: [chat link or "direct experience"]_

## Commands

### /wiki [topic] — [summary]
Write to wiki-public. Format content, append to the right section,
update TL;DR, commit and push.

### /wiki-ai — [what I learnt]
Append a dated entry to ai-learnings/index.md only.
Do not restructure. Do not update TL;DR on this file.
Append with today's date as a heading in this format:

### YYYY-MM-DD
[content]

## Hard rules
- One index.md per topic folder. Never more.
- Always update TL;DR on every write except /wiki-ai
- Always update _index.md when creating a new topic
- Always git pull before writing anything
- Commit message format: "wiki: update [topic-name]"
- Never delete existing content — only append or update TL;DR

### Exception for system-architectures topics
Topics under `system-architectures/` may contain a `captures/` subfolder alongside `index.md`. Captures are raw single-source preservations; `index.md` is the synthesised roadmap. This is the only place multiple files per topic folder are allowed.

## CRITICAL: Handling source documents
When a source document (docx, pdf, notes, chat export, or any format)
is provided as the basis for a wiki entry:

- Recreate the content COMPLETELY and FAITHFULLY in markdown format
- Every section, data point, timeline entry, table row, and detail
  must be preserved — nothing omitted, nothing compressed
- Do NOT summarise, condense, or make judgment calls about what is
  important enough to include
- The TL;DR at the top is the only summary — everything below it
  is the full record
- This rule is absolute — applies to all content types including
  medical records, research notes, financial data, and project logs
- When in doubt: include it. Omitting content from a source document
  is never acceptable without explicit instruction from the user
