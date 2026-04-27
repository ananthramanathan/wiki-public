# Capture: SaaStr Agentforce Lead Reactivation
_Captured: 2026-04-27_
_Source: SaaStr AI Agent Playbook for GTM, by Jason Lemkin & Amelia Lerutte, February 2026 (PDF)_
_Topic: ai-gtm-playbook → sales_

## What this is
SaaStr's lead reactivation agent built on Salesforce Agentforce. Targets ghosted, neglected, and lapsed leads — including five- and six-figure sponsor prospects who reached out and were never followed up with by human SDRs. Achieves 72% open rates and 10%+ response rates on leads previously considered dead.

## How it works

### The architecture
- Salesforce Agentforce running on top of the existing Salesforce data
- Targets specifically the leads humans refused or forgot to follow up with
- Re-engages with context drawn from the original lead source and Salesforce history
- Routes responses back through the standard sales process
- Pricing model: ~$2/conversation

### The reactivation segments
Agentforce specifically runs against:
- Sponsor prospects who reached out for five- and six-figure deals and never got a response
- Lapsed contacts from prior years' events
- Form-fill leads that human SDRs deprioritised
- Marketing-qualified leads that fell through the cracks
- Any segment that human SDRs systematically refused to work

### Why these leads existed in the first place
This is the operator-relevant context. SaaStr's human SDRs:
- Wanted to hunt six-figure sponsorships, not chase ticket sales
- Tried incentives (Starbucks cards), begging, accountability checks — all failed
- Said they'd follow up with return attendees, then activity logs showed they didn't
- Systematically ignored entire segments because the per-lead value was too low

The result: a backlog of warm-but-untouched leads sitting in Salesforce, accumulating over time.

### The reactivation outcomes
- 72% open rate on "dead" leads
- 10%+ response rate on the same
- Generated 15% of London ticket revenue (in combination with Artisan SDR)
- Re-engaged sponsor prospects who'd already raised their hand for $50K–$200K commitments

## What's distinctive

1. **Found-revenue is the entire thesis.** This isn't AI doing sales better than humans. It's AI doing sales humans refused to do at all. The 72% open / 10%+ response rates aren't "better than human SDR" — they're "infinitely better than zero," because the human number on these leads was zero.

2. **Operates on the existing Salesforce graveyard.** No new lead sourcing. No new prospecting. The TAM for this agent is "leads we already have but haven't worked." For most B2B companies, this is a substantial number.

3. **Reveals a structural inefficiency in human SDR comp.** The reason leads went dead is rational individual behaviour — SDRs maximised commission by chasing big deals, not small ones. Agentforce reveals what the org-level cost of that rational behaviour was.

4. **Per-conversation pricing changes the math.** At ~$2/conversation, the ROI calculation is conversation-by-conversation, not seat-based. This makes it economically viable to re-engage segments where per-lead expected value is low.

5. **The "ghosted sponsor" specific case.** SaaStr explicitly calls out that humans ignored people offering them five- and six-figure sponsorships. That's not a low-value segment being ignored — that's high-value leads dying because of capacity/prioritisation failures. Agentforce's first job was triaging this backlog.

## The author's stated purpose
Jason and Amelia frame Agentforce as the canonical "found revenue" example — proof that the right place to deploy AI is wherever humans systematically refuse to work, not wherever humans are weakest. The deeper purpose is shifting operator thinking: stop trying to make your existing SDR team better with AI; start auditing what your team isn't doing and put AI there.

Why this purpose matters for an operator: every B2B org has a Salesforce graveyard. The CCO/COO question this surfaces is "what's the dollar value of leads in our system that humans systematically don't work?" That's an audit operators can run before deciding whether reactivation AI is worth deploying.

## Pros / cons as the source presents them

### Pros
- 72% open rate on previously "dead" leads
- 10%+ response rate
- Zero cannibalisation of existing pipeline by definition (these leads were going to be ignored)
- Per-conversation pricing makes it economically viable on low-EV segments
- Native Salesforce integration — minimal data plumbing
- Re-engages high-value sponsors humans dropped

### Cons
- Only works if you have a Salesforce graveyard (so most B2B but not all)
- Per-conversation pricing scales linearly with engagement — at high volume, costs add up
- Requires the same daily QA discipline as other agents
- The 72% / 10%+ numbers come from a strong-brand company (SaaStr) where the original outreach had brand recognition; unclear how this generalises to less-known brands

## Cross-cutting principles that apply to this surface

### Found-revenue doctrine
This is the surface where the doctrine is most explicit. "If your team consistently refuses to do certain work, stop fighting it. Deploy an AI agent on that segment immediately." Agentforce is the canonical example.

### Start with hot, not cold
Reactivation is the warmest possible segment — these are leads who already raised their hand once. Per the source's deployment order, this is closer to position #1–3 than to truly cold outbound.

### Single source of truth
Agentforce works because Salesforce is the system of record. The agent has full context on every prior interaction. If your CRM is dirty, the agent's context is dirty.

### Forward Deployed Engineers matter
SaaStr cites Salesforce specifically as having put an FDE on their success team. Same vendor-relationship pattern as Qualified and Artisan.

### Tell agents what they CAN'T do
Reactivation agents have a specific failure mode: they over-apologise for the original ghosting, or they offer concessions to make up for it. Negative constraints (no compensatory discounts, no "we owe you anything," no implicit promises about future responsiveness) are required.

## Operator-relevant signal

- **The Salesforce-graveyard audit as a pre-deployment exercise.** Before deploying reactivation AI, run the audit: how many leads in your CRM are >90 days old, marked as MQL or higher, and have zero outbound activity in the last 30 days? That's your reactivation TAM.
- **Comp-design implication.** Reactivation AI exposes the org-level cost of commission-maximising SDR behaviour. If the AI captures 15% of revenue from leads humans refused, the question becomes whether comp design should change — or whether the human SDR role itself should be redefined to exclude this segment.
- **The "found revenue" story is the cleanest board narrative.** Easier to defend than "AI is making our humans better." This is "AI is doing work we weren't doing at all and capturing revenue we were leaving on the table." Less politically sensitive internally.
- **Org-design implication.** Where does reactivation sit? Sales? Marketing? RevOps? At SaaStr it's Sales-adjacent but the activity is more like marketing nurture. The org placement matters because it determines who owns the metric.
- **First-90-days commitment.** Agentforce isn't plug-and-play. Same daily-QA discipline as every other agent in the stack. Don't deploy unless you have the exec time.

## Open questions

- What's the size of SaaStr's Salesforce graveyard? The 72% / 10%+ numbers are rates, not volumes — without the denominator, hard to benchmark.
- Does the 72% open rate hold at scale, or does it degrade as you work deeper into the graveyard? Top of the graveyard is the warmest leads; the bottom may not perform similarly.
- How does Agentforce hand off to humans when a reactivated lead engages seriously? The source doesn't detail this routing.
- What's the brand-recognition floor for this to work? SaaStr leads remember SaaStr. A SaaS company most leads barely recall might see very different rates.
- How does the per-conversation pricing scale? At $2/conversation × thousands of conversations, the cost becomes meaningful. The economic model isn't free; it's just better than the alternative of leaving leads dead.
- Could this be done on HubSpot or other CRMs? The source ties it specifically to Salesforce/Agentforce. Operators on other stacks need to know if equivalents exist.

## Raw notes / quotes

### Numbers specific to this surface
- 72% open rate on "dead" leads
- 10%+ response rate on same
- ~$2/conversation pricing
- Combined with Artisan, generated 15% of London ticket revenue
- Re-engaged ghosted sponsor prospects at five- and six-figure deal sizes

### Direct quotes
- "Same story with our 'ghosted' leads — people who reached out wanting to sponsor SaaStr for five and six figures, and our human team just... never followed up. Agentforce re-engaged those leads with 72% open rates and 10%+ response rates."
- "If your team consistently refuses to do certain work, stop fighting it. Deploy an AI agent on that segment immediately."
- "Our human SDRs wouldn't follow up with return attendees for ticket sales. It wasn't worth their time — they wanted to hunt six-figure sponsorships instead. We tried incentives. We tried Starbucks cards. We begged them. They said they'd do it, then we'd check the activity logs and discover they lied."
- "Salesforce put an FDE on our success team."

### Tool stack
- **Agentforce** — Salesforce-native, ~$2/conversation
- **Salesforce** — system of record (and source of the graveyard data)
- **Zapier** — webhook layer for cross-agent context

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/sales/captures/.
Create the folder if it doesn't exist. Commit as 'wiki: capture
saastr-agentforce-reactivation for ai-gtm-playbook/sales' and push.
```

Then attach the file.
