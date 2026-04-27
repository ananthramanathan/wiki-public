# Capture: Barona Marcoms OS — Marketing Operating System (Vahaaho-Pesola)
_Captured: 2026-04-27_
_Source: LinkedIn post by Henri Vahaaho-Pesola (CMO, Barona), ~April 2026. Confirm author at filing._
_Topic: ai-gtm-playbook → marketing_

## Pattern note
This is a **marketing operating system** capture, not a worker-agent capture. It describes a structured context + skills + MCP infrastructure that the marketing team queries via Claude Desktop — closer in shape to a personal knowledge wiki than to Artisan/Qualified-style worker agents.

When the second OS-pattern capture lands (and they will — Kieran Flanagan's four-layer model is becoming a canonical pattern), this file should be promoted out of `marketing/captures/` into a dedicated `marketing-os/` or `gtm-os/` surface alongside it. For now it lives here with this note as the routing signal.

Worker-agent marketing captures (Jasper, Writer, Copy.ai, etc.) belong in `marketing/captures/` as originally scoped. This file is the exception, not the precedent.

## What this is
A solo-built marketing operating system at Barona (Finnish staffing company), built by the CMO over a few weeks of evenings. Branded internally as "Barona Marcoms Operating System" or "the brain." A centralised GitHub + Claude Code system of markdown files, skills, tools, and MCPs that any team member connects to via Claude Desktop. Built by a non-coding CMO with a few weeks of Claude Code learning and Opus tokens.

## How it works

### The four-layer architecture (adapted from Kieran Flanagan)

**Layer 1 — Foundation (the context layer)**
- Who Barona is
- Brand
- Services
- ICPs
- Markets
- Positioning
- Team
- Stakeholders
- Budgets

All in markdown, all loadable on demand. Status at time of capture: "somewhat done."

**Layer 2 — Research & Reach (real-time intel)**
- Real-time market & audience intel via MCPs
- Deal & customer context via MCPs
- Loaded into the system only when tasks need it (deliberate gating — load too much, clog the context; load too little, output goes generic)

Status at capture: scoped but not built.

**Layer 3 — Execution (the skills layer)**
- Campaign briefs
- Blog content
- LinkedIn posts
- Case studies
- PPT decks
- Press releases

Each skill reads the Foundation layer, matches Barona's voice, produces in their format.

Status at capture: partway in. Visible folder structure (from screenshot):
```
skills/
  brand-guidelines/      # Enforce voice & visual standards
  campaign-brief/        # B2B campaign planner
  content-writer/        # LinkedIn, blogs, emails, ads
  thought-leadership-writer/  # Long-form articles in voice
  ppt-maker/             # Branded presentations
  reference-writer/      # Customer case studies
  press-release-writer/  # Media releases
```

**Layer 4 — Feedback & iteration (the compounding layer)**
- Every output feeds back what worked
- Next month's content gets sharper than this month's

Status at capture: "still pretty far." Not built.

### The folder structure (verbatim from screenshot)
```
barona-marcoms-os/
├── README.md          # Version history, overview, structure
├── CLAUDE.md          # System orchestration rules
├── knowledge/         # LAYER 1: FOUNDATION
│   ├── brand/         # Voice, visual identity, architecture
│   ├── services/      # Service portfolio & positioning
│   ├── organization/  # Team, strategy, stakeholders
│   ├── markets/       # Business units, audiences, GTM
│   └── content-library/  # Indexed articles & case studies
├── skills/            # LAYER 3: EXECUTION
│   ├── brand-guidelines/
│   ├── campaign-brief/
│   ├── content-writer/
│   ├── thought-leadership-writer/
│   ├── ppt-maker/
│   ├── reference-writer/
│   └── press-release-writer/
├── templates/         # Design assets
│   ├── ppt-template-2026.pptx
│   └── (other brand templates)
├── mcp-server/        # INFRASTRUCTURE
│   ├── server.py      # FastMCP server (Python)
│   └── README.md      # Setup guide
├── output/            # Generated deliverables
└── setup/             # Onboarding for new team members
```

### How the team uses it
- Connect via Claude Desktop
- Foundation context loads on demand, not always — controlled via the MCP layer
- Skills produce drafts in Barona's voice and format
- Output target: 70% of the way there. Expert marketers take it from there.
- The CMO's framing: "70% there is *a lot* easier for the expert marketer to start from"

### What's queryable today
- Tone of voice
- Brand architecture
- Service positioning
- Draft campaign brief in a couple of minutes
- Draft content piece in actual Barona voice in a couple of minutes

## What's distinctive

1. **The four-layer model is the spine, not the implementation.** Vahaaho-Pesola explicitly credits Kieran Flanagan for the Foundation / Research / Execution / Feedback framing. The implementation choices (GitHub + Claude Code + Claude Desktop + MCP) are downstream of the architecture, which is the load-bearing intellectual move.

2. **The Foundation layer as the moat, not the AI.** "The moat isn't the AI — it's the structured business context that feeds it." This is the operator-relevant claim — switching costs accumulate in the curated context (brand voice, services, ICPs, positioning), not in the tooling. The AI is interchangeable; the structured Foundation isn't.

3. **Solo-build by a non-technical CMO.** No engineering team, no consultants, no vendors. CMO + existing business documentation + a few weeks of Claude Code learning. This is the v1 capture's "weekend build" claim extended to "weeks of evenings build" at department scale.

4. **Layer 4 (feedback) is the unbuilt magic.** Vahaaho-Pesola explicitly flags this as the part that makes the system compound. The first three layers produce drafts; Layer 4 is what makes next month's drafts better than this month's. Currently theoretical, not implemented. This is the gap most "marketing OS" implementations will likely have.

5. **Layer 2's "load on demand" gating is a thoughtful architecture choice.** Most context-loading systems either dump everything (clogging context) or pull narrowly (generic output). The deliberate gating — load real-time intel only when the task needs it — is a non-obvious design decision that comes from actually having built the thing.

6. **The "70% there" framing reframes the value proposition.** Not "AI replaces the marketer." Not "AI does the work." It's "AI gets the marketer to 70% so they can start from a good draft." This positions the system as scaffolding, not replacement — which is both more honest and more deployable inside a marketing team that doesn't want to be replaced.

7. **Different shape from worker agents.** Artisan, Qualified, Agentforce, Deli are all *agents that do a job*. Barona's OS is *infrastructure that the team queries*. The team is in the loop on every output. It's a tool, not a worker. This distinction is the routing signal that justified the surface routing decision.

## The author's stated purpose
Vahaaho-Pesola is making a public claim that within 12 months, marketing OS systems like this will be table stakes for any competitive marketing team. The post is part build-in-public, part marketing-leader-positioning. The deeper purpose is naming a pattern (the Kieran four-layer applied to a marketing department) and demonstrating that it's buildable solo by a non-coding CMO — which lowers the barrier-to-entry argument for other CMOs considering similar projects.

Why this purpose matters for an operator: if you're a CCO/COO upskilling for an AI-first GTM org, this is a proof point that department-level OS systems are buildable today, by the operator themselves, without engineering investment. The hot take ("table stakes within 12 months") is the prediction worth either betting on or against.

## Pros / cons as the source presents them

### Pros (claimed)
- Buildable solo by a non-coding CMO
- Output is "70% there" — meaningfully accelerates expert marketers
- Foundation layer is queryable: tone, brand architecture, services
- Compounds with use (in theory — Layer 4 not yet built)
- Token-efficient — Foundation loads on demand, not always
- Cost: "a few weeks of on-and-off Claude Code learning and Opus tokens"
- Scales across the team via Claude Desktop

### Cons (admitted/implied)
- Layer 2 (real-time intel) scoped but not built
- Layer 4 (feedback) "still pretty far" — the compounding magic isn't real yet
- Output is 70%, not 100% — still requires expert marketer to finish
- Implicit cons not addressed: maintenance cost as Foundation grows stale, governance question (who edits the brand markdown when positioning changes), team adoption curve (will marketers actually query it daily)
- The "moat is the structured context" claim assumes the context stays current; nothing in the post addresses how

The source is uncritical. Real cons an operator should append:
- Foundation rot: brand documents written today are stale in 12 months unless someone owns updating them
- Skill drift: the "voice" embedded in skills today won't match the brand's evolved voice in 12 months
- Tool lock-in: built on Claude Desktop + Claude Code. If Anthropic pricing changes 5x or the desktop product sunsets, the system needs porting
- Single-author risk: if Vahaaho-Pesola leaves Barona, who maintains it?

## Cross-cutting principles that apply to this surface

### Single source of truth (adapted)
Not Salesforce — GitHub. The repo is the SoT for brand, services, positioning, voice. Same architectural principle as the SaaStr stack, different implementation.

### "Pretty good at scale"
The 70%-there framing is the same principle. Not "AI writes perfect blog posts." It's "AI writes pretty-good drafts of every blog post we need, every time, in our voice, in our format."

### Daily training (sort of)
Layer 4 is the daily-training-equivalent for an OS-pattern system. Without it, the system is static. With it, it compounds. The Barona implementation acknowledges Layer 4 is the missing piece.

### Forward Deployed Engineers — *inverted*
SaaStr's lesson: pick vendors with strong FDEs. Barona's pattern: be your own FDE. The CMO became the engineer. This works for solo-builder CMOs; doesn't work for CMOs who can't or won't learn Claude Code.

### Tell agents what they CAN'T do
Implicit in the brand-guidelines skill — voice and visual standards are constraints, not just affordances. The "what we can't do" discipline is preserved at the skill level rather than the agent level.

## Operator-relevant signal

- **The "moat is the context, not the AI" claim is the operator-relevant takeaway.** If you're a CCO/COO planning AI-first GTM, the highest-leverage investment isn't picking the right AI vendor — it's curating the structured business context that any AI vendor can query. This argues for building the Foundation layer first, regardless of which agents/orchestrators get built on top.

- **The four-layer model gives operators a planning framework.** Foundation → Research → Execution → Feedback isn't just architecture, it's a sequencing rule. Foundation first (because everything else depends on it), Execution second (because it's the visible value), Research third (because it adds real-time signal once the static context is in place), Feedback last (because it requires the previous three to even have something to feed back on).

- **Solo-build by a non-coding CMO is the proof point.** This is the pattern operators should expect to replicate. If your CMO can't or won't learn Claude Code, the AI-first marketing transition has a different shape (delegate to a builder, hire one in, or partner with a vendor). If they can, this becomes a tractable solo project.

- **The "70% there" framing is the politically deployable framing inside a marketing team.** "AI gets you to 70%, you bring it home" doesn't threaten marketers. "AI replaces marketers" does. Operators rolling this out internally should adopt the 70% framing, even if the long-term trajectory is higher.

- **GitHub + Claude Desktop + MCP is the canonical stack.** Same pattern as your own wiki. Same pattern likely emerging across other operator-built systems. The stack itself is becoming a recognisable pattern — operators not familiar with it should learn it directly rather than waiting for a vendor to package it.

- **The 12-month "table stakes" prediction is worth tracking.** If true, marketing teams without an OS in mid-2027 are at a competitive disadvantage. If false, the claim was hype. Either way, an operator should make a deliberate bet on this prediction within the next 6 months — building the OS, dismissing the pattern, or planning to adopt later. Hedged inaction is the worst option.

- **Department-level OS pattern likely generalises.** If marketing OS works, sales OS, RevOps OS, product OS likely follow. The operator implication: this isn't a marketing-specific pattern; it's a department-level pattern that marketing happens to be early on. Operators should expect to build (or evaluate) similar systems for every department they own.

## Open questions

- How does Layer 4 actually work when built? "Every output feeds back what worked" is easy to say; the implementation question is what's the feedback signal (engagement metrics? human edits? content performance?), how is it captured, how does it modify the skills?
- How is Foundation kept current? When Barona's brand evolves, who updates the markdown? On what cadence? With what review process?
- Does the 70% claim hold for all skills equally? Press release vs. LinkedIn post vs. PPT deck likely have different ceilings. Source treats them uniformly.
- Adoption rate inside the team? Vahaaho-Pesola says "any team member connects" but doesn't say how many actually do, daily.
- What does the MCP layer actually pull? "Real-time market & audience intel" is vague. Specific MCPs not named.
- Cost trajectory: "a few weeks of evenings + Opus tokens." What's the monthly run rate at steady state? Not addressed.
- How does this coexist with existing marketing tools (HubSpot, Marketo, etc.)? OS pattern plus marketing automation stack equals what?
- Is the Barona OS publicly viewable as a reference, or proprietary? The post implies the latter, but the four-layer pattern is shareable independent of the implementation.
- Is Vahaaho-Pesola the author? Confirm at filing — the post style and Barona context strongly suggest it, but I haven't verified the byline directly.

## Raw notes / quotes

### Direct quotes
- "I've been spending my evenings writing markdown files for our marketing team."
- "What started as an idea now has a name: the Barona Marcoms Operating System — or 'brain' as we've started calling it internally."
- "The moat isn't the AI — it's the structured business context that feeds it."
- "It's a balancing act — load too much, clog the context; load too little and it's generic output again."
- "Layer 4 — Feedback & iteration. The true magical part that makes the system compound: every output feeds back what worked. Next month's content gets sharper than this month's."
- "We're somewhat done with Layer 1 and partway into Layer 3. Layer 2 is scoped but not built. Layer 4 is still pretty far."
- "The team can generate a draft campaign brief or a content piece in our actual voice in a couple minutes, which will never be 100%, but if it's 70% there, that's *a lot* easier for the expert marketer to start from."
- "The wild part to me is that this has been a solo-project: one CMO who can't code, the business documentation we already had, a few weeks of on-and-off Claude Code learning and Opus tokens for some super powers. That's it — not rocket science."
- "My hot take: within 12 months, a system like this will be table stakes for every marketing team that wants to compete."
- "All it takes is one builder with a vision."
- "Huge credit to Kieran Flanagan for the inspiration that made this click for me!"

### The four layers (verbatim)
- 🧱 **Layer 1 — Foundation.** The context layer. Who Barona is, our brand, our services, ICPs, markets, positioning, team, stakeholders, budgets. All in markdown. All loadable on demand.
- 🔍 **Layer 2 — Research & Reach.** Feeds real-time market & audience intel and deal & customer context via MCPs into the system when (and only when) tasks need it.
- ⚙️ **Layer 3 — Execution.** The skills: Campaign briefs, Blog content, LinkedIn posts, case studies, PPT decks, press releases.
- 🔁 **Layer 4 — Feedback & iteration.** Every output feeds back what worked. Next month's content gets sharper than this month's.

### Tool stack
- **GitHub** — repository for markdown context + skills
- **Claude Code** — for building the system
- **Claude Desktop** — interface for team members
- **MCP** (FastMCP, Python server) — for Layer 2 real-time data integration
- **Claude Opus** — model layer (per "Opus tokens" reference)

### Reference framework
- **Kieran Flanagan's four-layer model** — explicitly credited as the source inspiration. Worth tracking as a reference framework that's likely to recur in future captures.

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/marketing/captures/.
This will be the first file in this folder; remove the .gitkeep placeholder
if it exists. Commit as 'wiki: capture barona-marcoms-os for 
ai-gtm-playbook/marketing' and push.
```

Then attach the file.
