# LifeOS — v1 Product Spec

**Status:** Draft v0.1
**Date:** 23 May 2026
**Working name:** LifeOS *(see Naming, end of doc)*
**Owner:** Founder + team
**One-line pitch:** A personal knowledge brain whose primary input is your meetings — and whose long-term ambition is to be the single app where everything you capture, decide, owe, and remember lives in one connected graph.

---

## 1. Vision

Today, the things you care about live in fragments. Meeting notes in Granola. Action items in Todoist. Expenses in a different app. Personal notes in Apple Notes. Long-form thinking in Obsidian. None of these talk to each other. Your brain is split across twelve apps and the connective tissue exists only inside your head.

LifeOS is the opposite bet: **one app, one graph, one brain.** Every meeting, todo, expense, voice memo, and note becomes a node in a single personal knowledge graph that grows with you over months and years. The AI can answer questions across all of it. The modules feed each other automatically.

We start with the meeting-capture module because it is the highest-density input source — one hour-long call can produce a week's worth of structured notes, action items, and decisions. Get capture right and the rest of the app has fuel.

---

## 2. The Moment

Every great consumer product is built around one moment of use. LifeOS v1 is built around this one:

> **"I am in, or just finished, a meeting — and I want my brain to have it perfectly captured and organized without lifting a finger."**

This moment is intentionally universal. It applies to a founder pitching investors, a sales rep on a discovery call, a student in a lecture, a doctor with a patient, a freelancer scoping a project, a couple planning a home renovation with a contractor. The user demographic doesn't matter — the moment does. Every design and AI decision in this spec flows from this moment.

---

## 3. Why This Can Win

| Incumbent | What they do well | What they miss |
|---|---|---|
| **Granola** | Beautiful AI meeting notes, clean UX, real-time capture | No graph. No cross-app connection. Notes are dead ends. $18/mo. Weak on multilingual / Indian English. |
| **Obsidian** | The reference design for personal knowledge graphs | No AI capture. Requires manual linking. Steep learning curve. Not for "everyone." |
| **Notion** | Flexible workspace, broad surface area | No real meeting capture. AI is bolt-on. Graph view is a toy. Slow. |
| **Mem / Tana / Reflect** | Reaching for "second brain + AI" | None has nailed meeting capture. Small followings. Fragmented features. |
| **Capacities** | Object-based PKM done elegantly. Every note is a typed object (Person, Book, Place, Idea, Project); the graph emerges as you reference objects inside other objects. Beautiful native apps, calm UX, devoted user base. | No AI meeting capture — the user manually classifies every object. The graph is *yours to maintain*, not auto-built. No transcription, no Zoom integration, no cross-app modules. |
| **Otter / Fireflies / Read.ai** | Enterprise meeting transcription | Boring outputs, bot-in-the-meeting model, no personal-brain layer |

**The gap LifeOS fills:** AI-native capture + personal graph + everyday cross-app modules, in one product, at a price an individual will pay.

> **Note on Capacities specifically.** Their object model (typed nodes: Person, Project, Idea, etc.) is the closest existing approximation to what our entity-extraction layer in Section 9 produces automatically. The strategic positioning against them writes itself: *"Capacities, except your meetings build the graph for you."* Their visual graph implementation is also the cleanest in any consumer app on the market and is worth studying as a design reference for our v2 graph view.

---

## 4. v1 Scope — What We Are Building

v1 ships the **Notes module** (Granola-equivalent, with graph foundations baked in). Nothing else.

### 4.1 Core capabilities

1. **Meeting capture** — joins Zoom / Google Meet / Microsoft Teams via system audio + microphone. Works for in-person meetings via mic-only mode. No bot joins the call.
2. **Real-time transcription** — accurate transcription with diarization (who-said-what). First-class support for Hindi-English code-switching and Indian English.
3. **Pre-meeting prep** — user types or pastes context (agenda, attendees, prior notes) before the meeting. AI uses this to bias note generation.
4. **AI-structured notes** — after the meeting (or live, streaming), AI produces a structured note: Summary, Decisions, Action Items, Open Questions, Key Quotes, Follow-ups. User can edit any section.
5. **Meeting chat** — ask any question about the meeting in natural language: "What did Priya say about pricing?" "What did I commit to?"
6. **Cross-meeting memory** — chat across all meetings: "What has the team said about hiring this quarter?" "Have I ever discussed Acme with anyone?"
7. **Entity extraction (silent)** — every meeting silently extracts entities: people, companies, projects, decisions, dates, amounts, topics. These become the seeds of the knowledge graph. **Not visible as a graph in v1** — but the data structure is built so v2 can render it.
8. **Search** — full-text + semantic search across every meeting ever recorded.
9. **Share / export** — one-click share of a meeting note as a public link, Markdown, or PDF.

### 4.2 Platforms

- **Desktop only in v1** — Mac (priority), then Windows.
- Mac first because system audio capture is cleanest there and our ICP-of-the-moment (anyone in video calls) is on Mac disproportionately.
- Mobile companion app is **v2** — review, search, and dictation only, not capture.

---

## 5. Anti-Scope — What We Are NOT Building in v1

This section matters more than Section 4. The temptation to bloat will be constant. We will say no to:

- **The visual graph view** (the "Obsidian galaxy"). The data layer exists; the UI is v2. Building a beautiful graph view is a 6-month project and we don't earn the right to it until we have users with months of meetings.
- **Todo tab, Expense tab, any other module.** These are v1.5 and v2. v1 just lays the data hooks.
- **Team / collaboration features.** No shared workspaces, no multi-user notes, no permissions. LifeOS v1 is single-player.
- **CRM-style relationship tracking.** Tempting but distracting. Defer to v2+.
- **Custom AI prompts / templates.** v1 ships one excellent default. Configurability is a feature for power users we don't have yet.
- **Integrations.** No Slack, no Salesforce, no Linear, no Notion sync. v1 is a closed loop: meeting in, structured note out.
- **Audio editing / podcasting features.** We are not an audio tool. We are a brain.
- **Mobile capture.** Different product. Different problems. Don't split focus.

If anyone on the team proposes adding anything from this list to v1, the answer is no, with this section as the reason.

---

## 6. Product Pillars

Every design and engineering decision in v1 must serve one of these four pillars. If a feature serves none, it doesn't ship.

1. **Effortless capture.** From "click record" to "I have my notes" must feel like zero work. No bot joining. No setup per meeting. No formatting decisions.
2. **Trustworthy intelligence.** The notes have to be right. Hallucination is fatal. The AI must say "I'm not sure" rather than invent a quote. Source-grounded everywhere.
3. **Graph foundations.** Every entity extracted, every link formed, every meeting tagged — quietly building the user's personal graph from day one, even though it's invisible in v1.
4. **Personal-brain feel.** LifeOS is *yours*. Single-player. Calm. Not a productivity tool that nags you. A second mind that remembers things so you don't have to.

---

## 7. User Flow

### 7.1 First-run

App install → grant microphone + system audio permissions → optional Google/Microsoft calendar connect (so LifeOS knows when meetings start) → tutorial meeting (60 seconds, voiced) → home view.

### 7.2 Daily flow — the canonical journey

1. **Pre-meeting.** Calendar event approaches. LifeOS surfaces a notification: *"Call with Priya in 5 min — add anything you want me to know?"* User can paste context or skip.
2. **Meeting start.** User joins the Zoom/Meet/Teams call. LifeOS auto-detects and starts capturing (with a visible recording indicator — never silent). Or user clicks "Record" for in-person.
3. **During the meeting.** A floating overlay shows live transcript + a few real-time bullets. User can mark moments ("flag this") or jot quick notes. Most users will close the overlay and ignore LifeOS during the call — that's fine.
4. **Meeting ends.** Within 30–60 seconds, the structured note is ready. Notification: *"Your call with Priya is captured — 4 action items, 2 decisions."*
5. **Review.** User opens the note. Reads. Edits anything wrong. Optionally clicks "Share" to send a public link to attendees.
6. **Retrieval (hours / days / weeks later).** User opens LifeOS, types a question in the global chat: *"What did Priya commit to on the pricing question?"* LifeOS answers, cites the meeting, jumps to the moment in the transcript on click.

### 7.3 Key screens

- **Home / Library** — reverse-chronological list of all meetings, with filters (people, date, project). Search bar at the top.
- **Meeting view** — the structured note (Summary, Decisions, Action Items, Open Questions, Key Quotes, Follow-ups, Full transcript). Two-pane: structured note on the left, transcript on the right.
- **Live overlay** — small floating window during a meeting. Live transcript snippet, real-time bullets, flag button.
- **Global chat** — full-screen AI chat across all meetings. Like ChatGPT, but the corpus is your life.
- **Pre-meeting prep card** — minimal screen that pops up before a calendar event.
- **Settings** — account, audio devices, language preference, AI model, data export.

That's six screens. Resist adding a seventh in v1.

---

## 8. AI Behaviors

### 8.1 Transcription

- Real-time, streaming, with diarization.
- Languages v1: English (US/Indian/UK), Hindi, Hinglish code-switching. Spanish and other Indic languages v1.5.
- Model: leading streaming ASR (evaluate Whisper-large-v3, Deepgram Nova-2, ElevenLabs Scribe; pick on accuracy for Indian English specifically).

### 8.2 Structured note generation

Default template (user cannot edit in v1 — one excellent default):

```
SUMMARY            — 3-5 sentence narrative of what happened
DECISIONS          — bullets of things that were decided
ACTION ITEMS       — bullets, each with owner (extracted) + due (extracted) + flagged
                     if owner == "me" 
OPEN QUESTIONS     — things raised but not resolved
KEY QUOTES         — 3-7 short quotes worth remembering, with attribution
FOLLOW-UPS         — things to do before next meeting / next time
```

Every section is editable inline. Action items have a checkbox.

### 8.3 Meeting chat

- Scoped to a single meeting by default.
- Source-grounded: every answer cites the timestamp in the transcript. Click → jump to that moment.
- Refuses to invent. If the answer isn't in the meeting, the AI says so plainly.

### 8.4 Global chat (cross-meeting memory)

- Same as meeting chat but corpus is every meeting the user has ever recorded.
- Vector + structured retrieval — hybrid. Use embeddings for semantic, plus the entity graph for structured queries ("all meetings where Priya appeared and pricing was discussed").

### 8.5 Entity extraction (silent, foundational)

After each meeting, extract and store:

- **People** — names mentioned, attendees, roles if stated.
- **Companies / orgs** — entities mentioned.
- **Projects / topics** — recurring themes the user cares about.
- **Decisions** — separated from action items.
- **Action items** — with owner + due + source meeting.
- **Amounts** — any number with a currency, with context. (This is the seed for the future Expense tab.)
- **Dates** — any date mentioned, with context.

Entities are deduplicated across meetings (Priya the founder = Priya the founder, not three Priyas). Resolution is fuzzy + user-correctable in v1.5.

### 8.6 Quality bar

- Hallucination rate target: <1% on a benchmark we build of 100 hand-labeled meetings.
- Transcription WER target: <8% on Indian English; <5% on US English.
- Time-to-note after meeting end: <60 seconds median.

---

## 9. Knowledge Graph Layer (Foundations)

The graph is invisible in v1, but it is the spine of the product. Architecture must be right from day one or v2 is painful.

### 9.1 Data model

Three primitives:

- **Nodes** — meetings, people, companies, projects, decisions, action items, amounts, topics, notes (future), todos (future), expenses (future).
- **Edges** — typed relationships (e.g., `person:mentioned_in:meeting`, `action_item:owned_by:person`, `decision:made_in:meeting`).
- **Source provenance** — every node and edge carries a pointer to the transcript moment that produced it.

### 9.2 Why this matters now

When v1.5 adds the Todo tab, action-item nodes from meetings become first-class todos in a UI. No migration. When v2 adds the visual graph, the data is already there. We avoid the worst sin in software: building a feature and then having to rebuild the data layer to support its sibling.

### 9.3 v1 surface area of the graph

- Search uses graph data (e.g., filtering meetings by person).
- Global chat uses graph data to answer structured questions.
- Nothing else. No graph view. No node detail pages. Don't build them.

---

## 10. Cross-Tab Hooks (for v1.5+)

These do not ship in v1. They are listed here so v1 architecture makes them trivial later.

| Future module | Hook from v1 notes |
|---|---|
| **Todo tab** | Action items extracted in meetings become todos automatically (with a "from meeting X" provenance). |
| **Expense tab** | Amount entities mentioned ("we'll spend ₹2,000 on hosting") become pending expense entries for user review. |
| **People / CRM-lite** | Person entities accumulate across meetings, forming a contact graph: every interaction, every commitment, every mention. |
| **Project / topic spaces** | Project entities aggregate every meeting that touched them. A natural "project room" emerges. |
| **Standalone notes** | When the user types a note (v1.5), it can `@mention` any entity that exists from meetings — same graph. |

---

## 11. Phasing

### v1 (target: 4 months from kick-off)

Ship the Notes module on Mac, end-to-end, polished. One module, done well. Hard private beta to ~100 hand-picked users. No public launch.

### v1.5 (target: +2 months after v1)

- Windows.
- Todo tab.
- Expense tab.
- Entity resolution UI (let the user merge "Priya" / "Priya S." / "Priya Sharma").
- Public launch.

### v2 (target: +4–6 months after v1.5)

- Visual graph view (Obsidian-style, but auto-built).
- Mobile companion app (review + capture in-person).
- Public sharing of project spaces.
- Standalone notes module.
- API / integrations (Slack, Linear, Notion export).

### v3+ (long-horizon, not committed)

- Team / shared graphs.
- Marketplace of templates and integrations.
- The full super-app vision: every tab a deep module, all feeding one brain.

---

## 12. Pricing & Positioning

### 12.1 Pricing thesis

Granola is $18/mo, US-priced, US-centric. LifeOS undercuts globally and prices for India properly.

- **Free tier** — 10 meetings/month, no global chat, no export. Acquisition engine.
- **Pro** — $9/mo (US/EU), ₹599/mo (India), unlimited meetings, global chat, export, priority transcription. Annual discount.
- **Future Team tier** — v2+, shared spaces, $15–20/seat/mo.

### 12.2 Positioning vs Granola

> "Granola captures your meetings. LifeOS remembers them — and connects them to everything else in your life."

The single sentence the homepage leads with. Every marketing asset flows from it.

### 12.3 Why we win on positioning

- Cheaper, especially in India where Granola is unaffordable for individuals.
- Better on Indian English / Hinglish.
- The graph + cross-tab thesis is a story Granola structurally cannot tell — they've committed to "just meeting notes."

---

## 13. Success Metrics

### 13.1 v1 (private beta) — measure these, no targets yet, just instrument

- **Activation:** % of new users who record their first meeting within 24 hours.
- **Week-1 retention:** % of new users who record ≥3 meetings in their first week.
- **Note-edit rate:** % of structured notes the user edits (lower = AI is right more often).
- **Time-to-note:** median seconds from meeting-end to structured note ready.
- **Hallucination escape rate:** % of notes flagged by user-feedback "this is wrong."
- **Global-chat usage:** % of weekly actives who use cross-meeting chat at least once / week. *This is the leading indicator that the graph thesis is working.*

### 13.2 v1.5 (public launch) — first real bar

- 10,000 signups in first 30 days.
- 25% week-4 retention.
- 5% free → paid conversion.

(These numbers are starting points — calibrate against beta data.)

### 13.3 v2 — moat metric

- Average number of meetings per active user (the deeper the graph, the harder to churn).
- Cross-tab usage (% of users using ≥2 tabs weekly). This is the metric that proves the super-app thesis.

---

## 14. Technical Considerations (high-level)

Not an architecture doc — just decisions a PM / founder needs in their head.

- **Transcription:** start with a managed API (Deepgram or AssemblyAI) for speed; revisit own-model for cost at scale.
- **LLM for structured notes + chat:** Claude or GPT-class frontier model; budget ~$0.05–0.15 per meeting at v1 scale. Falls under unit economics as we grow.
- **Embeddings:** OpenAI `text-embedding-3-large` or open-source equivalent; store in pgvector or a managed vector DB.
- **Graph storage:** Postgres with relational tables for nodes + edges in v1. No Neo4j until v2 graph view forces it.
- **Audio capture on Mac:** ScreenCaptureKit (modern, no kernel extensions) + Core Audio for mic.
- **Privacy / on-device option:** v1 is cloud. On-device transcription is a v2+ premium feature ("Sensitive mode") — meaningful for doctors, lawyers, therapists, etc.
- **Data residency:** India-region data residency from day one. Non-negotiable for Indian users and a wedge against US-centric incumbents.

---

## 15. Open Questions

These are decisions we haven't made. Tag them, schedule them, don't let them rot.

1. **Naming.** "LifeOS" is a placeholder. Candidates worth testing: *LifeOS, Cortex, Memo (taken), Loop, Ground, Index, Brain, Mind, Trace.* The name should evoke memory, foundation, or connectedness — not productivity. Trademark search required before commitment.
2. **Mac-first vs Mac-only?** Do we ship Windows at launch or 6 weeks later? Cost: ~2 engineer-months. Trade-off: India has lots of Windows users; Mac-only is a strong wedge in startup land but caps TAM.
3. **Calendar integration depth.** Read-only (just to know when meetings happen) vs read-write (LifeOS creates follow-up events from action items). v1: read-only. Question: is read-write a v1.5 must-have or v2 nice-to-have?
4. **In-meeting AI vs only post-meeting?** Granola has live bullets. We propose the same. But should the AI suggest things to say in real-time ("you haven't asked about timeline")? Powerful but creepy. Defer to user testing.
5. **Default note template.** We propose one fixed template in v1. Validate with 20 beta users that one template works across founders/sales/students/professionals. If it doesn't, we need template-per-context — and that's a meaningfully bigger v1.
6. **Pricing in India — ₹599 or ₹399?** Granola is unpriced for India. We need price elasticity testing.
7. **Beta selection.** 100 users — how do we pick? Founder network + a few specific archetypes (5 founders, 5 sales reps, 5 students, 5 consultants, 5 doctors/therapists, etc.) to stress-test the universality claim before public launch.

---

## 16. Naming

Working name: **LifeOS.**

The name does real work for the positioning. An operating system sits *beneath* every app — invisibly powering them, providing the file system, the memory, the process scheduler. That is precisely what LifeOS is to your life: invisible plumbing beneath your meetings, todos, expenses, and notes. It also reframes the product away from "another productivity app" into infrastructure — which is a much stronger positioning against Notion/Obsidian/Granola, all of which are surface-level apps.

**Risks with the name:**
- "LifeOS" is descriptive enough that several small apps have used variants of it. Trademark search required in India, US, EU before any public commitment.
- The `.com` is almost certainly taken or expensive — `lifeos.app`, `lifeos.io`, `lifeos.ai`, or a coined alternative may be necessary.
- "OS" framing sets a high bar — users will expect it to be foundational, not just useful. Live up to that bar or the name backfires.

**Alternatives to keep on the bench** in case trademark / domain force a change:
- **Cortex** — biological, brain-y, slightly clinical.
- **Trace** — implies record + thread.
- **Index** — bookish, archive-y, understated.
- **Loop** — implies the closed feedback (capture → recall → act).
- **Ground** — foundational, grounded, calm.

Founder call. Action: run trademark + domain checks on "LifeOS" this week so we're not anchored on a name we can't legally own.

---

## 17. What "Done" Looks Like for v1

A user who installs LifeOS on Monday should, by Friday:

1. Have recorded 3+ meetings.
2. Have had at least one moment of "wait, that's exactly what was said" delight.
3. Have asked the global chat at least one question and gotten a useful, source-grounded answer.
4. Have shared one meeting note with someone outside LifeOS.
5. Have at least one moment of frustration — something wrong, something missing — that we can talk to them about.

If we hit those, v1 is a success, and we have the right to ship v1.5.

---

*End of spec. Next steps: founder reviews, edits, sends to team. Then we break v1 into engineering epics.*
