# Personal Knowledge Wiki — System Overview
_Last updated: 2026-04-14_

---

## Objective

Build a personal knowledge remnant system that captures what has been learned across domains — structured for human recall, shareable on demand, and natively readable by AI CLI tools without token waste.

Not a second brain app. Not a CMS. A flat-file wiki on GitHub that serves three audiences:
1. Future-self recall — stop losing knowledge across chat windows and projects
2. AI tools (Claude Code, Codex) — load context at session start without burning tokens re-explaining basics
3. People who ask "how did you do that" — shareable on demand via a link

Personal branding is an emergent outcome, not a design goal.

---

## Outcomes this achieves

- Every useful chat session can be written to a permanent, structured wiki entry via a single command
- AI tools (Claude Code, Codex) can pull a topic file at session start as context — flat markdown, no API overhead
- Public topics are accessible via a URL anyone can read
- Private topics stay in a private repo — same structure, different visibility
- Version history is free — every edit is timestamped and reversible via git
- System is portable — content files never change, only the renderer does if you upgrade later

---

## Architecture built

### Two GitHub repos

| Repo | Visibility | URL |
|---|---|---|
| wiki-public | Public | github.com/ananthramanathan/wiki-public |
| wiki-private | Private | github.com/ananthramanathan/wiki-private |

### Folder structure

```
wiki-public/
  CLAUDE.md               ← operating instructions for Claude Code
  _config.yml             ← Jekyll theme config (GitHub Pages)
  _index.md               ← master topic map, auto-updated on new topic
  ai-learnings/
    index.md              ← append-only, /wiki-ai command
  how-i-did-x/
    index.md
  job-skills/
    index.md
    AI Agent Deployer.md  ← example subtopic file
  meta/
    index.md              ← this architecture document lives here

wiki-private/
  CLAUDE.md               ← operating instructions for Claude Code
  _index.md               ← private topic map
  health/
    index.md
    l4-l5-disc-bulge.md
    supplement-needs-review.md
  finance/
    index.md
  projects/
    index.md
  md-skills/
    index.md
    wiki-spec.md          ← canonical format spec for all AI tools
```

### Local folders

```
~/Documents/Wiki/
  public/    ← connected to wiki-public via SSH git remote
  private/   ← connected to wiki-private via SSH git remote
```

### Why GitHub, not Notion/Obsidian/GitBook

Token efficiency is structural. A flat .md file pulled at session start costs ~200-500 tokens. Any API-based tool costs 3-5x that with metadata noise. Git is the only option where the file IS the context — no transformation layer, no API, no bloat.

---

## E2E flow instructions

### One-time setup (complete)

1. Created two repos on github.com — wiki-public (public) and wiki-private (private)
2. Created local folders at ~/Documents/Wiki/public and ~/Documents/Wiki/private
3. Connected each folder to its repo via SSH:
```bash
git remote add origin git@github.com:ananthramanathan/wiki-public.git
git pull origin main
```
4. Dropped all starter files (CLAUDE.md, _index.md, topic stubs) into each folder
5. Committed and pushed both repos
6. Enabled GitHub Pages on wiki-public — Settings → Pages → Deploy from branch → main

### Writing to the wiki (ongoing)

**From Claude Code CLI:**
```bash
cd ~/Documents/Wiki/public   # or private
claude
```
Then issue a command. Claude Code reads CLAUDE.md and handles everything.

**Commands:**
- `/wiki [topic] — [summary]` — writes to a topic file, updates TL;DR, updates _index.md, commits, pushes
- `/wiki-ai — [what I learnt today]` — appends dated entry to ai-learnings/index.md only

**From a source document:**
```
Read CLAUDE.md in this repo.
I have a source document to convert into a wiki entry under [folder]/.
Topic: [topic-name]
Overwrite any existing file for this topic completely.
Recreate the document completely and faithfully — nothing omitted.
[attach document]
```
Claude Code handles: file creation, index update, commit, push.

### Pushing manually if needed
```bash
cd ~/Documents/Wiki/public   # or private
git add .
git commit -m "wiki: update [topic-name]"
git push origin main
```

### Reading from the wiki (AI context loading)

At the start of any Claude Code or Codex session where topic context is needed:
```
Read ~/Documents/Wiki/private/health/l4-l5-disc-bulge.md and use it as context.
```
Or reference the TL;DR only for lightweight context:
```
Read only the TL;DR section of ~/Documents/Wiki/private/health/l4-l5-disc-bulge.md
```

---

## File format spec

Every topic file follows this structure exactly:

```markdown
---
layout: default
title: [Topic Name]
---

# [Topic name]
_Last updated: YYYY-MM-DD_
_Visibility: public | private_

## TL;DR
One paragraph summary. Updated on every write. Never skip this.

## [Section]
Content.

---
_Sources: [chat link, URL, or "direct experience"]_
```

The TL;DR is the only summary in the file. Everything below it is the full record — nothing omitted.

---

## Lessons learnt

### What works

- **Two-repo structure** — clean separation of public and private. No hacks, no per-file visibility toggles. Simple.
- **SSH over HTTPS for GitHub** — HTTPS caused authentication conflicts with multiple GitHub accounts on the same machine. SSH uses the key, always resolves to the right account. Use SSH for all remotes.
- **CLAUDE.md as the operating doc** — Claude Code reads it at session start and follows it. All rules, format spec, and commands live there. You don't re-explain anything.
- **Flat file per topic** — one index.md per topic folder. AI tools pull it once, get everything. No directory traversal, no multi-file assembly.
- **TL;DR at top** — lightweight context load for AI tools without reading the full file. Pays off as files grow.
- **Git as the write infrastructure** — pull → edit → push is all that's needed. Works identically from Claude Code, Codex, or manual terminal.

### What doesn't work / known issues

- **Jekyll theming is unresolved** — adding front matter (layout: default) to .md files broke rendering instead of improving it. GitHub Pages Jekyll setup needs a fresh dedicated session to diagnose properly. Do not attempt mid-session.
- **Chat Claude will summarise source documents unless explicitly told not to** — this is a known failure mode. Always use Claude Code CLI to convert source documents to wiki entries, never chat Claude. The CLAUDE.md hard rule covers this for CLI.
- **HTTPS remotes fail with multiple GitHub accounts** — if you have more than one GitHub account authenticated on your machine, HTTPS pushes will attempt the wrong account. Always set remotes via SSH: `git remote set-url origin git@github.com:username/repo.git`
- **_index.md must be updated on every new topic** — currently a manual check in the command flow. Claude Code handles it if instructed, but it is not yet a fully enforced automated step.
- **No search on GitHub Pages** — shareable as a direct link, not as an explorable wiki. A stranger landing on the homepage cannot search. Acceptable for current use case (share a specific link). Will require Docusaurus or Algolia when personal branding becomes a goal.
- **Private/public boundary is static** — visibility is set at topic creation. No defined migration path if a private topic becomes shareable later. Manual move between repos works but any hardcoded repo paths in AI config would break silently.

### What to fix next session

1. Diagnose and resolve Jekyll theming — screenshot Pages settings at session start
2. Update CLAUDE.md in both repos via Claude Code to add Jekyll front matter rule to every new file
3. Run the first proper CLI test — source documents → Claude Code → wiki entries → commit → push
4. Decide on cold start plan — how to backfill ~50 existing useful chat windows

---
_Sources: Product co-founder session, April 2026._
