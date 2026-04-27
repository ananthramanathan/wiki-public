# Capture: SaaStr Deli (Customer Support Agent)
_Captured: 2026-04-27_
_Source: SaaStr AI Agent Playbook for GTM, by Jason Lemkin & Amelia Lerutte, February 2026 (PDF)_
_Topic: ai-gtm-playbook → revops_

## What this is
SaaStr's customer support automation, called "Deli." Handles event questions, sponsor inquiries, and general SaaStr questions 24/7. Achieves 97% accuracy with 3% escalation rate to humans. Response time: instant, vs. previous 24-hour SLA. 50%+ of inbound conversations happen overnight while the team sleeps.

## How it works

### The architecture
- 24/7 support agent on customer-facing surfaces
- Handles event questions (logistics, schedule, registration, refunds)
- Handles sponsor inquiries (sponsorship tiers, deliverables, contact routing)
- Handles general SaaStr questions (community, content, AI events)
- Escalates 3% of cases to humans via a VIP Escalation Agent
- Wired back to Salesforce as the single source of truth

### Performance characteristics
- 97% accuracy on customer questions
- 3% escalation rate
- Instant response (vs. previous 24-hour SLA)
- 50%+ of conversations occur overnight

### Position in the broader stack
- Customer-facing surface (unlike Momentum/Attention which are internal)
- Coordinates with VIP Escalation Agent for high-value contact routing
- Likely shares context with Qualified for prospects vs. customers — but source doesn't detail the boundary

### Training and oversight
- Same daily QA discipline as the rest of the stack: read every conversation in first 30 days, then 20–30 min daily spot-checks
- Slack notifications fire on every interaction
- Real-time response from execs when they're awake; first thing in morning when not

## What's distinctive

1. **97% accuracy is the operator-relevant headline.** Most B2B support orgs don't measure or hit this. The 24-hour SLA → instant response shift is the surface change; the 97% accuracy is what makes it safe to deploy.

2. **The 3% escalation rate is calibrated, not aspirational.** Source frames this as "right amount of human" — enough that complex/edge cases get human attention, low enough that humans aren't doing routine triage.

3. **Customer-facing surface with low risk of brand damage.** Unlike outbound (where bad emails embarrass you publicly) or inbound chat (where bad qualification loses revenue), support has a more contained failure mode — wrong answer, customer asks again or escalates. The downside of being wrong is bounded.

4. **Overnight coverage is the unlock for global/community businesses.** SaaStr operates a global community with timezone spread. 50%+ overnight conversations means half the customer experience used to be "wait until business hours." The agent eliminates that.

5. **Replaces a job humans were doing badly, not a job humans weren't doing.** Unlike Agentforce (work humans refused) or Momentum (work humans didn't do), Deli replaces work humans were doing — just slowly and with worse coverage. Different deployment justification than the sales agents.

## The author's stated purpose
Jason and Amelia present support automation as one of the cleanest deployment cases — a layup with high accuracy ceiling, low brand-damage risk, and an obvious metric (response time + accuracy). The deeper purpose is showing operators that customer support is an early target, not a late one. Most operators wait to deploy AI on customer-facing support surfaces because they're worried about quality. The source's argument is that 97% accuracy at instant response beats 95% accuracy at 24-hour SLA.

Why this purpose matters for an operator: support is one of the surfaces where the "incognito mode test" most often fails. Operators trying their own support flow will frequently be the thing that makes them cry. This is the agent you buy to fix what makes you cry.

## Pros / cons as the source presents them

### Pros
- 97% accuracy on customer questions
- 3% human escalation rate
- Instant response vs. 24-hour SLA
- 50%+ overnight coverage that humans couldn't provide
- Bounded failure mode (worst case: customer asks again, escalates)
- Frees humans for higher-value work (per the broader playbook)

### Cons
- 3% escalation still requires human capacity on standby
- Quality of the knowledge base directly determines the agent's accuracy (not detailed in source)
- Same daily QA discipline as every other agent
- Bad answers in support can compound across customers (one wrong answer told to many)
- The 97% / 3% numbers are SaaStr-specific; less mature deployments will be much worse for months

## Cross-cutting principles that apply to this surface

### Start with layups
Support is the canonical layup along with inbound chat. Well-understood playbook, clear metrics, bounded failure mode. The source's deployment-order advice would put this in the first 1–3 agents.

### "Pretty good at scale"
Same principle as outbound. The Deli answers aren't the best support responses ever written. They're 97% accurate at 24/7 instant coverage, which beats human-quality answers at 24-hour SLA.

### Forward Deployed Engineers matter
Not specifically called out for Deli but implied — same vendor-partnership pattern as the rest of the stack.

### Daily training
First 30 days: read everything. Then spot-checks. Performance correlates with attention.

### Tell agents what they CAN'T do
Specifically relevant for support. Agents will try to resolve cases by promising things the company can't deliver (refunds, credits, custom packages). Negative constraints are required.

### The incognito mode test
Support is the surface most likely to fail this test. "You will cry about some of the things you see. Pick the thing that makes you cry the most. Go buy that agent and fix it."

## Operator-relevant signal

- **Deploy-order implication:** Support is in the first wave (1–3), not the third wave (10+). The source explicitly frames it as a layup.
- **Cost-of-bad-answer is bounded.** Compared to outbound (where a bad email is in someone's inbox forever) or inbound (where bad qualification kills a deal), support failures are usually recoverable. This makes it a safer place to start.
- **Knowledge base architecture is the load-bearing question.** The source doesn't detail what corpus Deli pulls from, but for an operator deploying the same, the knowledge base quality directly determines the accuracy ceiling.
- **Org-design implication for support team.** Support roles transform — most routine triage disappears, the remaining 3% escalation work requires more skill. Volume of support headcount drops; per-person seniority rises.
- **Customer satisfaction as the meaningful metric, not deflection rate.** Operators will be tempted to optimise deflection (% of cases the AI handles end-to-end). The source implicitly argues for accuracy + escalation calibration as the meaningful metric — keeping humans involved on the right 3% matters more than maximising AI handling.
- **Trust transfer to customers.** Customers eventually figure out they're talking to AI. The 97% accuracy is what makes them OK with it. Operators deploying support AI before they've nailed accuracy will damage trust faster than they can fix it.

## Open questions

- What's the knowledge base architecture? The source doesn't describe what Deli reads from to answer questions. For operators building the same, this is the question that matters most.
- What does the 3% escalation routing look like? Auto-detected confidence threshold? Customer requests human? Specific topic flags?
- Is Deli on multiple channels (chat, email, in-app, Slack community) or one? Source doesn't specify.
- How does Deli coordinate with Qualified on the customer-vs-prospect boundary? Both are customer-facing chat surfaces.
- What's the failure mode for the 3% that wrongly stays with the AI (false negatives on escalation)? Source doesn't address.
- How does Deli handle cases where the right answer is "we don't know" or "policy needs to be checked"? Inventing answers is the canonical support AI failure mode.
- Cost: the source bundles "additional tools: ~$3,000/month" without breaking out Deli specifically.

## Raw notes / quotes

### Numbers specific to this surface
- 97% accuracy on customer questions
- 3% escalated to humans
- Response time: instant (vs. previous 24-hour SLA)
- 50%+ of inbound conversations overnight

### Direct quotes
- "Customer Support: 97% accuracy on customer questions. 3% escalated to humans. Response time: Instant (vs. previous 24-hour SLA). 50%+ of inbound conversations happen overnight while team sleeps."
- "Deli (Support Bot): Handles event questions, sponsor inquiries, general SaaStr questions 24/7."
- "VIP Escalation Agent: Identifies and routes high-value contacts to human team."
- "Use the incognito mode test... I promise you: you will cry about some of the things you see. Pick the thing that makes you cry the most. Go buy that agent and fix it."

### Tool stack
- **Deli** — primary support agent (proprietary or third-party not clearly specified in source)
- **VIP Escalation Agent** — routing layer for high-value contacts
- **Salesforce** — single source of truth
- **Slack** — notification layer for human oversight

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/revops/captures/.
Create the folder if it doesn't exist. Commit as 'wiki: capture
saastr-deli-support for ai-gtm-playbook/revops' and push.
```

Then attach the file.
