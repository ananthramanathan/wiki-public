# Capture: SaaStr "10K" — AI VP of Marketing (Orchestrator)
_Captured: 2026-04-27_
_Source: SaaStr AI Agent Playbook for GTM, by Jason Lemkin & Amelia Lerutte, February 2026 (PDF)_
_Topic: ai-gtm-playbook → orchestrators_

## What this is
SaaStr's proprietary-built AI VP of Marketing, nicknamed "10K" (after the goals: 10,000 attendees for SaaStr Annual + $10M revenue for the year). Built in a weekend on Claude Opus + Replit. Generates week-by-week marketing game plans with daily executable tasks across all SaaStr's other agents (Qualified, Artisan, Agentforce) plus human-executed work (Jason's social posts, LinkedIn ad spend). Not connected to tools directly — generates plans; humans execute.

This is the only build (not buy) agent in SaaStr's stack of any operational significance.

## How it works

### Why they built it (instead of buying)
SaaStr couldn't find a viable third-party marketing agent that could do more than content. Most marketing AI tools are content-related (write the copy, generate the image). SaaStr's problem was orchestration:
- Based on data
- Based on already having other agents
- Based on proprietary information about goals, calendar, segments

Every time they tried to onboard an actual human VP of Marketing with all this data, the human got overwhelmed.

So they built the agent.

### The build

**Stack:**
- Claude Opus on the Max plan (Pro ran out of memory — this is the operator-relevant detail)
- Pushed to Replit to create a website the team can access
- Built in a weekend

**Inputs:**
- Data from SaaStr's other agents and third-party tools
- Internal data — cherry-picked the best, not all of it
- Zapier workflows
- Salesforce data
- Registration patterns, time-of-day buying patterns
- Recent agent interactions

**Initial prompts/instructions:**
- "Give me a 6-month roadmap"
- "Give me high-level AND executable daily tasks"
- "Ground everything in the data"
- "Make it easy enough for the 3 humans + 1 dog to execute"

### What it produces

A week-by-week game plan:
- Early weeks: early bird campaigns
- January: alumni campaigns
- February: speaker announcements
- Etc.

Click into any week and it has executable detail:
- The emails to send
- What to do with Qualified
- What to do with Artisan
- What to do with Agentforce
- What Jason should post on social
- How much to spend on LinkedIn ads and what the ads should be

### What it doesn't do

It's not connected to the tools directly. It doesn't draft LinkedIn ads automatically. It doesn't write email copy in Artisan. It generates ideas; humans execute.

By H2 2026 (per the source), this should connect natively — the AI VP of Marketing wired via Zapier or direct integration to LinkedIn, AI SDR, email tools. Today it's telling SaaStr what to do and keeping them honest.

### How it's used day-to-day

Jason: "I talk to 10K every day: 'Where are we at? What should we be doing today? Where are we falling behind?'"

It's a planning and accountability layer, not an execution layer.

### When it's wrong

Jason challenges its outputs. Example: it gave a campaign for end of January that he didn't think had urgency. He pushed back. It looked at the data, looked at his points, agreed they should change it.

"It's not always right. But it's not always wrong. The key is human orchestration — checking in with it, challenging it when something feels off."

## What's distinctive

1. **Built, not bought — and the only one in the stack.** The 90/10 buy/build rule is being applied. SaaStr buys 90% of their stack; 10K is the 10%. The reason cited: no vendor does this category well.

2. **Operates one layer above worker agents.** Worker agents (Artisan, Qualified, Agentforce) answer "how do I do this job?" 10K answers "given my goals and the agents/humans available, what should everyone do this week?" Different problem, different architecture.

3. **The "VP of Marketing" framing is load-bearing.** This isn't a tool — it's a role. SaaStr couldn't hire a human into the role (they got overwhelmed by the data) so they built one. The implicit claim: AI-VP roles are now viable in domains where the data complexity exceeds what a human can hold in their head.

4. **Disconnection from tools is admitted as a current limitation, not a design choice.** Source explicitly flags this changes by H2 2026. The current architecture is "AI plans, humans execute" but the trajectory is toward "AI plans, AI executes via integrations."

5. **Jason talks to it daily.** This is the use pattern most operators won't believe. The CEO has a daily standing conversation with an AI agent he built about what marketing should be doing. That's not "I check in on the agent's output" — that's "the agent is in the org chart."

6. **Built in a weekend with a reasonable stack.** Claude Opus + Replit. Not a year-long build with a team. The implication for operators: orchestrator agents are buildable now, by exec teams, without dedicated engineering investment.

## The author's stated purpose
Jason and Amelia present 10K as proof that the AI executive layer is viable today, not someday. The deeper purpose is showing operators that orchestration agents are different from worker agents in build-or-buy economics, in oversight pattern, and in role within the org. The source explicitly distinguishes this from worker agents and explicitly flags that it's the only build in the stack.

Why this purpose matters for an operator: if you're a CCO/COO building an AI-first GTM org, the question of "do we need an AI VP of X" is the most strategically important architectural question. SaaStr's answer: yes, we needed one for marketing because no human could hold the data, and we built it because no vendor does it well, and it cost us a weekend.

## Pros / cons as the source presents them

### Pros
- Replaced an unhireable role (humans got overwhelmed by the data)
- Gives Jason a daily planning and accountability layer
- Granular enough to direct execution across the stack (specific emails, specific ad spend, specific posts)
- Built in a weekend on accessible tools
- Costs less than a VP Marketing salary
- Updated with real-time data from the rest of the stack

### Cons
- Not connected to tools — humans still execute
- Not always right; requires human challenge
- Required Claude Opus on Max plan (Pro ran out of memory) — implies real cost at usage
- Single-source dependency on Claude — if model degrades or pricing changes, the agent's economics shift
- The build was possible because SaaStr already had data flowing from other agents; an org without that prerequisite couldn't replicate
- "It's been a problem for now, not forever" — the orchestration architecture is admitted as transitional

## Cross-cutting principles that apply to this surface

### 90/10 buy/build
This is the 10%. SaaStr could not find a third-party marketing orchestrator that worked. Every other agent in the stack is bought. The decision to build was driven by absence of a viable vendor, not by preference for in-house.

### Single source of truth
10K reads from Salesforce + agent outputs + Zapier-aggregated data. Without the SOT being clean (which Momentum + Attention enforce), 10K's plans would be based on fiction.

### Tell the agent what it CAN'T do
Implicit — 10K is told what SaaStr's offers are, what their constraints are, what the goals are. The negative-constraint discipline applies even to orchestrators.

### Daily training / daily oversight
Jason talks to 10K every day. This is closer to "managing a direct report" than "monitoring a tool." The oversight pattern is daily, not weekly or monthly.

### "Pretty good at scale"
The plans 10K generates aren't the best marketing plans ever written. They're ground in real data, generated weekly, granular enough to execute, and updated as the data changes. Pretty good at full coverage beats great at partial coverage.

## Operator-relevant signal

- **The orchestrator is the role, not the tool.** This is the most important architectural shift for an operator to understand. You're not buying a marketing tool that uses AI. You're effectively hiring an AI into an executive role that humans can no longer fill due to data complexity.
- **Build economics: a weekend, not a year.** Claude Opus + Replit. The build cost is a few days of executive time. The ongoing cost is Claude Max plan usage. Compare to a VP Marketing salary (~$300K loaded cost) and the math is decisive.
- **Daily executive interaction is the use pattern.** Operators thinking of this as "set up the agent and check on it monthly" have the wrong model. Jason talks to 10K daily. If you're not willing to talk to your orchestrator daily, you don't need one yet.
- **The prerequisite is data-flow architecture.** 10K works because SaaStr has data flowing from Qualified, Artisan, Agentforce, Momentum, Attention, all unified in Salesforce. An org without that data architecture can't build a useful orchestrator — it would be operating on fiction.
- **Org-chart implication.** When orchestrator agents are real, the question of "do we hire a VP Marketing" becomes "do we build a VP Marketing." This is the role-displacement argument that hits hardest at the executive layer, not the IC layer. The $250K SDR replacing the $80K SDR is one story; the AI VP Marketing replacing the $300K human VP is a different story.
- **Reporting line question.** Who does 10K report to? At SaaStr it's Jason. In a larger org with a CMO, would the orchestrator report to the CMO, or replace the CMO? The source doesn't address this.
- **Career implication for the operator.** If you're a CCO/COO upskilling for an AI-first GTM org, building an orchestrator (or being able to articulate how one would work for your business) is the single most defensible skill. It's the thing CMOs/CROs without it can't do.

## Open questions

- How does 10K handle being wrong? When a plan doesn't pan out, does Jason update the prompt? Add to the data? Re-prompt fresh? The source describes one anecdote but not a systematic correction loop.
- What's the prompt architecture? "Give me a 6-month roadmap" is the high-level prompt, but there must be a system prompt with company context, constraints, KPIs, calendar, etc. The source doesn't expose this.
- How does 10K stay current? If it's Claude Opus accessed via Replit, does it have ongoing data feeds or is it re-prompted with fresh context each time?
- Where does this break? At SaaStr's scale (3 humans, 20 agents) it works. At 50 humans with 100 agents and a more complex P&L, does the same architecture scale?
- What's the cost-per-month at SaaStr's usage? Claude Max plan + Replit hosting + dev time. Source doesn't specify.
- What happens if Claude Opus pricing changes 5x? The economic model has model-pricing risk.
- Could this be done with a non-Anthropic model? The source specifies Claude Opus but doesn't address whether GPT-5 or other models would work equivalently.
- How does 10K interact with Digital Jason? Both are Claude-based, both touch the same business. Source doesn't address the relationship.

## Raw notes / quotes

### The build details
- Claude Opus, Max plan (had to upgrade from Pro — Pro ran out of memory)
- Pushed to Replit to create a website the team can access
- Took a weekend to build

### The instruction set used
- "Give me a 6-month roadmap"
- "Give me high-level AND executable daily tasks"
- "Ground everything in the data"
- "Make it easy enough for the 3 humans + 1 dog to execute"

### What it does (granularity)
Click into any week, you get:
- The emails to send
- What to do with Qualified
- What to do with Artisan
- What to do with Agentforce
- What Jason should post on social
- How much to spend on LinkedIn ads and what the ads should be

### Direct quotes
- "We couldn't find a viable third-party marketing agent that could do more than content. Most marketing tools do content-related activities."
- "Our problem was orchestration — based on data, based on already having other agents, based on proprietary information."
- "Every time we tried to onboard an actual human with all this data, they got overwhelmed."
- "I talk to 10K every day: 'Where are we at? What should we be doing today? Where are we falling behind?'"
- "It's not always right. But it's not always wrong. The key is human orchestration — checking in with it, challenging it when something feels off."
- "The biggest thing 10K does: It keeps me extremely organized in one very particular vector. Because I manage so many agents and still do sales and production goals, it keeps me honest on what I should be doing and focusing on each day."
- "By late 2026, this should all connect natively — the AI VP of Marketing connected via Zapier or direct integration to LinkedIn, to your AI SDR, to your email tool. But today, it's telling us what to do and keeping us honest."

### Tool stack
- **Claude Opus** (Max plan) — the brain
- **Replit** — UI hosting
- **Zapier** — data piping from other agents
- **Salesforce** — single source of truth feeding context
- All other agents in the SaaStr stack — data inputs

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/orchestrators/captures/.
Create the folder if it doesn't exist. Commit as 'wiki: capture
saastr-10k-vp-marketing for ai-gtm-playbook/orchestrators' and push.
```

Then attach the file.
