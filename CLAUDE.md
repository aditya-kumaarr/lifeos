# CLAUDE.md — Handoff Brief for Claude Code Agents

**Read this first. Every section matters.**
This document is the single source of truth for any Claude Code agent picking up the Sevri project. It captures every decision, every credential note, every rejected path, the full plan, the dashboard system internals, the user's communication preferences, and exactly what to do next.

If you skim only one section, skim §15 (What To Do Next). If you skim two, also read §1 (TL;DR) and §11 (Rejected Names — Do Not Relitigate).

---

## 1. TL;DR

- **Project:** Sevri — an AI-powered meeting capture app that builds a personal knowledge graph; the long-term ambition is one app where todos, expenses, notes, meetings, and memory all live in one connected brain.
- **Pronunciation:** SEV-ree (two syllables, five letters).
- **Owner:** Aditya Kumar — [@aditya-kumaarr on GitHub](https://github.com/aditya-kumaarr).
- **Status:** Planning phase complete. Name locked. Build dashboard live. Phase 0 (de-risk week) ready to start.
- **Live repo:** <https://github.com/aditya-kumaarr/sevri>
- **Live dashboard:** <https://aditya-kumaarr.github.io/sevri/dashboard/>
- **Most urgent next action:** Confirm `sevri.ai` domain has been registered. If not, get it done in the next 24 hours — coined `.ai` domains get sniped fast.

---

## 2. What Sevri Is (Product Context)

### 2.1 One-line pitch

*A personal knowledge brain whose primary input is your meetings.*

### 2.2 The thesis

Knowledge work today is fragmented across many apps: meeting notes in Granola, action items in Todoist, expenses in another app, personal notes in Apple Notes, long-form thinking in Obsidian. None of these talk to each other. The user's brain is split across twelve apps and the connective tissue exists only inside their head.

Sevri is the opposite bet: **one app, one graph, one brain.** Every meeting, todo, expense, voice memo, and note becomes a node in a single personal knowledge graph that grows with the user over months and years. The AI can answer questions across all of it. The modules feed each other automatically.

v1 starts with AI meeting capture (Granola-equivalent + graph foundations baked in) because meetings are the highest-density input source.

### 2.3 The user moment v1 is built around

> *"I just had a meeting — and I want my brain to have it perfectly captured and organized without lifting a finger."*

This is the only moment that matters for v1. Every design and AI decision flows from it.

### 2.4 Target users

The founder explicitly said **"everyone"** when pushed on user segmentation, against the advice in the spec. The spec was kept faithful to that — we design around a *moment* (above) rather than a demographic. India is the geographic priority market, so Hindi-English code-switching and Indian English transcription are first-class concerns. Pricing is explicitly two-tier: $9/mo US, ₹599/mo India.

### 2.5 The competitive landscape (as of May 2026)

| Incumbent | What they do well | What they miss (i.e. our opening) |
|---|---|---|
| Granola | Beautiful AI meeting notes, real-time capture | No graph. No cross-app. Notes are dead-ends. $18/mo. Weak on Indian English. |
| Obsidian | Reference design for personal knowledge graphs | No AI capture. Manual linking. Steep learning curve. |
| Notion | Flexible workspace | No real meeting capture. AI is bolt-on. Graph view is a toy. Slow. |
| Mem / Tana / Reflect | Reaching for "second brain + AI" | None has nailed meeting capture. |
| Capacities | Object-based PKM done elegantly | No AI meeting capture; the user manually classifies. Graph is yours to maintain, not auto-built. |
| Otter / Fireflies / Read.ai | Enterprise meeting transcription | Boring outputs, bot-in-the-meeting model, no personal-brain layer. |

**The strategic positioning line** that resulted from this analysis (in spec Section 3): *"Capacities, except your meetings build the graph for you."*

---

## 3. Current State

Everything below is true at the time of this handoff. If you discover a discrepancy, the live repo state at <https://github.com/aditya-kumaarr/sevri> is authoritative.

### 3.1 Done

- [x] v1 Product Spec drafted (see `docs/v1-Product-Spec.md`)
- [x] Master Build Plan drafted (12 months, 7 phases — see `docs/Master-Plan.md`)
- [x] Phase 0 User Interview Guide drafted (see `docs/Interview-Questions.md`)
- [x] Interactive Build Dashboard built and live with GitHub auto-sync
- [x] Repository created, GitHub Pages enabled, dashboard deployed
- [x] Name research complete — **Sevri locked in** (full audit trail in `docs/Name-Decision.md`)
- [x] All references throughout repo updated from "LifeOS" (working name) → "Sevri"
- [x] GitHub repo renamed `lifeos` → `sevri` via API; Pages re-deployed at new URL

### 3.2 Not yet done

- [ ] `sevri.ai` domain purchased *(urgent — verify with user)*
- [ ] Defensive registrations: `sevri.app`, `sevri.io`, `sevri.so`
- [ ] Trademark clearance by IP attorney (US, EU, India)
- [ ] Social handles reserved (`@sevri` on X, LinkedIn, Instagram)
- [ ] Phase 0 workstreams executed (interviews, transcription spike)
- [ ] Phase 1 deliverables (spec revision, wireframes, architecture doc, design system)
- [ ] All Phase 2+ work (engineering epics, build, beta, launch, etc.)

---

## 4. Repository Layout

```
sevri/
├── CLAUDE.md                       ← THIS FILE — handoff for future Claude agents
├── README.md                       ← human-facing project intro + dashboard usage
├── .gitignore
│
├── docs/                           ← source-of-truth planning documents
│   ├── v1-Product-Spec.md          ← what we're building, v1 scope, anti-scope
│   ├── Master-Plan.md              ← 12-month phased execution plan (source of truth for the dashboard)
│   ├── Interview-Questions.md      ← Phase 0 user-research field guide (22 questions)
│   └── Name-Decision.md            ← full audit trail of name search; why "Sevri"
│
├── dashboard/
│   └── index.html                  ← interactive build dashboard (self-contained HTML)
│
├── state/
│   └── dashboard-state.json        ← persistent dashboard progress (auto-synced)
│
└── app/                            ← placeholder for v1 application code (empty for now)
    └── .gitkeep
```

### 4.1 File-by-file purpose

| File | Purpose | When to edit |
|---|---|---|
| `CLAUDE.md` | This handoff. | When you make a decision that future agents must respect. Update §11 (rejected) and §3 (state). |
| `README.md` | Human-facing project intro. | When project structure or setup steps change. |
| `docs/v1-Product-Spec.md` | Product spec — what we're building, scope, anti-scope, screens, AI behaviors, pricing. | When product scope changes after Phase 0 / 1. Versioned as v0.x. |
| `docs/Master-Plan.md` | Execution plan — phases, workstreams, owners, deliverables. | When the plan needs revision based on what Phase 0 reveals. |
| `docs/Interview-Questions.md` | Field tool for Phase 0 interviews. | After running interviews, if patterns emerge that should refine the script. |
| `docs/Name-Decision.md` | Naming audit trail. | Should not need editing — locked. |
| `dashboard/index.html` | Live dashboard. Reads Master-Plan as 49 todos. | When todos change (must match Master-Plan), or when the dashboard UI needs work. |
| `state/dashboard-state.json` | Dashboard progress. **Auto-managed by dashboard JS.** | Do not edit manually — the dashboard's JS will overwrite. |
| `app/` | Future v1 code lands here from Phase 3 onward. | Phase 3+. Likely subfolders: `app/client/`, `app/server/`, `app/shared/`, `app/infra/`. |

---

## 5. Access, Credentials, and Security

### 5.1 GitHub

- **Account:** `aditya-kumaarr` (the user's personal GitHub).
- **Repo:** `aditya-kumaarr/sevri` (public).
- **Repo URL:** <https://github.com/aditya-kumaarr/sevri>
- **The user has `gh` CLI authenticated locally** on their Mac, so they can run any standard git/gh command directly.
- **My (Claude's) bash sandbox does NOT have `gh`** but has `git` and authenticated HTTPS via PAT. The remote URL is set to `https://github.com/aditya-kumaarr/sevri.git`.

### 5.2 GitHub Personal Access Token (PAT)

A PAT with `repo` scope is currently in use, but **the token itself is intentionally NOT committed to this repo** — GitHub's push protection (secret scanning) correctly blocked the first attempt to include it here, which is the right behavior.

**Where the active PAT actually lives:**

- In the user's browser localStorage (powers the dashboard auto-sync to `state/dashboard-state.json`)
- The user can view, rotate, or revoke it at any time at <https://github.com/settings/tokens>

**For a future agent who needs to authenticate against the repo via API:**

1. **Prompt the user** to generate a fresh PAT with `repo` scope at the link above.
2. Have them paste it directly in chat to you (not commit it anywhere).
3. Use it for the immediate operation, then advise rotation when convenient.
4. Never commit any PAT, API key, or other secret to this (or any) repo — GitHub will block the push and the secret will be in git history forever even if you reverse-engineer it out.

**The current PAT was used to:**

1. Create the repo via API
2. Push commits via HTTPS-with-token URL
3. Enable GitHub Pages
4. Rename the repo (LifeOS → Sevri)
5. Power the dashboard's GitHub Contents API auto-sync (reads/writes `state/dashboard-state.json`)

**Expiry:** 90 days from creation (around late August 2026). Set a calendar reminder for the user.

### 5.3 Local workspace

- **Cowork workspace folder (on user's Mac):** `/Users/adityakumar/Library/CloudStorage/OneDrive-Personal/LifeOS/`
- **Note:** the folder is still called `LifeOS` even though the product is now Sevri. This is because:
  - OneDrive sync would create complications if the folder were renamed
  - The folder name has no bearing on the repo / product brand
  - We chose not to disrupt anything working
- **The repo inside it has correct remote URL** (`https://github.com/aditya-kumaarr/sevri.git`).
- **Bash sandbox path mapping:** `/Users/.../LifeOS/` ↔ `/sessions/<id>/mnt/LifeOS/`

### 5.4 Email (project-related)

- The user provided `cityfurnish10@gmail.com` (their Cityfurnish business email). This is what git commits are attributed to. The user's personal GitHub username (`aditya-kumaarr`) does not match the Cityfurnish email — both are theirs.
- **Style note:** the user's other work involves a company called **Cityfurnish** (always written exactly as `Cityfurnish`, never `CityFurnish`). This is unrelated to Sevri but you may encounter the preference in workspace memory.

---

## 6. The Live Dashboard System (Technical Internals)

If the user reports a dashboard issue or you need to extend it, this is the model.

### 6.1 Architecture

- **Single-file HTML** at `dashboard/index.html`. Self-contained — inline CSS, inline JS, no build step.
- **Hosted by GitHub Pages** from the `main` branch root. URL is `https://aditya-kumaarr.github.io/sevri/dashboard/`.
- **Cache-control meta tags** are set in `<head>` to discourage aggressive Safari caching.

### 6.2 Data layer

- **Source of truth for the todo list:** the JS constants `PHASES[]` and `TODOS[]` in `dashboard/index.html`. These were hand-derived from `docs/Master-Plan.md`. If `Master-Plan.md` changes, these must be updated to match.
- **Persistent progress:** `state/dashboard-state.json` in the repo. Schema:
  ```json
  {
    "completed": { "p0-1": true, "p1-3": true, ... },
    "collapsed": { "p3": true, ... },
    "activeTodo": "p0-3",
    "updatedAt": "2026-05-23T07:42:15.123Z"
  }
  ```
- **localStorage caches** the same state under key `sevri-dashboard-v2` plus a separate config key `sevri-dashboard-cfg-v1` holding `{owner, repo, branch, pat}`.

### 6.3 Sync mechanism

- **GitHub Contents API** is used for read/write.
- On page load (`init()`): fetches `state/dashboard-state.json`, smart-merges with local state by `updatedAt` timestamp (newer wins).
- On every checkbox change: debounced 1.5s, then `PUT /repos/aditya-kumaarr/sevri/contents/state/dashboard-state.json` with new content + previous SHA.
- **Auto-refresh:** polls every 30 seconds; immediately refetches on `visibilitychange` to `visible`. Means two tabs / two machines stay in sync within ~30s of any change without manual reload.
- **Error recovery:** 409 (SHA conflict) and 422 (SHA missing) both trigger a refetch + retry.
- **Sync gate:** `isInitialized` flag prevents the first save from racing with the initial fetch.

### 6.4 Critical bugs we've already fixed (don't reintroduce)

1. **PUT requests were dropping the Authorization header** due to `Object.assign({headers}, opts)` ordering. Fixed by `Object.assign({}, opts, {headers})`.
2. **First-click race condition** between user clicking and init fetching SHA. Fixed by `isInitialized` gate.
3. **Stale state on second tab** when changes were made in tab 1. Fixed by 30s polling + visibilitychange refetch.

### 6.5 One-click setup link

For onboarding a new browser to sync, the URL fragment carries the PAT:

```
https://aditya-kumaarr.github.io/sevri/dashboard/#setup=<PAT>
```

On load, the dashboard parses `#setup=`, stores the PAT in localStorage, strips the fragment from the URL bar via `history.replaceState`, and proceeds to sync. **The PAT briefly lives in browser history** — acceptable for a personal project but document it as a known trade-off.

---

## 7. The Plan — Phased Execution (12 Months)

Pulled from `docs/Master-Plan.md`. Full detail lives there; this is the summary so you can hold the shape in your head.

| Phase | When | Goal | Key deliverables |
|---|---|---|---|
| **0 — De-risk** | Week 1 | Validate before building | Name lock ✅, 15 user interviews, transcription quality spike, go/pivot/kill call |
| **1 — Synthesize + Design** | Weeks 2–3 | Insight → design | Spec revision, low-fi wireframes for 6 screens, technical architecture doc, mid-fi mockups, beta-list kickoff |
| **2 — Engineering Kickoff** | Week 4 | Plan → epics | v1 broken into 6-10 epics with estimates; staging infra; design system v1; team roster |
| **3 — Build v1** | Months 2–4 | Ship private beta | Mac app: audio capture, transcription pipeline, knowledge graph data layer, structured notes, meeting view, entity extraction, search, live overlay, calendar integration, meeting chat, global chat, share/export, onboarding |
| **4 — Private Beta** | Month 5 | Validate with 100 real users | 4 waves of 25; weekly user interviews; daily bug triage |
| **5 — Build v1.5** | Months 5–7 | Make the cross-tab thesis real | Todo tab (action items from meetings auto-flow), Expense tab (mentioned amounts auto-flow), Windows port, entity resolution UI, payments + pricing |
| **6 — Public Launch** | Month 7 | Open the doors | Marketing site, coordinated launch motion (Product Hunt, HN, IN tech communities), 3 long-form essays, customer support, activation funnel tightening |
| **7 — v2 Horizon** | Months 8–12 | Build the moat | Visual graph view (Obsidian-style, auto-built), mobile companion app, standalone notes module, public sharing, API + integrations (Slack/Linear/Notion), on-device transcription ("Sensitive Mode" premium tier) |

### 7.1 Phase gates (don't skip these)

End of every phase has an explicit go-decision. Document the decision before starting the next phase. Phase 0's go/pivot/kill is the most critical — it determines whether v1 is built at all.

### 7.2 Cross-phase quality bars

- **Hallucination rate:** target <1% on a hand-labeled benchmark of 100 meetings. Measure weekly during Phase 3.
- **Transcription WER:** target <8% on Indian English, <5% on US English, <10% on Hindi-English code-switching.
- **Time-to-note after meeting end:** <60 seconds median.

These targets came from the Phase 0 transcription-quality spike requirements. If you regress against any of them during Phase 3, **halt feature work** and restore the bar before continuing.

---

## 8. Product Pillars (Use as a Decision Filter)

Every design and engineering decision should serve one of these. If a proposed feature serves none, it shouldn't ship.

1. **Effortless capture.** From "click record" to "I have my notes" must feel like zero work. No bot joining. No setup per meeting. No formatting decisions.
2. **Trustworthy intelligence.** The notes have to be right. Hallucination is fatal. The AI must say "I'm not sure" rather than invent a quote. Source-grounded everywhere.
3. **Graph foundations.** Every entity extracted, every link formed, every meeting tagged — quietly building the user's personal graph from day one, even though the graph UI is v2.
4. **Personal-brain feel.** Sevri is *yours*. Single-player. Calm. Not a productivity tool that nags you. A second mind that remembers things so you don't have to.

---

## 9. Anti-Scope (What v1 Is NOT)

This is more important than the scope. Print and pin to a wall:

- **No visual graph view in v1.** Data layer only. The galaxy is v2 work.
- **No Todo tab or Expense tab in v1.** Those are v1.5.
- **No team/collaboration features.** v1 is single-player.
- **No custom AI templates.** One excellent default.
- **No integrations.** No Slack, Linear, Notion sync.
- **No audio editing.** We are a brain, not an audio tool.
- **No mobile capture.** Different product. Mobile (review-first) is v2.

If anyone proposes adding any of these to v1, the answer is no, and this section is the reason.

---

## 10. Technical Stack Decisions (Tentative — Revisit in Phase 1)

These are starting points. The lead engineer should revisit during the architecture-doc workstream in Phase 1.

- **Desktop client:** Electron likely, or native Mac (SwiftUI) for v1 — TBD based on team skills.
- **Audio capture on Mac:** ScreenCaptureKit + Core Audio. No kernel extensions.
- **Transcription:** managed API for v1 (Deepgram Nova-2 / AssemblyAI Universal-2 / Whisper-large-v3 — choose based on Phase 0 spike). Own-model fine-tune only if the spike shows providers can't hit our WER bar.
- **LLM:** Claude or GPT-class frontier model for structured notes + chat. Budget ~$0.05-0.15 per meeting.
- **Embeddings:** OpenAI `text-embedding-3-large` or open-source equivalent.
- **DB:** Postgres + pgvector for v1. No Neo4j until v2 visual graph forces it.
- **Vector DB:** pgvector in same Postgres for v1.
- **Cloud:** any major cloud; **India data residency required from day one**.
- **Payments:** Stripe (India support) or Razorpay; needs to handle GST.
- **On-device transcription (Sensitive Mode, v2 premium):** Whisper on-device.

---

## 11. Rejected Names — DO NOT RELITIGATE

The naming search took six rounds and 280+ candidates. The decision is final. **Do not propose naming changes** unless the user explicitly raises it.

### 11.1 Names killed by major brand collisions

| Name | Why killed |
|---|---|
| **LifeOS** | 17 active competitors, including LifeOS Labs (direct AI-OS competitor) and RunLifeOS. Every TLD taken. |
| **Orix** | ORIX Corporation — Fortune 500 Japanese financial services, NYSE-listed (IX), $96.9B US assets. |
| **Cortex / Trace / Index / Loop / Ground** | Common English words. All have `.com` owned by major companies; AI/software TM conflicts everywhere. |
| **Orlo** | UK SaaS (orlo.tech), 300+ customers including UK Police. |
| **Nexa** | Nexa AI, $8.75M-funded AI infrastructure startup, San Jose. |
| **Orion** | Multiple Orion AI products, NASA spacecraft, Kagi browser, Orion Innovation (NASDAQ). |
| **Zylo** | Established Enterprise SaaS Spend Management platform. |
| **Kyro** | KYRO AI, construction-management AI platform. |
| **Rovio** | Rovio Entertainment — makers of Angry Birds. |
| **Luno** | Luno crypto exchange, 10M+ users. |
| **Varo** | Varo Bank, 5M+ US fintech customers. |
| **Aivo** | Established conversational AI / customer service AI company. |
| **Constella** | Constella App — "Second Brain App with Visual Infinite Graph and AI" (literally our v2). |
| **Mavix** | Mavix AI — custom automation systems. |
| **Tyrn** | Tyrn Review App on App Store + Google Play. |
| **Reha** | 5+ rehabilitation apps; Reha Vedic Astrology app. |
| **Welva** | Welva LinkedIn AI company. |
| **Olvi** | Olvi — Finnish brewery, public stock OLVAS. |
| **Selax** | Seljax lumberyard software. |
| **Melox** | Melox Pro virtual instrument software. |
| **Grevo** | GREVO Co., Ltd. Vietnamese game dev. |
| **Brino** | Brinno App Store apps. |
| **Tevon** | Tevon B2B software solutions. |
| **Pelya** | Game-porting developer on Google Play. |
| **Bolor** | Bolor Toli Mongolian vocabulary app. |
| **Zelva** | Multiple Zelva products (zelva.dev jazz tool, Zelva Scanner, zelva.io eco). |
| **Sevox** | UK SEVOX LTD + brand of Seventh International. |

### 11.2 Names killed by all-TLDs-taken (no brand collision found, but no available domain)

> 200+ names from the user-submitted batches across 5 rounds. Including: Avero, Noru, Evaro, Veylo, Alyr (partial), Novu, Ryvo, Oryn, Zuno, Orin, Rivo, Noro, Zyra, Avio, Kivo, Vyro, Eron, Zivo, Ovio, Nuvy, Kyvo, Lyvo, Ozyr, Oriva, Elyra, Nyro, Avoro, Lunor, Elora, Kavon, Velar, and dozens of Claude-generated coined names.

### 11.3 Why Sevri specifically

- 5 letters, 2 syllables, SEV-ree.
- Coined word — no English meaning, no cultural baggage, no incumbent claim.
- `.ai` confirmed unregistered at time of selection.
- Web search returned zero competing software/AI/app brands.
- Pronounces cleanly in English and Hindi.
- Visually clean as a logotype.
- Closest phonetic neighbour (`Sevva AI` / sevva.ai) is different spelling and different sound.

If you ever reopen naming, start by reading `docs/Name-Decision.md` end-to-end. It has the full audit trail.

---

## 12. User Profile and Communication Preferences

This is the most useful section if you've never worked with this user.

### 12.1 What the user values

- **Visible progress.** Files committed, links delivered, things working — not theory.
- **Speed.** They will get impatient with consulting-style back-and-forth.
- **Action over deliberation.** When the user says "do it for me," they mean it literally. Pre-verify, then execute.
- **Honesty about what's hard.** If something can't be done, say so directly and offer the alternative.

### 12.2 What the user doesn't like

- Lectures or theoretical framings.
- "Are you sure?" loops when they've already decided.
- Long preambles before the actual answer.
- Reopening closed decisions (the naming chapter is closed).

### 12.3 Communication style

- Plain, direct prose. Not bullet-vomit. Some structure when comparing options is fine.
- No emojis unless they use one first.
- Acknowledge what they want, then deliver. Don't justify length.
- When you've made a mistake, own it concisely and fix it. They appreciate that — they don't appreciate excessive self-flagellation.

### 12.4 Working assumptions

- **The user has a "big team" (their words)** but practically operates as a solo founder + Claude. Treat as solo for execution; plan as if there will be a team for Phase 3 onward.
- **Indian context matters.** Hindi-English code-switching support is critical for the product. Pricing assumes India will be a major market.
- **The "for everyone" user-segment choice is locked.** They explicitly chose this over my advice for narrower targeting. Don't reopen.
- **The user prefers fewer apps and consolidated tools.** This is also a product-philosophy alignment — the founder is the target user.

### 12.5 What to do when in doubt

- Ask one clarifying question via `AskUserQuestion` if a real decision is gated. Don't ask three. Don't ask "are you sure?"
- When in doubt about scope, pick the smaller version.
- When in doubt about a name decision: Sevri. It's locked.

---

## 13. The Live Dashboard — Daily Use

The dashboard at <https://aditya-kumaarr.github.io/sevri/dashboard/> is the user's primary working surface. They open it to check what's done and tick boxes when they finish things.

### 13.1 What the dashboard shows

- 49 todos grouped into 7 phases.
- Each todo is clickable; the right pane shows the full detail (owner, duration, activities, success criteria, deliverable, risks).
- The "Conduct 15 user interviews" todo (Phase 0) opens the full Interview Guide inline.
- Progress bar at the top: X of 49 done.
- Sync status pill at the top right: "Synced X ago" / "Saving…" / "Sync failed" / "Not connected".

### 13.2 What you (an agent) should do when working with the dashboard

- **Do not edit `state/dashboard-state.json` manually.** The dashboard JS manages it; you'll create merge conflicts.
- **If you change a todo's content,** update both `dashboard/index.html` (the `TODOS[]` JS array) **and** `docs/Master-Plan.md`. They must stay in sync — see §4.1.
- **If a user reports a sync issue,** check (a) the PAT is valid, (b) the dashboard JS console for errors, (c) the latest commit on the repo to see if the state file was updated.
- **The dashboard polls every 30s and on visibility change** — if a user makes a change in one tab, another tab will pick it up within 30s automatically. They shouldn't need to refresh.

### 13.3 Known dashboard limitations

- localStorage caches state per browser; switching browsers requires re-running the `#setup=` link.
- Long offline periods will desync; coming back online triggers `pullFreshState()` via visibility change.
- The `.com` repo name change to `sevri` means any old `lifeos`-cached configs need a fresh setup link.

---

## 14. Open Questions / Things Not Yet Decided

These are tagged in `docs/v1-Product-Spec.md` Section 15 and `docs/Master-Plan.md`'s "Decision log" section. Highlights:

1. **Mac-first vs Mac + Windows at launch?** Target answer: end of Phase 1.
2. **One default note template vs template-per-context?** Target answer: after Phase 0 interview synthesis.
3. **Calendar integration depth — read-only or read-write?** Currently v1 = read-only. Question: is read-write a v1.5 must-have or v2 nice-to-have?
4. **In-meeting AI suggestions (yes/no)?** Could be creepy. Defer to user testing.
5. **India pricing — ₹599 vs ₹399 Pro?** Needs price-elasticity testing.
6. **Beta selection criteria (founder network vs broader)?** Target: end of Week 3.
7. **Will the user actually run the 15 user interviews themselves, or will someone on the team?** This affects scheduling and interview-guide handoff.

When a phase concludes and one of these can be resolved, resolve it and update the spec.

---

## 15. What To Do Next (Concrete, In Order)

### 15.1 If the user has just asked you to "continue the project"

Ask exactly one question: *"Where would you like to start — wireframes for the six v1 screens, breaking v1 into engineering epics, or beginning Phase 0 user-interview prep?"*

These are the three forward-progress paths from current state. Don't propose anything else first.

### 15.2 If the user hasn't registered `sevri.ai` yet

Remind them once. Don't nag. The one-line message:

> *Quick check — did you register `sevri.ai`? It's the one thing that decays if delayed. Porkbun and Namecheap both have it for ~$80/yr. Defensive `.app`/`.io`/`.so` are ~$50 total more.*

After that, drop it.

### 15.3 If you're starting Phase 0 work

1. **Workstream 0.2 — User interviews.** Use `docs/Interview-Questions.md` literally. Don't rewrite the script — it was deliberately designed for stress-testing the universal-moment claim. Do help with recruitment outreach if asked.
2. **Workstream 0.3 — Transcription spike.** This is an engineer task. If the user doesn't have an engineer yet, this becomes your first blocker. Flag it.

### 15.4 If you're starting Phase 1 work

1. **Wireframes for the six screens.** They are listed in v1 Spec Section 7.3: Home/Library, Meeting view, Live overlay, Global chat, Pre-meeting prep card, Settings. Low-fi first. Don't pixel-polish.
2. **Architecture doc.** 5-10 pages with diagrams. Two engineers reading it independently should sketch the same system.

### 15.5 If you're starting Phase 3 build work

You'd be doing this in `/app/`. The structure isn't yet committed — likely:

```
app/
├── client/      (desktop app — Electron or native Mac)
├── server/      (backend services)
├── shared/      (shared types)
└── infra/       (deployment configs)
```

Don't start until Phase 0 + 1 + 2 are done. Build sequence in Master-Plan Section "Build v1".

---

## 16. Gotchas and Sharp Edges

Things that have already caused friction. Don't step on these again.

1. **OneDrive + Git can have sync conflicts.** Bash commands within the repo are fine, but two machines syncing the same .git folder simultaneously will cause grief. For a solo user, it works.
2. **GitHub Pages takes 30-90 seconds to redeploy after a push.** Polling the dashboard URL too soon will get the old version.
3. **Safari caches dashboard HTML aggressively.** The `<meta http-equiv="Cache-Control" content="no-cache">` is in place, but if you push an update, ask the user to hard-refresh (Cmd+Shift+R).
4. **`gh` CLI is NOT available in my (Claude's) bash sandbox.** Use raw `curl` against the GitHub API with the PAT. The user can use `gh` directly from their Mac terminal.
5. **`whois` is NOT installed in the sandbox.** For domain availability, use Verisign RDAP (`https://rdap.verisign.com/com/v1/domain/<name>` returns 404 for available, 200 for taken on `.com`) or DNS NS-record presence as a heuristic (no NS = possibly available).
6. **Renaming the repo doesn't automatically update browser localStorage.** Any user who had the dashboard configured before the rename needs the `#setup=` link to refresh their cached `cfg.repo`.
7. **The bash sandbox sometimes times out at 45 seconds** on long-running batches. Split big screening jobs into 2-3 calls.
8. **The dashboard's TODOS[] array and Master-Plan.md must stay in sync.** They were derived from the same source but are now separate. If you change one, change the other.

---

## 17. Cross-Reference: How These Documents Relate

```
                      ┌─────────────────────┐
                      │   v1-Product-Spec   │  ←─ Sets WHAT we're building (scope)
                      └──────────┬──────────┘
                                 │
                                 ▼
                      ┌─────────────────────┐
                      │    Master-Plan      │  ←─ Sets HOW we'll execute (phases)
                      └──────────┬──────────┘
                                 │
            ┌────────────────────┼────────────────────┐
            ▼                    ▼                    ▼
  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
  │  Dashboard       │  │  Interview-      │  │  Name-Decision   │
  │  (todos derived  │  │  Questions       │  │  (audit trail)   │
  │   from plan)     │  │  (Phase 0 tool)  │  │                  │
  └──────────────────┘  └──────────────────┘  └──────────────────┘
                                 │
                                 ▼
                      ┌─────────────────────┐
                      │      CLAUDE.md      │  ←─ Handoff (this file)
                      └─────────────────────┘
```

If you find a contradiction between docs: **Spec > Master Plan > Dashboard > everything else.** The spec is the source of truth for *what* we're building. The plan derives from the spec. The dashboard derives from the plan.

---

## 18. The Bar for "Done"

What it means for each phase to be "done." Don't promote to the next phase until these are met.

| Phase | "Done" means |
|---|---|
| 0 | A go/pivot/kill decision is documented in writing after all 3 Week-1 outputs are in hand. |
| 1 | A designer and an engineer can each describe v1 in one sentence using the same words. |
| 2 | Every engineering epic has a named owner and an effort estimate. The total fits the 4-month v1 budget within 10%. |
| 3 | The team has used Sevri internally for 4 weeks and misses it when offline. Hallucination <1%, time-to-note <60s, on the internal benchmark. |
| 4 | 100 strangers have used Sevri. At least 10 have written unsolicited "I love this" messages. |
| 5 | A user can complete "meeting → action item → done" without leaving Sevri. Pricing works in production. |
| 6 | 10,000 signups in 30 days, 25% week-4 retention, 5% free→paid conversion. |
| 7 | A new user opens Sevri and, within five minutes, sees their personal graph form — and never wants to go back to a fragmented set of apps. |

---

## 19. Final Notes

This handoff was written at the end of a long, multi-turn working session that took LifeOS through a brutal naming search to arrive at Sevri, set up the live repo, built the auto-syncing dashboard, and committed planning docs across the spec, plan, and interview guide. The product hasn't been built yet — Phase 0 is Monday. Everything in this repo is preparation for Monday.

When you (future Claude agent) pick this up, the user's goodwill is real but their patience for ground-relitigation is low. Honor their decisions. Push forward.

**The name is Sevri. The plan is the Master Plan. The first thing to do Monday is Phase 0.**

Good luck.

— Claude *(handoff dated 23 May 2026)*
