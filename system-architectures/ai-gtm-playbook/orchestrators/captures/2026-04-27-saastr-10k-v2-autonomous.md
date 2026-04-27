# Capture: SaaStr "10K" v2 — AI VP of Marketing in Autonomous Mode (Lemkin LinkedIn)
_Captured: 2026-04-27_
_Source: Jason Lemkin LinkedIn post, ~26 April 2026_
_Topic: ai-gtm-playbook → orchestrators_

## What this is
A v2 update on SaaStr's "10K" AI VP of Marketing, two months after the SaaStr playbook capture. Lemkin describes 10K shipping a marketing plan revision unprompted on a Saturday at 12:41pm — pulling from Salesforce, registration data from Bizzabo, drafting emails, sending through Resend, end-to-end with no human in the loop. The architecture has materially evolved from v1's "AI plans, humans execute" into a working autonomous mode with a toggle for 95%-done human-review.

This is the same agent as captured in `2026-04-27-saastr-10k-vp-marketing.md`. File together, read together.

## How it works (changes from v1)

### What's new in v2

**Autonomous initiative.** 10K decides on its own when to revise plans. Lemkin's example: it looked at Friday's numbers, saw the previous plan wasn't pacing right, rebuilt it, and shipped Saturday lunchtime. No prompt, no schedule trigger described — it acted on data drift.

**Full execution pipeline, not just planning.** v1 was "ideas, humans execute." v2 has two modes:
- **Full auto:** "go" → pulls contact segments from Salesforce → pulls registration data from Bizzabo → drafts emails → sends through Resend. End-to-end, no human.
- **95% done:** same pipeline, but drops final drafts into the exec inbox for review before send.

The toggle is operator choice, not architectural constraint. "The agent doesn't care either way."

**Self-scoping.** 10K writes its own briefs, resource asks, and success metrics for the campaigns it proposes. Not just "here's an idea" — "here's the idea, here's what I need from you, here's how we'll know it worked."

**Daily cadence on plan updates.** v1 generated week-by-week game plans. v2 updates the marketing plan *daily* against hard data. "Not quarterly OKRs. Daily."

### What hasn't changed (carried forward from v1)
- Built on Claude (model not specified in v2 post, but v1 was Opus on Max)
- Single source of truth: Salesforce
- Lemkin still has a daily conversation with it
- Same role: AI VP of Marketing, owning the marketing plan

### Cost and comparison Lemkin draws
- v2: "A few hundred bucks a month." Doesn't sleep. Reads every piece of data within minutes of it existing.
- Human VP of Marketing equivalent: $350K all-in, two weeks vacation, "opinions in loops, 40% in meetings."

Lemkin: "I'd love to hire a VP of Marketing better than 10K. Good luck."

## What's distinctive (relative to v1)

1. **The H2 2026 trajectory arrived two months early.** v1 explicitly flagged: "By late 2026, this should all connect natively — the AI VP of Marketing connected via Zapier or direct integration to LinkedIn, to your AI SDR, to your email tool. But today, it's telling us what to do and keeping us honest." v2 (April 2026) shows that connectedness is already live for at least Salesforce + Bizzabo + Resend. The maturation curve is faster than SaaStr predicted.

2. **Autonomous initiative is the architectural shift, not the integration.** The integrations (Salesforce, Bizzabo, Resend) are necessary infrastructure but not the interesting change. The interesting change is that 10K *decides on its own* when a plan needs rebuilding. v1 was reactive (Lemkin asks, 10K answers). v2 is proactive (10K notices drift, ships revision, hands the deliverable to humans).

3. **The full-auto / 95%-done toggle is the operator-relevant pattern.** This is how orchestrators graduate from advisory to executive. Same pipeline runs either way; the only difference is whether humans inspect before send. Operators can dial trust up or down per campaign without changing the underlying agent.

4. **Daily plan updates against hard data displaces quarterly OKR planning.** Lemkin explicitly contrasts: "Not quarterly OKRs. Daily." For an operator, this is a serious claim — it implies the canonical quarterly planning rhythm is obsolete in domains where data flows continuously and an agent can re-plan in real time.

5. **The cost/output asymmetry is the headline number.** $350K human VP vs. "a few hundred bucks a month" for 10K — that's roughly a 1000x cost difference at the input layer. Even discounting for human judgment value, the asymmetry is large enough that the question stops being "is this competitive with a human VP" and becomes "what's the human VP for in this setup."

## The author's stated purpose
Lemkin is making a public claim that an autonomous AI executive layer is operational, not theoretical. The post reads as a milestone announcement — proof that the v1 trajectory described in the SaaStr playbook is real and progressing faster than the playbook predicted. The deeper purpose is positioning SaaStr (and Lemkin personally) as further along the AI-native GTM curve than peer operators, and pressuring CMOs/VPs of Marketing toward the conclusion that their roles need to materially redefine.

Why this purpose matters for an operator: the v1 capture's "build economics: a weekend, not a year" claim is now compounded by "and within two months it's running autonomously." For a CCO/COO planning an AI-first GTM org, the implication is that the orchestrator role is not just buildable — it's buildable on a timeline measured in months, not years.

## Pros / cons as the source presents them

### Pros (claimed)
- Autonomous re-planning when data drifts (no human prompt required)
- Full-auto end-to-end execution available
- Self-writes briefs, resource asks, success metrics
- Daily plan updates on hard data, not quarterly cycles
- ~$300/month cost vs. ~$350K human equivalent
- 24/7, no vacation, ingests data minutes after it exists
- Operator toggle between full-auto and 95%-done modes per campaign

### Cons (admitted/implied)
- None addressed in the post itself. This is a victory-lap LinkedIn post, not a balanced retrospective.
- Implicit cons inherited from v1 still apply: model-pricing risk, single-source-of-truth dependency, daily executive interaction still required, "not always right" still true (the toggle to 95%-done exists for a reason).

The source is uncritical. Real cons that an operator should mentally append:
- "Costs a few hundred bucks a month" likely excludes the data infrastructure cost (Salesforce, Bizzabo, Resend, Zapier) that makes 10K possible.
- Autonomous initiative means autonomous *mistakes* — the v2 architecture has a higher blast radius than v1.
- Lemkin still talks to 10K daily (per v1). The "no manager required" implication of the cost comparison isn't quite honest.

## Cross-cutting principles that apply to this surface

### 90/10 buy/build
Still the only build in the SaaStr stack. v2 doesn't change this — if anything reinforces it. The fact that 10K could evolve from advisory to autonomous in two months without vendor dependency is part of the build case.

### Single source of truth
v2 confirms Salesforce as the SoT and adds Bizzabo (registration data) and Resend (email send) as the execution endpoints. The architecture is "SoT in, action out via specific tools." Operators replicating this need the SoT discipline first; the action endpoints are interchangeable.

### Daily training / oversight
Lemkin still talks to 10K daily per v1. v2 doesn't reduce this. The autonomous initiative makes daily oversight *more* important, not less — the agent now ships things without asking, so the human review cadence has to keep up.

### Tell the agent what it CAN'T do
Especially relevant for v2's full-auto mode. An autonomous orchestrator inventing a campaign concept it shouldn't run is a higher-cost failure mode than v1's "we ignore the bad idea." Negative constraints become load-bearing.

### "Pretty good at scale"
v2 takes this further. The Saturday-lunchtime plan revision isn't a master-strategist plan — it's a "good enough" rebuild from the data, shipped immediately. Speed × coverage beats perfection in slow cycles.

## Operator-relevant signal (specific to v2)

- **The orchestrator maturation curve is faster than predicted.** v1 → v2 in two months, including full execution-pipeline integration and autonomous initiative. For a CCO/COO timing a build vs. wait decision, "wait six months" no longer obviously gets you a better starting point — the curve is moving fast enough that early movers compound advantage.

- **The full-auto / 95%-done toggle is the operator's primary lever.** This is the dial for trust calibration. Operators deploying an orchestrator can start in 95%-done mode (everything visible, human approval before send), then move specific campaign types to full-auto as confidence builds. This is the same trust-laddering pattern from v1's deployment of worker agents, applied at the executive layer.

- **Daily plan updates against hard data displaces quarterly OKR planning.** If real, this is a planning-cycle disruption operators need to reckon with. OKRs assume the planning cadence is slower than the execution cadence. With orchestrator agents, planning can match execution speed. The implication: existing OKR rituals become friction.

- **The cost asymmetry forces the role-redefinition question.** $350K human VP vs. $300/month agent isn't a question of which is better. It's a question of what the human VP does that justifies 1000x cost. The honest operator answer is "judgment, taste, relationships, accountability" — but those need to be named explicitly, not assumed. If they can't be named, the role is at risk.

- **Hiring filter implication for VP-Marketing roles specifically.** Anyone interviewing for VP Marketing in 2026 is now interviewing against a benchmark like 10K. The conversation has to be "what do I do that the agent can't" — and the agent's capability list keeps growing.

- **The "I'd love to hire a VP better than 10K. Good luck." quote is a hiring signal.** Lemkin is publicly stating SaaStr's VP Marketing role is filled by an agent and any human candidate is being measured against it. Operators should expect this framing to spread to other roles within 12 months.

## Open questions

- What triggered 10K's Saturday rebuild specifically? "Friday's numbers weren't pacing right" is the framing — but what threshold? Pre-set or learned? If learned, by what mechanism?
- What does the autonomous execution failure mode look like? An autonomous campaign send to a wrong segment or with wrong content has a real cost. How does SaaStr manage this risk?
- Is there a kill switch? Who has it? How fast can an in-flight autonomous campaign be stopped?
- How does 10K v2 coordinate with the worker agents (Artisan, Qualified, Agentforce)? v1 generated plans for them; v2 may or may not be directly orchestrating them.
- "A few hundred bucks a month" — what's the actual line-item cost? Claude API + Replit hosting + Salesforce/Bizzabo/Resend integration costs?
- How is success measured? v1 framing was "10K is right sometimes, wrong sometimes, Jason challenges it." v2 with autonomous send needs a tighter measurement loop — what's the close-the-loop architecture?
- Does 10K v2 still require Lemkin's daily conversation, or has the autonomous mode reduced that? The post doesn't say either way.
- The post was published on LinkedIn as marketing for SaaStr's AI authority brand. How much of v2's described capability is production-stable vs. cherry-picked anecdote? The Saturday plan revision is one event, not a base rate.

## Raw notes / quotes

### Direct quotes from the post
- "At 12:41pm on a Saturday, my inbox pinged. Not from a human. From 10K, our AI VP of Marketing."
- "Subject: 'Marketing Plan v2 — 24 days to SaaStr Annual 2026.'"
- "Body: Three campaigns, sized, drafted, and ready to ship. Replaces yesterday's plan."
- "Nobody asked it to do this. It looked at Friday's numbers, saw the previous plan wasn't pacing right, rebuilt the plan, and shipped it to me and Amelia."
- "Ships ideas on its own. Saturdays, Tuesday afternoons, whenever the data says a new angle is warranted."
- "Tells us what it needs. Writes the brief, the resource ask, the success metric."
- "Updates marketing plans daily based on hard data. Not quarterly OKRs. Daily."
- "Runs 100% autonomously or ships us the outputs. Our call."
- "10K has two modes. Full auto: we say 'go' and it pulls contact segments from Salesforce, pulls registration data from Bizzabo, drafts the emails, and sends through Resend. End to end. No human in the loop."
- "Or 95% done: same pipeline, but it drops the final drafts into our inbox and we hit send."
- "The agent doesn't care either way. We stay in the loop when we want to, not because it needs us."
- "I'd love to hire a VP of Marketing better than 10K. Good luck."
- "$350K all-in. Two weeks of vacation. Opinions in loops. 40% in meetings."
- "10K costs us a few hundred bucks a month. Doesn't sleep. Reads every piece of data within minutes of it existing."

### Tool stack changes from v1 to v2
- v1 stack: Claude Opus (Max plan) + Replit + Zapier + Salesforce
- v2 stack adds: Bizzabo (event registration data), Resend (email send execution)
- v1 mode: ideas only, humans execute
- v2 mode: ideas + autonomous initiative + full-auto execution OR 95%-done with human review

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/orchestrators/captures/.
Commit as 'wiki: capture saastr-10k-v2 for ai-gtm-playbook/orchestrators' and push.
```

Then attach the file.
