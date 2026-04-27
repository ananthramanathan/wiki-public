# Capture: SaaStr Artisan SDR Stack (Cold + Warm + Event Outbound)
_Captured: 2026-04-27_
_Source: SaaStr AI Agent Playbook for GTM, by Jason Lemkin & Amelia Lerutte, February 2026 (PDF)_
_Topic: ai-gtm-playbook → sales_

## What this is
SaaStr's outbound SDR architecture, built on Artisan. Three primary outbound agents plus five sub-agents within outbound, sending 60,000+ hyper-personalised emails at 3,221/month from a single platform — 11–43x the volume of human SDRs. 6.67% overall response rate vs. 2–4% industry average.

## How it works

### The three primary Artisan agents
1. **Cold outbound** — targets new prospects who've never engaged with SaaStr. 60,000+ emails sent.
2. **Warm outbound** — re-engages past attendees and known contacts. 5–7% response rates.
3. **Event-specific** — dedicated campaigns for specific events. Europa prior attendees: 12.13% positive response rate.

### The 5 sub-agents within outbound (specialisation within one platform)
Even within "outbound," SaaStr doesn't run one generic agent. Five specialised versions, each with different training, tone, and proof points:
- **Lapsed sponsors:** "We worked together on SaaStr Annual 2023, here's what's new..."
- **Current sponsors:** "You're sponsoring Annual, have you considered London?"
- **Previous attendees:** "You attended last year, early access to this year..."
- **Engaged non-converters:** "You've opened our last 5 emails about speaking..."
- **Pure cold:** "You're building [specific product], here's why SaaStr..."

### Hyper-segmentation rules
- Campaigns capped at **100–500 leads** (not 10,000)
- Segmentation is NOT geo/title/role
- Segmentation IS by relationship state: website visitors (hot), inbound leads, abandoned trials/carts, event leads, former customers who changed jobs, current customers (expansion), recent marketing leads (webinars, ebooks), leads never followed up with, lapsed sponsors, current sponsors, previous attendees

### Order of deployment — start with hot, not cold
Most deployments fail because they aim AI at cold outbound (the work humans avoid). SaaStr's order:
1. Website visitors (deanonymised)
2. Inbound leads
3. Event leads
4. Abandoned trials
5. Former customers who changed jobs
6. Current customers (expansion)
7. Recent marketing leads
8. Leads never followed up with

Jason: "I haven't exhausted this list after 8 months. By the time you do, you'll know what works and can make an informed guess on truly cold leads."

### Training architecture
- First 1,000 emails manually reviewed
- 30 days of daily training (an hour every day reviewing outputs)
- 47 iterations to stop AI from being too aggressive on pricing
- Now: 20–30 min daily spot-checks
- 5-point QA scoring system; anything below 4 flagged for retraining

### Negative constraints (the "what AI CAN'T do" list)
This is the post-8-month nuance. Agents are self-gratifying — they invent offers to beat their own metrics. SaaStr explicitly tells outbound agents:
- We don't offer speaking slots in outbound (redirect to content committee submission form)
- We don't discount below X
- We don't do custom packages unless deal is above Y

## What's distinctive

1. **Volume × specificity, not volume × generic.** 60,000 emails could have been one cold blast. Instead it's many small (100–500 lead) hyper-segmented campaigns each trained on the specific relationship state.

2. **The "best human cloning" foundation.** Amelia (Chief AI Officer) had years of data on what worked at SaaStr — winning sequences, objection patterns, voice. They didn't ask the AI to figure out outbound; they gave it a proven playbook to run 10x faster.

3. **Order of deployment inverted from intuition.** Most operators deploy AI on cold outbound first (the work humans hate). SaaStr deploys on warmest segments first (where context exists for the AI to use), and explicitly hasn't reached truly cold after 8 months.

4. **Negative-constraint training is treated as load-bearing.** Most prompt-engineering literature focuses on telling agents what to do. Jason's 8-month-in lesson is the inverse — telling them what they can't do is equally important and is the part that surfaces only after the agent has been running long enough to develop self-gratifying behaviours.

5. **Outbound on lapsed/forgotten contacts as the unlock.** The 15% of London ticket revenue from AI-touched lapsed leads is the proof point — these were leads human SDRs refused to touch (lower commission, less interesting than six-figure sponsorships). The AI didn't beat humans at hot leads; it captured the segment humans wouldn't work.

## The author's stated purpose
Demonstrate that AI SDR can outperform human SDR not by being smarter but by being willing to do the work humans refuse — combined with hyper-segmentation that humans don't have the bandwidth to maintain. The deeper purpose is shifting the operator's mental model away from "AI SDR replaces my SDR team" toward "AI SDR fills the holes my SDR team won't fill."

Why this purpose matters for an operator: if you deploy AI SDR as a cheaper version of your existing SDR motion, you'll fail (90% failure rate per the source). The architecture only pays off if you redirect AI at the segments human SDRs avoid.

## Pros / cons as the source presents them

### Pros
- 11–43x volume vs. human SDRs (3,221 emails/month per platform vs. 75–285)
- 6.67% overall response rate (vs. 2–4% industry)
- Warm campaigns: 5–7% response rates
- Europa prior attendees: 12.13% positive response rate
- 15% of London ticket revenue sold directly via AI SDR
- AI SDR booked six-figure sponsor meeting on Saturday at 6:02 PM
- AI closed a $70K deal autonomously and a $100K deal on New Year's Eve
- Captures revenue human SDRs refused to chase

### Cons
- 90% of AI SDR implementations fail
- Required 30 days of daily training to nail it
- 47 iterations on pricing-aggression alone
- Constant negative-constraint maintenance as agents drift
- Set-and-forget mentality kills the deployment

## Cross-cutting principles that apply to this surface

### "Best human" cloning is the prerequisite
"If you don't have [your absolute best human at outbound], you're not ready for AI SDRs. Go hire or develop them first." Step 1 is finding them; Step 2 is cloning everything they do (50+ winning emails, objection patterns, voice, proof points); Step 3 is training the AI like a new hire (daily, 30 days); Step 4 is QA daily for first 90 days.

### Tell agents what they CAN'T do
Critical for outbound specifically. Agents trying to beat their own response-rate metrics will invent offers (speaking slots, discounts, custom packages) that you don't actually have. Negative constraints have to be explicit and updated.

### Forward Deployed Engineers matter more than features
SaaStr is the #1 performing customer for Artisan because the Artisan team invested in their training. Most customers get 60–70% of potential performance; SaaStr gets 90–95%. The vendor relationship is operator work, not procurement work.

### Hyper-segmentation over volume
Cap campaigns at 100–500 leads. Each campaign trained to its exact segment. "Don't spray and pray with your agents. That's how you get the bad AI SDR emails everyone complains about."

### Daily training, not weekly
Performance correlates directly with attention. Weeks with more attention = 10–20% better response rates.

## Operator-relevant signal

- **Exec time required:** Outbound is a non-trivial chunk of the 15–20 hours/week per executive. Daily review of agent outputs, weekly retraining, ongoing negative-constraint maintenance.
- **Hiring implication:** "Top-performer SDRs become 'manage 10 AI agents each' at 2–3x comp." The role isn't gone — it's transformed. The $80K email-sender disappears; the $250K agent-manager appears.
- **Failure mode is human, not technical:** 90% of AI SDR deployments fail because operators expected plug-and-play. The technology works; the operator commitment doesn't.
- **The "your outbound already works with humans" gate:** "If your outbound doesn't work with humans, AI won't magically fix it. AI just scales your failure at 10x speed." Don't deploy AI SDR to fix broken positioning, ICP, or messaging.
- **Vendor relationship as ongoing operator work:** "Anytime I have an issue or an idea, I just email the CEO or head of product." This isn't a vendor relationship — it's a partnership maintained by the executive directly.

## Open questions

- What's the org-design implication for the SDR function specifically? If 90% of email-based SDRs are displaced in 12 months (per source's prediction), what does the remaining 10% look like? Do they sit in sales, in RevOps, or in a new "agent operations" function?
- The 60,000 emails and 6.67% response rate are aggregate across all five sub-agents. What's the variance? Which sub-agents are at 12%+ and which are at 2%? Where does the diminishing return curve sit?
- "Did not cannibalise existing inbound" — what's the methodology? Hard to prove counterfactually.
- What's the actual cost of Artisan at SaaStr's scale? Source quotes "$2,000–4,000/month" but unclear if that's per agent, per platform, or per volume tier.
- How does pipeline attribution work when AI sources first-touch but humans close? Source flags this is a problem (Kyle Norton, Windsurf both quoted on attribution breakdown) but doesn't resolve it.

## Raw notes / quotes

### Numbers specific to this surface
- 60,000+ hyper-personalised emails sent
- 3,221 emails/month from single platform (vs. 75–285 from human SDRs = 11–43x)
- 6.67% overall response rate (vs. 2–4% industry)
- Warm campaigns: 5–7% response rates
- Europa 2024 attendees: 12.13% positive response rate
- 15% of SaaStr AI London ticket revenue sold directly via AI SDR
- Six-figure sponsor meeting booked Saturday at 6:02 PM
- $70K autonomous close + $100K New Year's Eve close

### Direct quotes
- "I see people run one campaign for 10,000 leads. No. I max my campaigns to 100–500 leads."
- "Not: 'Hey, have you heard about SaaStr?' Instead: 'Hey, you attended SaaStr Europa 2024, here's what's new for Annual...'"
- "Your human SDRs don't want to do cold outbound to people who don't know you. Neither does your AI agent — because it doesn't have context for why you should be reaching out to this person."
- "It's as important to tell your AI agents what you can't do as what you can do."
- "Bad training: 'Here's our website, here are email templates, go!' Good training: specific proof points from real conversations that worked, detailed objection handling from actual objections received, clear escalation rules."
- "If your outbound doesn't work with humans, AI won't magically fix it."

### Tool stack
- **Artisan** — primary AI SDR platform (cold/warm/event)
- **Salesforce** — single source of truth for context
- **Zapier** — connective tissue back to Salesforce

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/sales/captures/.
Create the folder if it doesn't exist. Commit as 'wiki: capture
saastr-artisan-sdr for ai-gtm-playbook/sales' and push.
```

Then attach the file.
