# LifeOS — Master Build Plan

**Owner:** Founder + team
**Version:** v0.1
**Date:** 23 May 2026
**Status:** Active — kick-off Monday
**Related docs:**
- [LifeOS v1 Product Spec](./LifeOS-v1-Product-Spec.md)
- [LifeOS Interview Questions](./LifeOS-Interview-Questions.md)
- LifeOS Build Dashboard *(interactive artifact)*

---

## Purpose

This is the master execution plan for LifeOS. It turns the v1 Product Spec into sequenced work over twelve months. Every action that needs to happen — across product, design, engineering, research, operations, and go-to-market — lives somewhere in this plan.

The plan is paired with two companion artifacts that you should keep open alongside it:

1. **LifeOS Build Dashboard** — the interactive day-to-day UI. Each todo there maps to a workstream below; clicking a todo reveals the detailed plan content.
2. **LifeOS Interview Questions** — the field guide used in the Phase 0 research workstream.

The three documents are deliberately connected. The plan is the source of truth, the dashboard is how you work the plan daily, the interview guide is how you execute one specific workstream.

---

## How to read this plan

The plan is organized in seven phases over twelve months. Each phase has:

- A **goal** (one sentence).
- **Workstreams** — parallel tracks of work, each with an owner role.
- **Deliverables** — concrete outputs that prove the phase is done.
- **Success criteria** — measurable signals that the phase succeeded.
- **Risks** — what could go wrong, and how we'll notice early.

Phases compound. Skipping work in Phase 0 to "save time" causes pain in Phase 3. The plan resists the urge to start coding before the riskiest assumptions are validated.

---

## Phase 0 — De-risk before build (Week 1)

**Goal:** Resolve the three questions that decide whether this product is worth building — *can we own the name*, *do enough people want it*, and *does the technology actually work for our users*.

### Workstream 0.1 — Lock the name (Trademark + Domain)

- **Owner:** Operations or founder (non-technical).
- **Duration:** 2 days (Mon–Tue of Week 1).
- **Activities:** Run "LifeOS" through trademark databases — USPTO (US), EUIPO (Europe), Indian Trademark Registry. Check domain availability across `lifeos.com / .app / .io / .ai`. If "LifeOS" is unavailable or weakly protectable, fall back to the Section 16 shortlist (Cortex / Trace / Index / Loop / Ground) and repeat checks for the chosen alternative.
- **Success criteria:** Name confirmed available in target markets, primary domain secured (or strong alternative locked in).
- **Deliverable:** One-page decision doc with screenshots of search results and the final name + domain.
- **Risk:** "LifeOS" is descriptive enough that some variant is taken. Have Plan B and Plan C ready before Monday morning so we don't lose a day.

### Workstream 0.2 — Validate the moment (User interviews)

- **Owner:** Founder + designer.
- **Duration:** 5 days (Mon–Fri of Week 1).
- **Activities:** Recruit and conduct 15 user interviews across diverse archetypes — founders (3), sales reps (3), students (3), consultants (3), doctors / therapists / lawyers (3). Use the LifeOS Interview Guide. Record with consent, take notes, synthesize daily so patterns appear by mid-week.
- **Success criteria:** Clear signal on whether the "meeting moment" from Section 2 of the spec is genuinely universal, or whether one segment is dramatically more underserved than the rest. By interview ten, patterns must be visible.
- **Deliverable:** Synthesis doc with top 5 themes, top 5 verbatim quotes, segment heatmap, and a *go / pivot / kill* recommendation for v1.
- **Risk:** Confirmation bias — founders hear what they want to hear. Mitigation: the designer asks the cold follow-up questions; the engineer doing the technical spike sanity-checks the synthesis.

### Workstream 0.3 — Prove transcription quality (Technical spike)

- **Owner:** One senior engineer.
- **Duration:** 5 days (Mon–Fri of Week 1).
- **Activities:** Record 10 meetings spanning the conditions LifeOS must handle — 3 Indian-English Zoom calls, 2 Hindi-English code-switched calls, 2 noisy in-person meetings (mic only), 2 US-English video calls, 1 lecture/monologue. Run each through Deepgram Nova-2, AssemblyAI Universal-2, and Whisper-large-v3. Hand-label a 5-minute segment from each meeting and compute Word Error Rate (WER) per provider per condition.
- **Success criteria:** At least one provider achieves <8% WER on Indian English specifically, and <10% on Hindi-English code-switching. If none does, this is a v1-killing problem and we replan.
- **Deliverable:** One-page comparison table + recommendation memo + the 10 recordings + transcripts retained for later regression testing.
- **Risk:** All three providers are weak on Indian English. Fallback: fine-tune our own model (~6–8 weeks added to v1). The whole point of the spike is to discover this in Week 1, not in Month 3.

### Phase 0 — gate

End of Week 1, the founder makes a *go / pivot / kill* call based on the outputs of all three workstreams. Do not start Phase 1 until this call is made explicitly and documented.

---

## Phase 1 — Synthesize and design (Weeks 2–3)

**Goal:** Turn validated insight into a buildable design and a tight engineering plan.

### Workstream 1.1 — Spec revision

- **Owner:** Founder + designer.
- **Duration:** 3 days at the start of Week 2.
- **Activities:** Review the v1 Product Spec against Phase 0 interview findings. Edit ruthlessly. Tighten or expand the anti-scope. Update the "default note template" if interviews showed one template doesn't fit all archetypes.
- **Deliverable:** Spec v0.2, signed off by team.
- **Success criteria:** No section of the spec contradicts what users said.

### Workstream 1.2 — Low-fidelity wireframes

- **Owner:** Designer.
- **Duration:** Week 2 (5 days).
- **Activities:** Wireframe the six screens in Spec Section 7.3 — Home/Library, Meeting view, Live overlay, Global chat, Pre-meeting prep card, Settings. Paper or Figma. No visual polish — focus on flow and information hierarchy.
- **Deliverable:** Wireframe deck reviewed with engineering and founder.
- **Success criteria:** Each wireframe can be explained in one sentence; flows tested against the daily journey in Spec Section 7.2.

### Workstream 1.3 — Technical architecture doc

- **Owner:** Lead engineer.
- **Duration:** Week 2 (5 days, in parallel with wireframes).
- **Activities:** Document the v1 architecture: client (Electron or native Mac), backend services (ingestion, transcription pipeline, LLM service, vector store, graph store), data model for the knowledge graph, choice of ASR / LLM / embeddings / DB. Build vs buy decisions documented.
- **Deliverable:** 5–10 page architecture doc with diagrams.
- **Success criteria:** Two engineers reading it independently can sketch the same system.

### Workstream 1.4 — Mid-fidelity mockups

- **Owner:** Designer.
- **Duration:** Week 3 (5 days).
- **Activities:** Take wireframes to mid-fi in Figma — real type, real grid, real component states. Empty states, loading, error, success. Not yet pixel-perfect.
- **Deliverable:** Figma file shared with engineering.
- **Success criteria:** Engineering can estimate the build from the file.

### Workstream 1.5 — Beta user recruitment kick-off

- **Owner:** Founder.
- **Duration:** Starts Week 3, continues for months.
- **Activities:** Begin building the list of 100 private-beta users. Mix of archetypes (5 founders, 5 sales reps, 5 students, 5 consultants, 5 medical/legal, etc.). Start with personal network, expand outward. Capture them in a CRM or simple spreadsheet with archetype, willingness-to-pay signal, calendar booking link.
- **Deliverable:** Running beta list, target of 30 confirmed by end of Phase 2.
- **Success criteria:** People are saying yes to "we'll let you try it in 3 months" — that itself is a validation signal.

---

## Phase 2 — Engineering kick-off (Week 4)

**Goal:** Translate the design and architecture into a sequenced engineering plan with clear ownership.

### Workstream 2.1 — Epic breakdown

- **Owner:** Lead engineer + founder.
- **Duration:** 2 days at the start of Week 4.
- **Activities:** Break v1 into 6–10 engineering epics. Each epic has a name, a one-paragraph description, a rough effort estimate (S / M / L / XL), and a dependency map. Likely epics: Audio capture (Mac), Transcription pipeline, Structured note generation, Meeting view UI, Library / search UI, Global chat, Knowledge graph data layer, Onboarding, Settings, Telemetry.
- **Deliverable:** Epic doc with estimates and dependency graph.
- **Success criteria:** Total estimate is within 10% of the 4-month v1 budget. If it's 6 months, scope is cut in this meeting.

### Workstream 2.2 — Stack and infrastructure setup

- **Owner:** Lead engineer.
- **Duration:** Week 4 (3 days, in parallel).
- **Activities:** Provision cloud accounts, set up CI/CD, repo conventions, error tracking, secrets management, observability baseline. Lock in vendor accounts (ASR, LLM, vector DB, payments processor for later).
- **Deliverable:** "Hello world" deployment from a developer machine to staging.

### Workstream 2.3 — Engineering hiring (if needed)

- **Owner:** Founder.
- **Duration:** Week 4 onward.
- **Activities:** Confirm the team can deliver the epics within the 4-month budget. If not, identify gaps and start hiring or contracting now. Don't start month two understaffed.
- **Deliverable:** Confirmed team roster with each epic mapped to an owner.

### Workstream 2.4 — Design system v1

- **Owner:** Designer.
- **Duration:** Week 4 (5 days).
- **Activities:** Define type scale, colour, spacing, basic components (button, input, card, modal, transcript bubble, action item row). Keep it minimal — extend later when needed.
- **Deliverable:** Figma library file + a Storybook (or equivalent) skeleton in code.

### Phase 2 — gate

End of Week 4: epic plan exists, team is staffed, design system is bootstrapped, infrastructure is ready, beta list is growing. Engineering can now start building epics in Month 2.

---

## Phase 3 — Build v1 (Months 2–4)

**Goal:** Ship a polished private beta of the Notes module — Granola-equivalent feature parity plus knowledge graph foundations — on Mac.

### Build sequencing

Build in this order. Resist the urge to parallel-stream more than the team can review.

**Month 2:**
- Audio capture (Mac, ScreenCaptureKit + Core Audio).
- Transcription pipeline (streaming, with diarization).
- Knowledge graph data layer (Postgres tables for nodes + edges + provenance).
- Skeleton app shell — sign-in, home, settings.

**Month 3:**
- Structured note generation (the default template).
- Meeting view UI (two-pane: structured note + transcript).
- Entity extraction running silently after each meeting.
- Search (full-text + semantic).
- Live overlay during meetings.

**Month 4:**
- Pre-meeting prep flow + calendar integration (read-only).
- Meeting chat (single-meeting scope).
- Global chat (cross-meeting scope).
- Share / export.
- Onboarding flow + polish.

### Cross-cutting workstreams during Months 2–4

- **Quality bar enforcement:** Hallucination rate <1%, time-to-note <60s median. Measure weekly; if either regresses, stop feature work until restored.
- **Internal dogfooding:** Every team member uses LifeOS for their real meetings starting Month 3. Track bugs in a single channel.
- **Beta list growth:** Founder keeps recruiting. Target 100 confirmed users by end of Month 4.

### Phase 3 — gate

End of Month 4: v1 build is feature-complete, dogfooded by the team for ≥4 weeks, hallucination + transcription targets met on internal data. Ready to ship to private beta.

---

## Phase 4 — Private beta (Month 5)

**Goal:** Validate that v1 delights real users — not just the team. Find the rough edges and the magic moments.

### Workstreams

- **Onboarding wave 1:** 25 users in Week 1 of Month 5. Hand-onboarded; one-to-one Loom or call with each. Watch them install, record, review.
- **Onboarding waves 2–4:** 25 more users each subsequent week. By end of Month 5, all 100 are on.
- **Telemetry + feedback:** Instrument everything from Spec Section 13.1. Run weekly user interviews — 5 per week, rotating.
- **Bug triage:** Daily standup focused on user-reported issues. Fix bar: any "this is wrong" report from a user triages within 24 hours.

### Phase 4 — gate

End of Month 5: ≥70% of beta users have recorded ≥3 meetings, ≥40% have used global chat at least once, ≥1 magic-moment story per archetype. If those numbers aren't hit, v1.5 build pauses until we understand why.

---

## Phase 5 — Build v1.5 (Months 5–7, overlaps Phase 4)

**Goal:** Make the cross-tab thesis real — Todo and Expense modules, plus Windows support — so public launch has a story bigger than "another meeting notes app."

### Workstreams

- **5.1 — Todo tab.** Action items extracted from meetings become first-class todos. Add manual todo creation (not all todos come from meetings). Filter by source meeting, by person, by due date.
- **5.2 — Expense tab.** Amount entities mentioned in meetings become pending expense entries. Manual entry too. Simple categorization. Monthly view.
- **5.3 — Windows port.** Match Mac feature parity. Audio capture via WASAPI.
- **5.4 — Entity resolution UI.** Let users merge duplicate people / projects / topics.
- **5.5 — Pricing infrastructure.** Payments (Stripe), free vs Pro tiers, India pricing (₹599 Pro), trial logic.

### Phase 5 — gate

End of Month 7: v1.5 is shippable. Pricing works in production. Three modules live, talking to each other via the graph.

---

## Phase 6 — Public launch (Month 7)

**Goal:** Move from invite-only to open, with a story strong enough to earn organic attention.

### Workstreams

- **6.1 — Marketing site.** One-page site. The Section 12.2 positioning line above the fold. Three screenshots. Pricing. Privacy. Trust signals.
- **6.2 — Launch motion.** Product Hunt, Hacker News, Indian product communities, founder Twitter, target subreddits. Coordinated day.
- **6.3 — Content seeding.** 3 long-form posts pre-written: the "one-app thesis," "how we built the graph layer," "the case against Granola for India."
- **6.4 — Customer support.** A real human answers every email for the first 60 days. Yes, founder included.
- **6.5 — Telemetry on activation + conversion.** Tighten the funnel based on what 1,000+ public-launch users do differently from the 100 private-beta users.

### Phase 6 — gate

30 days post-launch: 10,000 signups, 25% week-4 retention, 5% free → paid conversion. If we miss, run the next 30 days as a fix-funnel sprint before any feature work.

---

## Phase 7 — v2 horizon (Months 8–12)

**Goal:** Build the moat — the visual graph, mobile companion, and standalone notes — that makes LifeOS the *only* app on a user's screen.

### Workstreams (sequence TBD based on what v1.5 data reveals)

- **7.1 — Visual graph view.** The Obsidian-style galaxy, auto-built from the graph layer. Click any node → see everywhere it appears. This is the moment users say "oh, this is different from everything else."
- **7.2 — Mobile companion app.** iOS + Android. Review meetings, search, dictation, capture in-person meetings via mic. *Not* full feature parity with desktop — review and quick capture only.
- **7.3 — Standalone notes module.** Manual notes that participate in the graph via `@mention` of any entity.
- **7.4 — Public sharing.** Project spaces sharable with a link.
- **7.5 — API + integrations.** Slack export, Linear export, Notion export, calendar write.
- **7.6 — On-device transcription (Sensitive Mode).** Premium tier feature for doctors, lawyers, therapists. Differentiator no incumbent has.

### Phase 7 — gate

End of Month 12: visual graph is shipped, mobile companion is in TestFlight, two flagship integrations are live. The product is now structurally different from any incumbent.

---

## Cross-phase risks (track these every month)

| Risk | Early warning | Mitigation |
|---|---|---|
| Hallucination rate creeps up | Weekly QA dashboard shows >1.5% | Halt feature work; fix prompts or upgrade model |
| Transcription weakens on Indian English as model providers update | WER regression on the Phase 0 recording set | Lock model versions; consider own model |
| Granola or another competitor copies the graph thesis | Public roadmap or release notes hint at it | Accelerate v2 graph view; lean harder on India + pricing |
| Cloud cost per meeting exceeds plan price | Monthly unit-economics review shows margin compression | Negotiate ASR rates; switch providers; consider on-device for free tier |
| Burn-out on the founder doing user interviews + spec + recruiting + launch | Founder skipping interviews or weekly reviews | Hire a head of growth at the start of Phase 6 |
| Beta users love it but churn after week 6 | Cohort curves flatten then drop | Investigate "why" with calls; the long-tail of value (graph) may not be felt yet |

---

## Decision log / open questions

These are decisions we haven't made. Each must have a target date for resolution; do not let them rot in a doc.

1. **Mac-first vs Mac + Windows at launch?** Target: end of Phase 1.
2. **One default note template vs template-per-context?** Target: after Phase 0 interviews.
3. **Calendar integration depth — read-only or read-write?** Target: Phase 1.
4. **In-meeting AI suggestions (yes/no)?** Target: end of Phase 4 beta data.
5. **India pricing — ₹599 vs ₹399 Pro?** Target: Phase 5, with price-elasticity testing.
6. **Beta selection criteria (founder network vs broader)?** Target: end of Week 3.

---

## What "done" looks like at each phase — a single sentence

- **Phase 0 done:** We've decided to build (or not).
- **Phase 1 done:** A designer and an engineer can each describe v1 in one sentence using the same words.
- **Phase 2 done:** Every epic has an owner and an estimate; build can start Monday.
- **Phase 3 done:** The team has used LifeOS to capture their own meetings for four weeks and miss it when it's offline.
- **Phase 4 done:** 100 strangers have used LifeOS, and at least 10 of them have written unsolicited "I love this" messages.
- **Phase 5 done:** A user can complete the full "meeting → todo → expense" flow without leaving LifeOS.
- **Phase 6 done:** LifeOS gets 10,000 signups in 30 days through organic + earned channels.
- **Phase 7 done:** A new user can install LifeOS and, within five minutes, see their personal graph form — and never want to go back to a fragmented set of apps.

---

*End of master plan. Open the Build Dashboard to start executing.*
