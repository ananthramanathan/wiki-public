# How to create an AI Chief of Staff
_Last updated: 2026-04-21_
_Visibility: public_

## TL;DR
Five distinct approaches exist for building an AI Chief of Staff, ranging from a simple context layer (30 min setup) to a fully autonomous multi-agent squad (weeks of build). The right choice is determined by one question: what is the primary problem you are solving? Context loss, daily automation, always-on capture, knowledge accumulation, or end-to-end execution each point to a different architecture. Most people should start with the context layer and add layers only when the previous one is working.

---

## The core problem all these systems solve

Every AI tool resets between sessions. You re-explain yourself, re-establish context, re-describe your priorities. The system has no memory of what you've decided, what you're working on, or how you think. The result: AI feels like a capable stranger you have to brief from scratch every time.

An AI Chief of Staff solves this by creating persistent context — a structured layer the AI reads before every interaction so it already knows who you are, what matters, and how to engage with you.

Beyond context, more advanced systems add: automation (things happen without you prompting), capture (inputs come from anywhere), knowledge accumulation (learning compounds), and execution (agents complete work end-to-end).

---

## Objective-to-approach mapping

Before choosing an architecture, identify your primary objective:

| Primary objective | Best starting approach |
|---|---|
| Stop re-explaining myself every session | Context layer only (Approach 1) |
| Get a daily brief without lifting a finger | Context layer + automation (Approach 2) |
| Capture thoughts on the go, always-on ambient assistant | Always-on agent with mobile interface (Approach 3) |
| Build a personal knowledge base that compounds | LLM wiki (Approach 4) |
| Delegate end-to-end work across multiple workflows | Multi-agent squad with self-improving tools (Approach 5) |

---

## Approach 1 — Context layer: stop re-explaining yourself

**The problem it solves:** Every session starts from zero. You spend the first 10 minutes re-establishing who you are and what you're working on.

**How it works:** A set of read-only markdown files (identity, thinking models, voice, working preferences) stored in a folder. An AI tool reads them at the start of every session. You never re-explain yourself.

**Core files:**
- `ABOUT_ME.md` — role, expertise, strategic lenses
- `THINKING_MODELS.md` — your actual decision filters, not aspirational frameworks
- `VOICE_CALIBRATION.md` — writing style defined by what's "off" as much as what's right
- `WORKING_PREFERENCES.md` — named operating modes you can invoke by name
- `GLOBAL_INSTRUCTIONS.md` — the behavioural contract (what the AI reads, writes, never deletes)

**Best for:** Solo knowledge workers, writers, operators who produce a lot of output and want AI that reasons through their frameworks rather than generic ones.

**Pros:** Low setup cost (one afternoon), no ongoing infrastructure, context compounds across sessions, bootstrappable from prior AI history.

**Cons:** Static — nothing is automated, nothing is proactive, no execution layer, single-user only.

**Setup time:** 1–3 hours. Tool required: Claude Code or Claude Projects.

---

## Approach 2 — Context layer + automation: the daily operating system

**The problem it solves:** You have the context layer but still have to manually prompt for everything. You want a brief waiting for you every morning without lifting a finger.

**How it works:** Adds scheduled Routines on top of the context layer. A morning routine reads your priorities file + calendar + email and delivers a focused brief. An evening routine asks what moved and updates the files. The priority file (`priorities.md`) is the operating spine — both routines read and write to it, creating a feedback loop between planning and execution.

**Additional components beyond Approach 1:**
- `priorities.md` — living P0/P1/Backlog file, the single source of truth
- Morning Routine — daily brief at a set time
- EOD Routine — daily closedown, processes the day's activity
- Weekly Routine — surfaces everything across domains, confirms the week's top priorities
- GitHub repo + Obsidian Git — so cloud-based Routines can access your files
- Live data connectors — Google Calendar, Gmail, Google Drive

**Best for:** Personal life operators whose digital life runs through Google Workspace. People who want automation without infrastructure complexity.

**Pros:** Zero-touch daily brief, live data integration, priorities feedback loop, tiered action triage (what Claude can do vs what needs you).

**Cons:** GitHub as middleware adds fragility. Routines dependency — if the feature changes, the system degrades. No outbound action (Claude surfaces but can't send). No collaboration model.

**Setup time:** 2–4 hours. Tools required: Claude Max subscription (Routines access), GitHub account, Obsidian.

---

## Approach 3 — Always-on agent with mobile interface: the ambient familiar

**The problem it solves:** You're not at a computer. You think of things on the go, in WhatsApp, in voice notes. You want an AI that's available wherever you are, proactively checks on things, and remembers everything without you having to open a dashboard.

**How it works:** An always-on agent (OpenClaw) running on a local machine or VPS, connected to WhatsApp as the primary interface. You text or voice-note it anytime. It files captures, answers questions, monitors inboxes, and — crucially — wakes up autonomously every 30 minutes (heartbeats) to check if anything needs attention. Memory is structured across markdown files with clear rules for what gets stored, indexed, and discarded.

**Memory file structure:**
- `SOUL.md` — personality, behavioural style, boundaries
- `USER.md` — stable facts about you
- `MEMORY.md` — long-term curated memory: decisions, rules, lessons
- `HEARTBEAT.md` — proactive wakeup rules: what to check, when to notify, when to stay silent
- `memory/YYYY-MM-DD.md` — daily scratchpad

**Best for:** People whose primary communication surface is mobile (WhatsApp-native). Those managing complex multi-context lives who cannot afford to sit at a computer to get a briefing. Those who want proactive, not just reactive, AI.

**Pros:** Truly always-on, zero-friction mobile capture, proactive heartbeat system, memory architecture is principled (clear rules on what gets stored), consistent identity across model switches, can participate in group chats.

**Cons:** Highest setup complexity of the personal-use systems (VPS, OpenClaw, WhatsApp plumbing). Local hardware dependency. Memory quality degrades if scratchpad maintenance lapses. No structured priority triage layer. Single-user.

**Setup time:** Several days to weeks. Tools required: OpenClaw, VPS (Hostinger ~$100/year), WhatsApp business number, multi-model API keys.

---

## Approach 4 — LLM wiki: the compounding knowledge base

**The problem it solves:** You accumulate knowledge across hundreds of chat windows, articles, and documents. You can't find it, can't build on it, and have to rediscover the same things repeatedly. Every AI query starts from scratch.

**How it works:** Raw source documents (articles, papers, notes) go into a `raw/` folder. An LLM *compiles* them into a structured wiki — it generates summaries, concept articles, and crucially, backlinks between related ideas. The wiki, not the raw sources, is what the LLM queries going forward. A linting pass periodically scans for inconsistencies and self-heals the wiki. Good Q&A answers are filed back as new wiki pages — the system gets smarter from use.

**Core structure:**
- `raw/` — immutable source documents
- `wiki/` — compiled, interlinked markdown articles (~100 articles, ~400K words at personal scale)
- `_index.md` — master topic map, auto-updated
- Commands: `/wiki [topic]` to write, `/wiki-ai` for append-only learnings log

**Best for:** Researchers, analysts, curious generalists who accumulate source material and want to query across it without rebuilding context. Also useful as the knowledge layer beneath any of the other approaches.

**Pros:** Knowledge compounds (not resets like RAG). No vector database required. Fully auditable — every claim traces to a readable file. Self-healing via linting. Human-readable at every layer.

**Cons:** Pure knowledge architecture — no action tracking, no execution, no people layer, no automation. Breaks at enterprise scale (hundreds+ of documents). LLM hallucination risk in the wiki itself (errors propagate). No proactive layer — entirely query-driven.

**Setup time:** 1–2 hours for structure, ongoing investment to populate. Tools required: GitHub, Claude Code or any coding agent, Obsidian (optional).

---

## Approach 5 — Multi-agent squad with self-improving skills: full execution

**The problem it solves:** You don't want an assistant that surfaces information — you want one that completes work end-to-end. Half-day projects should take 20 minutes. You have enough recurring workflows (financial analysis, CRM updates, content production, email triage) that building personalised tools for each one is worth the investment.

**How it works:** Multiple Claude Code Opus agents running simultaneously in terminal panes, each connected to the same environment of custom-built skill files. The distinctive idea: every skill has a self-improvement section — after each use, the agent edits its own skill file with what it learned. Skills rewrite themselves over time. The environment compounds without the operator writing any improvements. Tasks flow between human and agents via a shared task manager (@AGENT tags).

**Core components:**
- Multiple Claude Code instances in parallel (Zellij terminal panes)
- Custom skill files (32+ in a mature setup) — markdown instruction files built by Claude for specific workflows
- Self-improvement section in every skill — agents update skills after each use
- Shared Obsidian vault — collective memory across all agents
- Task manager (Todoist) as human-agent handoff surface
- Meeting capture (Granola) → auto-indexed into Obsidian

**Best for:** Technical founders, operators, or senior executives who are comfortable in a terminal and want to delegate complex, recurring work rather than just get briefed on it.

**Pros:** Agents complete work end-to-end. Self-improving skills compound without human effort. Multiple parallel workstreams. Personalised tools — not generic packages. Full visibility of every agent action.

**Cons:** Highest technical barrier (terminal required). Significant cost (multiple Opus instances). No mobile-native interface. Single-user. Skills require initial build investment. No proactive heartbeat layer — agents work when tasked, don't wake up autonomously.

**Setup time:** Days to weeks, ongoing. Tools required: Claude Max subscription, Claude Code, Zellij, Obsidian, Granola, Todoist, MCP servers.

---

## How to choose

**Start here:**

1. If you're not comfortable in a terminal → Approaches 1, 2, or 3 only
2. If you're primarily on mobile → Approach 3 (OpenClaw + WhatsApp)
3. If your life runs through Google → Approach 2 (Routines + Google connectors)
4. If you just want to stop re-explaining yourself → Approach 1 (context layer, one afternoon)
5. If you have lots of source material to make sense of → Approach 4 (LLM wiki)
6. If you want agents doing actual work, not just briefing → Approach 5

**The sequencing rule that holds across all of them:**

Context layer first. Automation second. Always-on third. The temptation is to build the full system immediately — that's why most of these never get finished. Each approach works on its own. Add layers only when the previous one is stable and actually in use.

**The one thing that kills all of them:**

Building the infrastructure before you've triaged what actually matters. A morning brief surfacing an untriaged task list is theatre, not useful. The system is only as good as the priorities it surfaces. Spend 20 minutes getting the priorities right before wiring up any automation.

---

## Key architectural principles that appear across all approaches

**Markdown as the universal format.** Every system uses plain .md files. Markdown is token-efficient, human-readable, version-controllable, portable across tools, and natively readable by any AI without API overhead.

**GitHub as the storage and sync layer.** Version history is free. Multiple tools (Claude Routines, Claude Code, Obsidian) can all read from and write to the same repo. The file IS the context — no transformation layer, no API bloat.

**Obsidian as the reading layer.** Not required, but present in almost every system. Renders markdown cleanly on desktop and mobile. Graph view shows connections between notes. The viewer is the only thing that changes when you upgrade — the files stay identical.

**Memory files over prompts.** Persistent markdown files that load at session start outperform repeated prompting every time. You write the context once; the system reads it forever.

**The environment compounds, not the model.** The model matters less than what you plug into it. The operators with the best systems didn't get there by finding the right model — they got there by building the right environment around whichever model they use.

---
_Sources: Five real implementations studied in detail, April 2026. Synthesised from direct conversations, published Substack posts, and WhatsApp architecture sessions._
