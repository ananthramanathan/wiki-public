# Capture: Kieran Flanagan — The 4 .md Files (Foundation Layer Spec)
_Captured: 2026-04-27_
_Source: "The 4 .md Files That Turn Claude Code Into a Marketing Machine," Kieran Flanagan, Substack (The AI Marketing Generalist), 3 April 2026_
_Topic: ai-gtm-playbook → marketing_

## Pattern note
Marketing-OS shape, not worker-agent shape. Same routing as the Barona capture — files here for now, promote to a `marketing-os/` surface when there's a non-OS marketing capture that justifies the split.

This piece is reference-shaped, not implementation-shaped. Kieran articulates the foundation layer; he doesn't show a deployed system the way Barona does. Other captures crediting Kieran's framework will be measured against this file.

Note on universality: framework is marketing-context. Kieran is B2B/B2C marketing-focused. Lemkin comes at GTM from sales-led B2B with many touchpoints. Future PLG-angle captures likely add a third lens. None of these is the universal spine — GTM motion is context-dependent (B2C: product → marketing → sales; enterprise: sales → marketing → product). Treat Kieran's four files as one well-articulated foundation pattern, not the foundation pattern.

## What this is
Kieran Flanagan's spec for the foundation layer of a Claude Code marketing system. Four .md files he's identified as the starting set that any marketer or marketing team should build before writing skills. Lives in a `/foundation/` directory; every skill reads from it before executing. The piece is the canonical articulation — Kieran is the originator other captures (Barona, etc.) credit.

## How it works

### The four files

**1. Audience Delight Profile** — replaces traditional ICP
- ICPs are written for slide decks ("Decision-maker at 200-500 person SaaS, VP level, cares about pipeline efficiency"). Useless for an AI agent writing content.
- Audience Delight captures: what makes the audience light up, what they share unprompted, what they complain about, **the actual vocabulary they use**.
- Vocabulary section is the load-bearing part. Concept × "they say" × "they don't say."
- Notion example: workspace = "my Notion / my setup / my system" (NOT "the platform / the solution"); organization = "second brain / single source of truth" (NOT "knowledge management system"); tool fatigue = "tab hell / context switching" (NOT "technology stack consolidation").
- Build by feeding Reddit threads, sales call transcripts, support tickets, competitor comment sections to Claude. Replicate from their language, not the marketing department's.

**2. Creator Style** — replaces brand voice guidelines PDF
- Traditional style guides are aspirational and vague ("warm, professional, empowering"). Apply to anyone.
- Creator Style is extracted **empirically** from best-performing content. Patterns, not adjectives.
- Instead of "we're conversational" → "short sentences lead, longer sentences follow to explain, fragments welcome for punch, rhythm alternates staccato then flow."
- Instead of "we're empowering" → "always lead with what the user can do, not what we built."
- Most powerful section: "Sounds Like Us vs. Doesn't Sound Like Us" with actual side-by-side phrases. Calibration examples, not vibes.
- Notion sounds-like: "Build your own CRM. Or a wiki. Or a project tracker. Or all three." / Notion doesn't-sound-like: "Notion offers comprehensive project management capabilities."
- Build by gathering 10 best-performing pieces, asking Claude to describe voice/tone/patterns observed, validating that the description matches the winners but NOT the losers.

**3. Market Positioning Map** — replaces quarterly positioning slide
- Most companies treat positioning as point-in-time. Offsite, deck, referenced once, forgotten.
- This is a **living .md file** tracking what competitors currently claim, contested vs. owned territory, white space, market shifts.
- Three territories:
  - **Owned** — positions competitors can't credibly claim (Notion: "flexibility without complexity," community-driven ecosystem)
  - **Contested** — multiple players claiming the same thing ("all-in-one workspace," "AI-powered" — when everyone claims it, no one owns it)
  - **Ceded, intentionally** — positions you've decided not to fight for (Notion ceded deep PM methodology to Asana). Knowing what you don't claim is as important as what you do.
- Read by any skill involving launch messaging, competitive differentiation, content that stakes a claim. Prevents AI from positioning the brand in territory it doesn't own, or missing territory it does.
- Build by auditing competitor homepages monthly, reading G2 reviews for customer comparison language, reviewing win/loss data. Update monthly — markets move faster than quarterly decks.

**4. Customer Journey Intelligence** — replaces the funnel diagram
- Traditional journey maps describe stages. They don't capture where people actually convert, stall, or leave.
- This file captures real mechanics: how people find you, what questions they ask during evaluation, what proof points close deals, where they get stuck, what triggers expansion.
- Most journey maps focus on what you want the customer to do. This focuses on **what the customer actually does, including where they stall**.
- Notion examples: #1 stall = "blank canvas paralysis" (sign up, see empty workspace, don't know where to start); #1 churn reason = "team adoption failure" (one champion builds, nobody else uses it).
- Conversion triggers: "aha workspace moment" (2-5 hours of real use); "colleague already using it"; "template that matches their use case"; "storage or guest limits hit."
- Read by nurture email skills, ad copy skills, anything that needs to address real friction. Without it, output is generic "here's what you can do with [product]." With it, output addresses blank canvas anxiety with a 2-minute template.
- Build from analytics (conversion paths, drop-off), sales call recordings (objections that close vs. kill), customer interviews ("walk me through how you found us and decided to buy").

### The selective-loading mechanism

This is the architectural detail that makes the system work.

**Every foundation file has a header declaring when it should be loaded:**
```
Load this file when the skill: writes any content — blog posts, social copy, 
emails, landing pages, ad copy, or any output that produces words.

Do NOT load this file when the skill: only needs audience data, only needs 
competitive positioning, or only needs the buyer's path.
```

**Every skill includes this generic instruction block:**
```
Step 1: Load Foundation Context. Scan ./foundation/ for all .md files. For 
each file, read ONLY the header block (everything above the first ---). 
Check the "Load this file when" line against this skill's task. Load the 
full file ONLY for files where the criteria match. Skip all others.
```

That's it. Intelligence lives in the files, not the skills. Build a new skill, paste the same block, foundation files route themselves.

### Loading examples Kieran gives
- LinkedIn post skill → Audience Delight + Creator Style
- Product launch messaging skill → Market Positioning + Customer Journey
- Nurture email sequence → Audience Delight + Customer Journey + Creator Style

### The compounding claim
Every update at the foundation level improves every skill that reads that file. You don't improve one skill at a time — you improve the system at the foundation level. Add a 5th file next month, every existing skill picks it up if relevant.

## What's distinctive

1. **The four files replace four traditional marketing artefacts.** ICP, voice guidelines, positioning deck, funnel diagram. Each replacement is an argument that the traditional artefact was built for humans reading slide decks, not for AI agents producing content. The architecture forces a re-derivation of marketing fundamentals from "what does the AI need to know to produce good output."

2. **Vocabulary as primary, not secondary.** The Audience Delight file's vocabulary section is the part Kieran flags as transformative. "Get the vocabulary wrong, and your content sounds like a vendor. Get it right, and it sounds like a peer." Most ICP work treats language as decoration. Kieran treats it as the substance.

3. **Empirical voice extraction.** Creator Style isn't written, it's *derived*. From the 10 best-performing pieces. The validation test: does the description match the winners but NOT the losers? Inverts the conventional brand-voice exercise (write aspirations, hope content matches).

4. **Positioning as living document.** "Update monthly — markets move faster than quarterly decks." This is a workflow claim, not just a content claim. The artefact is only useful if the cadence is fast enough.

5. **The selective-loading mechanism.** "Like imports in code — you don't import *." This is the engineering pattern that makes the foundation layer scalable. Without it, foundation files clog context as the library grows. With it, each skill pulls only what it needs.

6. **Pixar Braintrust as the framing.** Kieran opens with Pixar's near-failure on Toy Story → Catmull's Braintrust → Disney's same animators producing Frozen/Big Hero 6/Zootopia. The argument: same talent + new shared context = better outcomes. Foundation files are the marketing team's Braintrust.

## Why this purpose matters
For an operator in learning mode (not execution): this is the canonical articulation of one specific framework for AI-marketing foundations. Worth knowing in detail because (a) future captures will reference it, (b) it's well-thought-through enough to copy or adapt, and (c) the selective-loading pattern is reusable beyond marketing.

For eventual execution: useful when there's a company to apply it to. The framework's strength is concreteness (specific files, specific headers, specific build instructions). Its limitation is marketing-context — applying it directly to sales or PLG would require translation.

## Pros / cons as the source presents them

### Pros (claimed)
- Foundation-first beats skill-first; skills built on foundation produce specific, on-voice output
- Selective loading prevents context bloat as foundation library grows
- Compounding: foundation updates improve every dependent skill
- Empirical extraction (winners + losers) is more reliable than aspirational style guides
- "Living document" cadence keeps positioning current
- Vocabulary calibration moves output from "vendor sounding" to "peer sounding"

### Cons / what isn't addressed
- Maintenance cost as foundation grows — who owns updating the four files monthly?
- Validation: how do you know the empirically-extracted Creator Style is right when the next 10 winners arrive?
- Single-author risk: Kieran built this, his audience is following his lead, but the framework hasn't been stress-tested across many independent implementations yet
- Generalisability: explicitly marketing-context. Doesn't claim universality, but readers may overgeneralise.
- The "table stakes within 12 months" claim (made by Vahaaho-Pesola crediting this same framework) isn't validated here either way
- No discussion of tool lock-in (Claude Code-specific) or migration if the stack changes

## Cross-cutting principles this surfaces

### Foundation-first sequencing
Not just for marketing OS. The same logic applies to any agentic system: the curated context is the moat, the AI is interchangeable. Cross-applies cleanly to the SaaStr stack ("Salesforce as single source of truth," Momentum/Attention as the truth-keeping layer) — different domain, same architectural principle.

### Selective context loading
The "import only what you need" pattern is generalisable. Worth tracking whether other captures use equivalent mechanisms. Lemkin's 10K v2 effectively does this through Zapier-piped data flows; Kieran formalises it at the file-header level.

### Empirical over aspirational
Creator Style is derived from best-performing content, not written. This pattern — extract from what works, validate against what doesn't — is reusable for any content style guide, sales playbook, or RevOps process documentation.

## Operator-relevant signal

- **Concreteness is the value.** Most "build an AI-first marketing org" advice is abstract. Kieran's piece tells you the four specific files, the headers they need, the loading mechanism. For an operator in learning mode, this is the level of specificity worth absorbing.
- **The selective-loading pattern is the most portable idea.** Even if you never use Kieran's four specific files, the "header declares when to load, skill scans headers, loads only matches" mechanism is reusable for any context-heavy system. Worth internalising independently of the marketing application.
- **The four-file set is a starter, not a finished spec.** Kieran says "these 4 files are a great starting layer." Implication: real systems will accumulate more foundation files over time. The architecture has to support growth — which is why the selective-loading mechanism matters.
- **Not the spine, but a strong reference for one surface.** Per the routing note above, this is one well-articulated foundation pattern for marketing OS specifically. When other surfaces (sales OS, product OS, RevOps OS) get captures, they'll need their own foundation specs. Cross-applying Kieran wholesale would be a mistake.
- **The "vocabulary moat" is the most underrated insight.** Most operators won't have done the work to capture how their audience actually speaks. The Audience Delight vocabulary section is where new marketing-OS implementations will most often fail (or skip).

## Open questions

- How does Kieran's foundation layer handle conflicts? E.g., Audience Delight says the audience uses "second brain" but Creator Style says we don't use that phrase — which wins?
- What does the file header structure actually look like in full? The piece shows the "Load when / Do NOT load when" lines but doesn't show the full template.
- How is the foundation layer versioned? If positioning shifts mid-quarter, does the file get rewritten in place or versioned with date suffixes?
- The Audience Delight file is built from "Reddit threads, sales call transcripts, support tickets, competitor comment sections" — what's the volume threshold? 10 threads? 100? 1000?
- Creator Style is built from "10 best-performing pieces" — what's "best-performing" measured by? Engagement? Conversion? Pipeline?
- Cross-skill conflict: if a LinkedIn post skill and an email skill both load Audience Delight, do they produce consistent output? What if they don't?
- How does this handle multi-product companies where positioning varies by product line?
- How does the foundation layer evolve when the company evolves? Brand pivots, new ICPs, new markets — how is the layer maintained without becoming a graveyard of stale context?

## Raw notes / quotes

### The Pixar/Braintrust framing
- Pixar nearly didn't finish Toy Story (1995). Story kept breaking. Same problem hit different teams on different films. "Every film starts from zero. The lessons lived in individual directors' heads; there was no shared system."
- Catmull's fix: Braintrust — shared creative intelligence layer where directors screened work-in-progress and drew on collective context.
- Disney acquired Pixar 2006. Catmull exported Braintrust to Disney as "Story Trust." Same animators, same budgets, same studio that had been making bad film after bad film → produced Frozen, Big Hero 6, Zootopia.
- "Same talent. New system. Better outcomes."
- "Catmull's insight wasn't 'hire better directors.' It was 'give them shared context and let them create.'"

### The skills-without-foundation failure mode
- "They build skills in LinkedIn post writing, newsletter drafting, and ad copy generation. Each skill is good. Each skill works. But each skill starts from zero every time. No shared understanding of the audience. No consistent voice. No awareness of the competitive landscape. No memory of what converts and what doesn't."
- "The output is... fine. Generic. Interchangeable with any other SaaS marketer's content."

### What makes foundation files different from CLAUDE.md
- "Not CLAUDE.md (the system configuration file everyone's already talking about). These are different. These are files the marketer creates, about their audience, their voice, their market, their buyer's journey."
- Stored in `/foundation/` directory. Every skill reads from them before executing.

### Direct quotes worth preserving
- "Get the vocabulary wrong, and your content sounds like a vendor. Get it right, and it sounds like a peer."
- "It captures patterns, not adjectives."
- "When a skill reads this, it has concrete calibration. Patterns it can match against, not vibes it has to interpret."
- "Knowing what you don't claim is as important as knowing what you do."
- "Most journey maps focus on what you want the customer to do. This file focuses on what the customer actually does. Including where they stall."
- "Selective loading. Like imports in code — you don't import *."
- "The intelligence lives in the files, not in the skills."
- "You don't improve one skill at a time. You're improving the entire system at the foundation level."

### File structure (verbatim from post)
```
/foundation/
  audience-delight.md
  creator-style.md
  market-positioning.md
  customer-journey.md
```

### The header pattern (verbatim)
```
Load this file when the skill: [criteria for loading]

Do NOT load this file when the skill: [criteria for skipping]
```

### Stack
- Claude Code (the runtime)
- `/foundation/` directory (markdown files)
- Skills layer (lives elsewhere in the repo, reads from foundation)
- CLAUDE.md (separate; system configuration, not foundation context)

### Author context
Kieran Flanagan, Substack: "The AI Marketing Generalist." B2B/B2C marketing focus. Position is foundation-first thinking applied to Claude Code marketing systems. Has built a name in this space over the last ~18 months.

---

To file this, ask Ace:

```
Drop this capture into system-architectures/ai-gtm-playbook/marketing/captures/.
Commit as 'wiki: capture kieran-foundation-files for 
ai-gtm-playbook/marketing' and push.
```

Then attach the file.
