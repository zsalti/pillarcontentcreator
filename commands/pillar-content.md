---
name: pillar-content
description: Full pipeline for creating impactful pillar content — from strategic briefing through research, drafting, refinement, voice application, and distribution planning. Works with any project's context files.
---

# Pillar Content Creator

A systematic process for creating content that earns the right to exist. Not a writing assistant — a full content product pipeline. Each phase is a gate: you approve before moving forward.

**How to invoke:** Run `/pillar-content` with an optional topic hint, or just run it and answer the briefing questions.

---

## Phase 0: Context Discovery

Before anything else, load the strategic context this content will serve.

Search the repo for these file types using glob patterns:

```
**/icp*.md, **/*icp*.md
**/*persona*.md, **/*buyer*.md
**/*positioning*.md
**/*brand*voice*.md, **/*tone*.md, **/*voice*.md
**/*product*marketing*.md, **/*product*brief*.md
**/*content*pillar*.md, **/*content*strategy*.md
**/*jtbd*.md, **/*jobs*to*be*done*.md
**/*competitor*.md
```

For each file found, read it and extract:
- **ICP:** firmographics, company size, buying signals, team composition
- **Personas:** roles, daily frustrations, KPIs, language they use, what triggers a buying decision
- **Positioning:** value propositions, differentiation, how the brand frames the problem it solves
- **Brand voice:** tone, style rules, forbidden patterns, example writing
- **Content strategy:** existing pillars, topic priorities, buyer journey mapping
- **Product context:** what the product does, who it's for, what it replaces, key proof points

**If no context files are found:**
Report exactly which patterns returned nothing. Then ask the user:

> "I couldn't find [list of missing context types] in this repo. You have three options:
> 1. Point me to the files directly
> 2. Paste the key context into chat (I'll work from that)
> 3. Answer a few quick questions so I can build a working context from scratch
>
> Which works best?"

Do not proceed until you have at minimum: a target audience, a brand voice direction, and a sense of what the brand stands for.

Once context is loaded, summarize what you found in a brief table:

| Context Type | File Found | Key Takeaways |
|---|---|---|
| ICP | ✅ / ❌ | [1-2 sentences] |
| Buyer personas | ✅ / ❌ | [1-2 sentences] |
| Positioning | ✅ / ❌ | [1-2 sentences] |
| Brand voice | ✅ / ❌ | [1-2 sentences] |
| Content strategy | ✅ / ❌ | [1-2 sentences] |

**GATE 0:** Present the summary and ask: "Does this context look right? Anything missing or outdated before we start?"

Wait for approval before proceeding.

---

## Phase 1: Briefing

Get the raw material for the piece. Ask the user directly:

> "Tell me about the content piece you want to create. Give me:
> 1. **Topic / working title** — what's it about? (rough is fine)
> 2. **The main goal** — what should this piece make the reader think, feel, or do?
> 3. **Primary audience** — which persona is this for? (or is it multi-audience?)
> 4. **Any talking points or arguments you already have** — dump everything, even half-formed thoughts
> 5. **Content format** — long-form article, newsletter, video script, whitepaper, LinkedIn post series? (or TBD)
> 6. **Anything you've already tried** — drafts, angles that didn't work, things you want to avoid"

After the user responds, synthesize the briefing into a structured brief:

```
CONTENT BRIEF
Topic: [working title]
Goal: [what this piece must achieve]
Primary persona: [who it's written for]
Format: [content type]
Core argument (your interpretation): [1-2 sentences stating the central claim]
Key talking points: [bulleted list from their dump]
Constraints / avoid: [anything they flagged]
```

**GATE 1:** Present the brief and ask: "Does this brief capture what you're trying to build? Any corrections before I go deep on research?"

Wait for approval before proceeding.

---

## Phase 2: Research

**This is a two-stage process: Research, then Verification.**

### Stage 2A: Deep Research

Run a thorough research pass across multiple angles. Use WebSearch and Firecrawl.

**Source rules — non-negotiable:**
- ✅ Academic papers and peer-reviewed research
- ✅ Industry analyst reports (Gartner, Forrester, McKinsey, Deloitte, PwC, CB Insights, etc.)
- ✅ Government and institutional data (census, labor stats, central bank reports)
- ✅ Reputable journalism (FT, WSJ, The Economist, Reuters, Bloomberg, sector-specific press)
- ✅ Primary research published by universities or independent research firms
- ❌ Vendor whitepapers and case studies (they have selection bias baked in)
- ❌ PR-dressed blog posts with no primary sources
- ❌ Statistics cited without a traceable original source
- ❌ "According to a study..." without naming the study

**Research angles to cover:**

1. **The problem angle** — What's the documented scale, cost, or frequency of the problem this piece addresses? Get hard numbers.
2. **The market angle** — What does the industry/market data say about this space? Trends, growth, shifts.
3. **The human angle** — What research exists on how people (not companies) experience this problem? Psychology, behavior, decision-making.
4. **The failure angle** — What does the data say about what goes wrong, and why?
5. **The contrarian angle** — Is there credible research that complicates or challenges the obvious narrative? Surface it — it sharpens the argument.
6. **The forward angle** — What does the data suggest about where this is heading?

For each finding, record:
```
CLAIM: [the stat or insight]
SOURCE: [publication, author, year, URL]
QUOTE: [exact quotable passage if available]
RELEVANCE: [how this connects to the content brief]
```

Aim for 10-20 substantive findings across the six angles. Depth over breadth.

### Stage 2B: Claim Verification (Sub-Agent)

After Stage 2A completes, launch a **verification sub-agent** with this instruction:

> "You are a fact-checker. I'm going to give you a list of research claims with their stated sources. Your job is to verify each one independently. For each claim:
> 1. Search for the original source and confirm the stat/finding is accurately represented
> 2. Check whether the source is credible and not a vendor or PR publication
> 3. Flag if the claim has been taken out of context or if the methodology is questionable
> 4. Return a verdict: ✅ VERIFIED / ⚠️ QUESTIONABLE / ❌ UNVERIFIED — with a brief explanation for anything that isn't ✅
>
> Here are the claims: [paste all claims from Stage 2A]"

Wait for the verification sub-agent to return. Then:
- Remove all ❌ UNVERIFIED claims
- Flag ⚠️ QUESTIONABLE claims with a note when presenting to the user
- Keep only ✅ VERIFIED claims as the research foundation

Present the verified research as a clean brief:

```
RESEARCH BRIEF
[6 sections, one per angle, each with 2-4 verified findings]

Claims removed after verification: [list ❌ items so the user can see what was cut]
Claims flagged as questionable: [list ⚠️ items with the caveat]
```

**GATE 2:** Share the research brief and ask: "Does the research cover the right ground? Any angles I missed or sources you'd like me to dig deeper on?"

Wait for approval before proceeding.

---

## Phase 3: Find the Right Angle

With context and verified research in hand, develop **4 distinct angles** for the content piece. An angle is not a topic — it's a specific way of entering the story that shapes the entire argument, the emotional register, and what the reader walks away believing.

For each angle, write:

```
ANGLE [#]: [Name / headline-style title]

Entry point: [What's the opening move? What surprising fact, question, or reframe kicks it off?]
Core argument: [The central claim this angle makes in 1-2 sentences]
Why it works for this audience: [Why this persona will lean in — what tension does it activate?]
Research it draws on: [Which 2-3 findings from the research brief does this angle use?]
What the reader believes after reading: [Specific belief shift — not just "they found it interesting"]
Risk / weakness: [What could make this angle fall flat? Be honest.]
```

Angles should be genuinely different — not variations on the same thesis. Consider:
- **Contrarian** — challenges the obvious wisdom the audience currently holds
- **Pattern reveal** — shows a hidden dynamic that's been in plain sight all along
- **Cost of inaction** — makes the status quo viscerally expensive
- **Reframe** — renames the problem in a way that changes how the audience sees it
- **Case in point** — builds from a specific, documented scenario outward to the principle

**GATE 3:** Present all 4 angles and ask: "Which angle feels sharpest? Or is there a combination worth exploring? Pick one and I'll build from there."

Wait for approval and a selected angle before proceeding.

---

## Phase 4: Draft

Write the first draft based on the approved angle, verified research, and content brief.

**The draft is a prototype. Its job is to get the argument on paper — not to be good yet.**

Drafting rules:
- Follow the approved format (article, newsletter, script, etc.)
- Use the verified research — no invented stats, no paraphrased claims without source fidelity
- Structure the argument so each section earns the next (reader shouldn't be able to skip a section without losing the thread)
- Prioritize substance over style at this stage — voice comes later
- Write to the specific persona identified in the brief, not a generic reader
- Be specific: concrete examples beat abstract principles every time

End the draft with a **self-critique note:**
```
DRAFT SELF-CRITIQUE
Strongest section: [which part lands best and why]
Weakest section: [which part feels thin or off — be honest]
Argument gaps: [anything the reader could reasonably push back on that isn't addressed]
Missing specificity: [anywhere the draft is too vague or generic]
```

**GATE 4:** Share the draft plus self-critique and ask: "What's your read? What's working, what isn't? I'll hold off on any edits until you've weighed in."

Wait for feedback before proceeding.

---

## Phase 5: Iteration and Refinement

This is where the prototype becomes a content product.

Run the draft through three passes:

### Pass 1: Argument Stress-Test

Ask these questions of every major claim in the draft:
- What's the strongest objection a skeptical reader would raise here?
- Is the evidence actually proving what the argument says it proves?
- Are there counter-examples the draft ignores?
- Does each section logically follow from the one before?
- Is the conclusion earned by the argument — or does it outrun the evidence?

Identify every weak point and either fix it (strengthen the argument/evidence) or cut it (if it can't be fixed, remove it).

### Pass 2: Sharpening Pass

Go sentence by sentence through the draft and apply:
- **Cut what's soft:** Remove any sentence that hedges, over-explains, or restates what the previous sentence already said
- **Sharpen the verbs:** Replace passive constructions and weak verbs with direct ones
- **Kill the scaffolding:** Remove phrases like "In this piece, I'll show you..." or "As we've seen above..." — just do the thing
- **Tighten transitions:** Each paragraph should connect to the next without a bridge sentence that telegraphs the connection
- **One idea per paragraph:** If a paragraph is doing two jobs, split it

### Pass 3: Copy Check

Run the refined draft through the standard copy check. See `.claude/references/content-copy-check.md` if present in the repo — use it verbatim. If not present, apply:

**Minimum checks:**
- Forbidden terms scan: "transformational," "synergy," "leverage" (as verb), "best-in-class," "world-class," "cutting-edge," "circle back," "touch base," em dashes
- ICP parameter language: never write raw firmographic filters (revenue ranges, headcount numbers) in reader-facing copy — naturalize them
- Substance check: every claim is backed by experience, data, or specific example — no invented stats
- "So what?" test: why should a busy [persona] care about each section?
- Over-explanation check: if a metaphor lands, stop — don't explain what it means

Present a final **REFINED DRAFT** with a brief changelog noting what was cut and why.

**GATE 5:** Share the refined draft and ask: "Does this feel tighter? Any remaining sections that need more work before we move to hooks?"

Wait for approval before proceeding.

---

## Phase 6: Hooks

Brainstorm **8-10 hook variations** for the content piece. A hook is the first contact point — the first sentence of an article, the subject line of a newsletter, the opening line of a social post. It determines whether anyone reads the rest.

For each hook, note:
- The **hook type** (see list below)
- The **hook text** (just the opening — 1-2 sentences max)
- Why it **earns the click** for this specific persona

**Hook types to cover:**
- **The counterintuitive stat** — a number that breaks the reader's assumed model
- **The uncomfortable question** — directly asks something the reader doesn't want to face
- **The specific failure** — a named, specific scenario that mirrors the reader's reality
- **The reframe** — describes a familiar problem in a way the reader hasn't heard before
- **The hidden cost** — makes the price of inertia vivid and concrete
- **The confession** — starts with a vulnerable or honest admission that builds trust
- **The bold claim** — stakes out a clear, specific position that might be controversial
- **The paradox** — juxtaposes two things that shouldn't be true at the same time
- **The "most people" pattern** — opens by naming a common behavior and immediately questioning it

After presenting all 8-10, flag the top 2-3 that you think best fit the approved angle and audience.

**GATE 6:** Ask: "Which hooks land for you? Pick 1-2 favorites. I'll weave the strongest hook into the final version."

Wait for selection before proceeding.

---

## Phase 7: Brand Voice Application

Rewrite the refined draft in the brand's full voice and style. This is not cosmetic — voice is how the brand earns trust. A piece that says the right things in the wrong voice loses anyway.

**How to approach this:**

1. Re-read the brand voice file from Phase 0 (or the voice notes from the user's context)
2. Identify the 3-5 most specific voice traits that apply to this format (e.g., parenthetical asides, short-sentence punches, casual collective language, direct address, stance-taking)
3. Rewrite section by section — not word by word. Preserve every argument, data point, and example from the refined draft. Voice should add texture, not replace substance.

**Voice rewrite rules (universal):**
- Substance first: if the voice rewrite hollows out the argument, that's a failure — not a feature
- Do not over-explain after a metaphor or example lands
- Use direct address ("you," not "brands" or "companies")
- Vary sentence rhythm: short punchy sentences + longer explanatory ones
- If the brand has a list of forbidden terms/phrases — honor it completely
- The reader should be able to hear a real human thinking, not a polished AI

Run the voice draft through the copy check one more time (focus on Sections A, B, C from the check, or equivalent if using your own checklist).

**GATE 7:** Share the voice draft and ask: "Does this sound right? Is there anything that still feels off-brand or too generic?"

Wait for approval before proceeding.

---

## Phase 8: Launch Plan

A great piece distributed casually loses to a mediocre piece distributed with intent. Plan the launch before anything is published.

Build a **Content Launch Brief** with these sections:

### 8A: Asset Inventory
What does this piece produce?
- Primary asset: [the piece itself — format, length, where it lives]
- Secondary assets: [what can be extracted — key stats, pull quotes, frameworks, charts]
- Derivative formats: [what can be repurposed — LinkedIn posts, short video, email snippet, slide deck, carousel]

List each asset with a one-line description. These become the distribution fuel.

### 8B: Distribution Channels
Map each channel to the right asset:

| Channel | Asset | Timing | Notes |
|---|---|---|---|
| [e.g., Newsletter] | [Primary piece] | [Day 0] | [e.g., full text or excerpt + link] |
| [e.g., LinkedIn] | [3 derivative posts] | [Day -3, Day 0, Day +7] | [teaser / launch / insight excerpt] |
| [e.g., Website/blog] | [Full piece] | [Day 0] | [SEO-optimized version] |
| [e.g., Partner share] | [Excerpt + link] | [Day +1] | [identify partners in advance] |
| [e.g., Podcast/video] | [Adapted script] | [Day +14] | [if applicable] |

Fill this out specifically for the brand's actual channels. Do not leave placeholders — ask the user which channels they actively use if unclear.

### 8C: Pre-Launch Teasing
Plan 2-3 pre-launch social touchpoints (typically 3-7 days before launch):
- **Tease 1:** [What angle do you surface before the piece is live? A provocative stat? A question?]
- **Tease 2:** [A related observation or mini-insight that primes the audience]
- **Tease 3 (optional):** [Behind-the-scenes, a strong pull quote, or a visual from the piece]

Write the actual copy for each tease — not a description of it.

### 8D: Launch Day Sequencing
Hour-by-hour or platform-by-platform plan for launch day:
- What goes out first (and why)
- What fires next
- Who should amplify (team, partners, advocates) — and what you're asking them to share

### 8E: Re-Launch Triggers
A piece isn't a one-time event. Define the conditions under which this piece gets re-launched:
- [ ] New data is published that strengthens or updates the argument
- [ ] A major news event makes the topic suddenly more relevant
- [ ] X months have passed since original launch — topic is cyclically relevant
- [ ] Piece is updated with a new section, new case, or new framing
- [ ] Repurposed into a new format (e.g., article → video → slide deck)

For each trigger, note: what changes in the piece, and which channels get the re-launch push.

**GATE 8 (Final):** Share the launch brief and ask: "Does the launch plan feel right? Any channels missing, or timing that needs adjusting? Once you confirm, I'll produce the final deliverable package."

Wait for approval before proceeding.

---

## Final Deliverable Package

Once all gates are approved, produce a single consolidated file named `[YYYY-MM-DD]-[topic-slug]-content-product.md` (using today's date) containing:

1. **Content Brief** (from Phase 1)
2. **Verified Research Brief** (from Phase 2, clean version)
3. **Final Draft** (voice-applied, from Phase 7)
4. **Hook Options** (top 3, from Phase 6)
5. **Launch Brief** (from Phase 8)

Label each section clearly. This file is the full content product — briefing to launch plan — in one place.

---

## Critical Rules

- **Never fabricate stats or claims.** Every data point must trace to a real, verifiable source. If you can't verify it, remove it.
- **The draft is a prototype, not the deliverable.** Don't rush to "done" — push through all the gates.
- **Voice rewrites must preserve substance.** If personality is added at the expense of argument, the rewrite failed.
- **Each gate is real.** Do not auto-proceed from one phase to the next without explicit user approval.
- **Research agent and verification agent are separate passes.** Don't merge them — the verification is an independent check, not a self-review.
- **Distribution is not an afterthought.** A piece without a launch plan isn't finished.
