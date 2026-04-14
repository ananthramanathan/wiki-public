# Wiki system — architecture & design decisions
_Last updated: 2026-04-14_
_Visibility: public_

## TL;DR

A flat-file personal knowledge wiki on GitHub. Two repos (`wiki-public`, `wiki-private`), one markdown file per topic, written to via a `/wiki` command from any chat or CLI session. Optimised for AI read/write efficiency over visual polish. GitHub Pages for public sharing now; portable to any renderer later. This document captures the full architecture rationale and known limitations so future decisions have context.

---

## Objective

Build a personal knowledge remnant system that captures what has been learned across domains — structured for human recall, shareable on demand, and natively readable by AI CLI tools without token waste.

Not a second brain app. Not a CMS. A flat-file wiki on GitHub that serves three audiences:
1. Future-self recall
2. AI tools (Claude Code, Codex) loading context at session start
3. People who ask "how did you do that" — shareable on demand

Personal branding is an emergent outcome, not a design goal.

---

## Architecture

### Two-repo structure

| Repo | Visibility | Purpose |
|------|-----------|---------|
| `wiki-public` | Public | Shareable topics. GitHub Pages enabled. |
| `wiki-private` | Private | Personal context never shared. AI context/skill files. |

Same folder convention in both. Visibility is decided at topic creation — not retroactively.

### Folder structure

```
wiki-public/
  ai-learnings/
    index.md          ← append-only, command-triggered
  job-skills/
    index.md
  how-i-did-x/
    claude-projects.md
    pickleball-club.md
  _index.md           ← master topic map, auto-updated on new topic

wiki-private/
  health/
    index.md          ← private (personal health data)
  finance/
    index.md
  relationships/
    index.md
  projects/
    index.md
  md-skills/
    wiki-spec.md      ← single source of truth for AI tool format spec
    *.md              ← other AI context/protocol files
  _index.md           ← private topic map
```

### Why GitHub, not Notion/Obsidian/GitBook

| Requirement | GitHub verdict |
|-------------|---------------|
| AI read/write (Claude Code, Codex) | Native — git pull/append/push, no API layer |
| Token efficiency | A flat .md file is the context. No transformation overhead. |
| CLI access | First-class |
| Version history | Free, every commit timestamped |
| Public sharing | GitHub Pages, zero config |
| Future portability | Change the renderer, keep the files |

The decisive factor: token efficiency is structural, not behavioural. A flat markdown file pulled at session start costs ~200–500 tokens. Any API-based tool (Notion, etc.) costs 3–5x with metadata noise.

---

## File format spec

Every topic file, in both repos, follows this structure:

```markdown
# [Topic name]
_Last updated: YYYY-MM-DD_
_Visibility: public | private_

## TL;DR
One paragraph. Summarises everything below.
Updated on every write — mandatory, not optional.

## [Section heading]
Content.

## [Section heading]
Content.

---
_Sources: [chat link, URL, or "direct experience"]_
```

### Why TL;DR is load-bearing

AI tools reading for context load the TL;DR only (~50–100 tokens). Full file only when doing deep work on that topic. If the TL;DR rots, AI tools get misleading context. TL;DR update is mandatory on every `/wiki` write — enforced by the command protocol, not by discipline.

---

## Command protocol

Two commands. Identical syntax across Claude chat, Claude Code, and Codex.

### `/wiki [topic] — [summary of what to capture]`

Executes:
1. `git pull` on the relevant repo
2. Check if topic exists — create `topic/index.md` from template if not
3. If new topic: add entry to `_index.md` (mandatory)
4. Append formatted entry to the correct section
5. Update TL;DR to reflect new content
6. `git commit -m "wiki: update [topic]"` + `git push`

### `/wiki-ai — [what I learnt today]`

Appends a dated entry to `ai-learnings/index.md`. Append-only. AI tools never reorganise this file — manual quarterly consolidation only.

### AI tool configuration

- **Claude Code**: format spec lives in `CLAUDE.md` project file, references `wiki-private/md-skills/wiki-spec.md`
- **Codex**: same spec referenced in `codex.md` or system prompt
- Single source of truth: `wiki-spec.md`. Both tools point to it.

---

## Design decisions log

### Health pages are private
Health data is personal. Even "how I think about health" is context I may not want permanently public. Lives in `wiki-private/health/`.

### `_index.md` auto-updated on every new topic
Initially considered as a manual step. Rejected — manual index maintenance breaks at scale. Every `/wiki [new-topic]` command checks and updates `_index.md` automatically. Zero extra effort from the user.

### AI context files (md-skills) are separate from wiki content
Skill/protocol files for AI tools are not wiki pages — they're operational config. They live in `wiki-private/md-skills/` and are invoked differently (loaded at session start, not appended to). Conflating them with wiki content would pollute the topic structure.

### Append vs restructure for topic files
`ai-learnings` is append-only by design — chronological record of what was learnt, when.
All other topic files are living documents — append new content, but restructure quarterly to resolve contradictions and consolidate. Pure append on belief-heavy topics (health, finance) creates conflicting context over time.

---

## Known limitations (accepted, not fixed)

These are documented so future decisions have context. They are not bugs — they are known tradeoffs at current scale.

### 1. Cold start — existing knowledge not captured
The write path covers future sessions. ~50 existing useful chat windows are not automatically ingested. A one-time retroactive extraction sprint is needed — not a perfect archive, just a first-pass per topic. This was a deliberate deferral: building the system first, backfilling second.

### 2. TL;DR rot risk
If the TL;DR update step is skipped (human error, tool failure), the summary goes stale and AI tools get misleading context. Mitigated by making TL;DR update mandatory in the command protocol — but not technically enforced. Accepted risk at this scale.

### 3. Append creates contradiction over time
For topics where beliefs update (health, finance), appending without restructuring creates files where old and new positions coexist. AI tools reading the full file may surface outdated context. Mitigation: quarterly manual consolidation. Known limitation of the flat-file model.

### 4. Static public/private boundary
Visibility is set at topic creation. No defined migration path if a private topic becomes shareable later. Manual move between repos works, but any AI tool config referencing hardcoded repo paths would break silently. Accepted for now — at small topic count, manual migration is fine.

### 5. Git merge conflicts
If an AI tool and a manual edit write to the same file on the same day, a merge conflict is possible. Convention: AI tools always `git pull` before write. Avoid manual edits to a file the same day a `/wiki` command has been issued against it. Low probability, acceptable risk.

### 6. No search on GitHub Pages
GitHub Pages renders markdown cleanly but has no search. Shareable as "here is the exact link" works. "Go explore my wiki" does not — there is no discovery layer. This is a known hard wall for the personal branding use case (#4 in priority), not a soft limitation. Docusaurus or Algolia DocSearch would solve it when that use case becomes relevant.

---

## Future upgrade path

When the personal branding use case (#4) becomes relevant:
- Drop in Docusaurus as the renderer — files stay identical
- Add Algolia DocSearch for full-text search
- Add a custom domain
- No content migration required

The architecture was chosen specifically so the renderer is the only thing that changes.

---
_Sources: Product co-founder session, April 2026. Architecture designed for token efficiency, AI-native write paths, and portability._
