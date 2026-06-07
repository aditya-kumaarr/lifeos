# Sevri

> An operating system for your life. v1 starts as an AI-powered meeting-notes module that builds a personal knowledge graph from everything you say — and grows into the single app where your todos, expenses, notes, and memory all live.

This is the working repository for the Sevri product. It currently holds planning documents, the v1 spec, and an interactive build dashboard. Once we start building the app itself, the code will live alongside everything else in this same repo.

---

## Repository layout

```
.
├── docs/                       — Source-of-truth documents
│   ├── Master-Plan.md          — 12-month execution plan, phase by phase
│   ├── v1-Product-Spec.md      — v1 product specification
│   └── Interview-Questions.md  — Phase 0 user-research field guide
│
├── dashboard/
│   └── index.html              — Interactive build dashboard
│                                 (todos derived from Master-Plan.md)
│
├── state/
│   └── dashboard-state.json    — Persistent dashboard progress
│                                 (auto-synced when GitHub is configured)
│
├── app/                        — (placeholder) v1 application code goes here
│
└── README.md                   — This file
```

---

## How to use the dashboard

Open `dashboard/index.html` in your browser (Chrome/Edge recommended). The dashboard reads the Master Plan as 49 actionable todos grouped by phase. Tick the box on each one as you finish it.

### Without sync (default)
Progress persists in your browser's localStorage. Good for trying it out, but resets if you switch machines or clear browser data.

### With GitHub sync (recommended for long-term)
Click the **Sync settings** gear. Enter your GitHub username, the repo name (`sevri` if you used the default), and a Personal Access Token (see below). Once connected:

- Every checkbox change is auto-saved to `state/dashboard-state.json` in this repo.
- Open the dashboard on any machine, paste the same token, and your progress is right there.
- Eight months from now, if you mark "Phase 0 done" today, it'll still be ticked.

### Creating a GitHub PAT

1. Go to **<https://github.com/settings/tokens/new?scopes=repo&description=Sevri%20Dashboard>** — that link pre-fills the right scope (`repo`).
2. Set an expiration that you're comfortable with (90 days minimum; 1 year is fine for personal use).
3. Click **Generate token** and copy the value (starts with `ghp_…`).
4. Paste it into the dashboard's Sync settings modal.

The PAT lives only in your browser's localStorage. It is never sent anywhere except to GitHub's API.

---

## Companion documents

- **[Master Plan](./docs/Master-Plan.md)** — the 12-month execution plan; the source of truth for everything in the dashboard.
- **[v1 Product Spec](./docs/v1-Product-Spec.md)** — the product spec the plan is executing against.
- **[Interview Questions](./docs/Interview-Questions.md)** — the field tool for the Phase 0 user-research workstream.

The dashboard's "Conduct 15 user interviews" todo opens the interview guide inline, so you can use it as a live field tool during real conversations.

---

## What's next

After the planning phase, the app itself will be built in `/app`. Likely structure (TBD during Phase 2):

```
app/
├── client/      — desktop client (Electron or native)
├── server/      — backend services (ingestion, transcription, LLM, graph)
├── shared/      — shared types and protocols
└── infra/       — IaC, deployment configs
```

Build phasing lives in the Master Plan. Engineering kickoff is Week 4.

---

## Status

- [x] v1 product spec drafted (May 2026)
- [x] Master plan drafted (May 2026)
- [x] Interview guide drafted (May 2026)
- [x] Build dashboard live with GitHub sync (May 2026)
- [x] Name locked — **Sevri** (May 2026)
- [ ] Phase 0 — De-risk (Week 1) starts Monday
- [ ] `sevri.ai` domain purchased
- [ ] 15 user interviews complete
- [ ] Transcription quality validated
- [ ] Go / pivot / kill decision made
- [ ] Phase 1 onward — track via the dashboard

---

*This repo is currently a planning workspace. Once Phase 0 is complete, app code begins landing in `/app`.*
