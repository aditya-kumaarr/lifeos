# Name Decision — Preliminary Trademark + Domain Research

**Workstream:** P0.1 — Lock the name (trademark + domain checks)
**Researcher:** Claude (preliminary screen only — see legal note at end)
**Date:** 23 May 2026
**Status:** Research complete · awaiting founder decision on next-step naming.

---

## TL;DR — Verdict

**"LifeOS" is unusable as the brand. Kill it.**

The market is saturated with products already using the exact name. Multiple are direct competitors in the "AI-native operating system for your life" space. The major domain TLDs are taken by these competitors. There is at least one previous USPTO trademark filing (abandoned) and almost certainly common-law trademark rights belonging to several active users of the name.

The five fallback names in the spec (Cortex, Trace, Index, Loop, Ground) all suffer the same problem — they are common English words with `.com` already owned by major commercial entities and almost certainly conflicting software trademarks.

**Recommendation:** abandon the "common word" approach entirely. Move to a coined / invented name (the path taken by Notion, Granola, Figma, Roam, Tana, Mem, Reflect — every successful modern productivity product). Specific candidate names are proposed at the end of this doc for the next-round research.

---

## Why "LifeOS" is dead

### A. Active products already using "LifeOS" (most damaging finding)

| Product | URL | What it is | Conflict severity |
|---|---|---|---|
| **LifeOS Labs** | [lifeoslabs.com](https://www.lifeoslabs.com/) | AI research company. Explicitly building **"AI-native operating systems that move beyond fragmented applications"** — *the exact pitch in our spec*. | **CRITICAL** — direct competitor with the same vision and the same name. |
| **RunLifeOS** | [runlifeos.com](https://runlifeos.com/) | Tagline: *"Free AI Life Operating System — AI Scheduler, Habit Tracker, Goal Planner."* | **CRITICAL** — direct competitor. |
| **Life OS (lifeos.app)** | [lifeos.app](https://lifeos.app) | Live product, owns the `.app` TLD we wanted. | **HIGH** — owns a target domain. |
| **LifeOS (lifeos.ai)** | [lifeos.ai](https://lifeos.ai) | Live product, owns the `.ai` TLD we wanted. | **HIGH** — owns a target domain. |
| **LifeOS: Daily Habits & Focus** | [App Store id 6756681160](https://apps.apple.com/us/app/lifeos/id6756681160) | iOS productivity app, live on the App Store. | **HIGH** — App Store search collision; Apple may reject a duplicate name. |
| **LifeOS: Focus & Habit Tracker** | [Google Play](https://play.google.com/store/apps/details?id=com.buildkarmedia.lifeos) | Android productivity app, live. | **HIGH** — Play Store search collision. |
| **LifeOS: Subscriptions** | [App Store id 6748966574](https://apps.apple.com/us/app/lifeos-subscriptions/id6748966574) | iOS subscription tracker. | **MEDIUM** — different sub-niche, same name. |
| **LifeOS Pro** | [lifeos.vip](https://lifeos.vip/news/lifeos-pro-changelog.html) | Productivity tool. | **MEDIUM** |
| **LifeOS Dashboard** | [lifeosdashboard.com](https://www.lifeosdashboard.com/) | Productivity dashboard. | **MEDIUM** |
| **MyLifeOS** | [mylifeos.net](https://www.mylifeos.net/) | Tagline: *"Your Personal Life Operating System."* | **MEDIUM** |
| **Business LIFE OS** | [lifeos.business](https://www.lifeos.business/) | AI business OS for medical practices. | **MEDIUM** — adjacent vertical. |
| **LifeOS Global** | [lifeos.global](https://lifeos.global/) | Product. | **MEDIUM** |
| **LifeOS** | [lifeos.company](https://lifeos.company/) | Tagline: *"We build a better place for the human digital subconscious."* | **MEDIUM** |
| **Lif3OS** | [lif3os.com](https://www.lif3os.com/) | "Your Digital Butler" — variant spelling. | **LOW** |
| **LifeOS** (Steam) | [Steam app 3712650](https://store.steampowered.com/app/3712650/LifeOS/) | Video game. | **LOW** — different category, but App Store can still cite. |
| **LifeOS Genomics Corporation** | n/a | Biomedical / genomics company. | **LOW** — different industry. |
| **Agentic Notion Life OS** | [bettercreating.com/lifeos](https://www.bettercreating.com/lifeos) | Notion template. | **LOW** — different product type. |

That's **17 distinct entities** publicly using "LifeOS" or close variants. The two most damaging — LifeOS Labs and RunLifeOS — are direct competitors building essentially the same product we are.

### B. Domain status — every `lifeos.*` TLD is taken

| Domain | Status | Owner / use |
|---|---|---|
| `lifeos.com` | Parked / for sale | Sedo Parking (domainer). HTTP 403, listed for sale. |
| `lifeos.app` | Active product | Live "Life OS" product (title tag confirmed). |
| `lifeos.io` | Registered | Namecheap DNS, no active website served. |
| `lifeos.ai` | Active product | Live "LifeOS" product (title tag confirmed). |
| `lifeos.dev` | Registered | Cloudflare DNS. |
| `lifeos.so` | Registered | Cloudflare DNS, no active site. |
| `lifeos.xyz` | For sale | Listed as a premium domain on sale page. |

Buying `lifeos.com` from Sedo is **theoretically possible** but typically costs anywhere from **$5,000 to $50,000+** for a five-letter dictionary-style domain — and you'd still have all the trademark and search-collision problems below.

### C. Trademark status

- **USPTO — LifeWallet, LLC** filed `LIFEOS` (serial 86940965) on March 15, 2016 covering "operating system programs, computer operating systems, mobile operating systems, computer software for health, mindfulness, wellness, and medical-related information." **Abandoned October 23, 2017** for failure to file a Statement of Use. *(Source: [Justia Trademarks](https://trademarks.justia.com/869/40/lifeos-86940965.html))*
- **USPTO — serial 97878013** appears as a more recent "LifeOS" filing on [Trademarkia](https://www.trademarkia.com/lifeos-97878013). Could not confirm current status from public search results; would need a direct lookup via [USPTO TSDR](https://tsdr.uspto.gov/) — recommend a lawyer pull the full file history.
- **Common-law rights** apply to all of the active products listed in section A regardless of whether they have registered marks. In the US, mere use in commerce gives the user enforceable rights. With ~17 entities using the name, multiple parties have plausible common-law claims.
- **EUIPO + IP India** — I could not verify these from public web search alone. Given the saturation in the US market alone, additional jurisdictions are moot for the kill decision.

### D. Operational consequences if we proceed with "LifeOS" anyway

- **App Store / Play Store rejection risk.** Apple and Google both reject apps with confusingly similar names to existing apps. Multiple live "LifeOS" apps exist on both stores.
- **SEO / discovery is impossible.** "LifeOS" Google search is already dominated by competitors. We'd never rank.
- **Customer confusion.** Beta users would conflate us with LifeOS Labs or RunLifeOS.
- **Legal exposure.** Any of the active common-law users could send a cease-and-desist, especially LifeOS Labs (direct competitor with apparent funding).
- **Domain cost.** No clean TLD is available; premium acquisition would cost five figures.

---

## Shortlist (Cortex / Trace / Index / Loop / Ground) — also blocked

All five are common English words. All five have `.com` and at least 2 other major TLDs registered. All five have high-likelihood software/AI trademark conflicts.

| Name | `.com` | `.app` | `.io` | `.ai` | Known conflicts in software/AI |
|---|---|---|---|---|---|
| Cortex | Taken | Taken (atom.com hosting) | Taken | Taken (akam.net = Akamai-hosted, big company) | Cortex.ai (ML platform), Cortex Inc (BI), Cortex Labs (AI), Cortex Diagnostics |
| Trace | Taken (Cloudflare) | Taken | Taken | **Apparently available** | Trace Genomics, Trace.com (multiple), Trace ID |
| Index | Taken | Taken (Google Cloud-hosted) | not checked | not checked | Index Exchange (adtech), Index by FTX, dozens of others |
| Loop | Taken (AWS) | Taken | Taken (AWS) | not checked | Loop Capital, Loop Industries, Loop (Salesforce), Loop Returns |
| Ground | Taken | Taken | Taken | not checked | Many — too common to enumerate |

**`trace.ai` is the only target domain that appears unregistered** in this set, but: (a) `.ai` domains carry $150-180/year renewal (much higher than `.com`), (b) "Trace" still has heavy software TM conflict, (c) it's a common dictionary word with low brandability.

**Recommendation: do not pick any of these.** Same trap as LifeOS, just with different specifics.

---

## Path forward — coined / invented names

Every successful modern productivity / second-brain product uses either an invented word or an unusual repurposing of one. There's a reason:

- **Notion**, **Granola**, **Figma**, **Asana**, **Roam**, **Mem**, **Tana**, **Reflect**, **Linear**, **Slack** — none are common dictionary words associated with their product space. The naming move that wins is *standing apart*, not *describing*.

For our product (AI meeting capture + personal knowledge graph + cross-app brain), the brand should evoke **memory**, **connection**, or **clarity** without being descriptive. Below are 8 candidate names that should be researched next.

### Candidates to research (preliminary screen pending)

| Name | Evocation | Pronunciation (English / Hindi) | First-pass risk |
|---|---|---|---|
| **Mneme** | Greek goddess of memory; literally "memory" | "neem-ee" / similar | Mythic, distinctive, short |
| **Memora** | "memory + aurora"; soft, made-up | "meh-MO-ra" / works in both | High brandability |
| **Cogniq** | "cognition + unique"; tech-feeling | "COG-nick" / works | Crisp, modern |
| **Threadly** | thread / weaving metaphor | "THRED-lee" / works | Mid; product-y feel |
| **Synapt** | synapse-based; AI-adjacent | "SY-napt" / works | Strong but slightly clinical |
| **Capsoul** | capsule + soul; memory keeper | "CAP-soul" / works | Distinctive, soft |
| **Vivora** | living + aurora; brand-y | "vi-VOR-a" / works | High brandability |
| **Knosis** | gnosis (knowledge); short | "NO-sis" / works | Mythic feel; check spelling collisions |

Each of these still needs the same depth of research that was done on LifeOS — domain availability across `.com / .app / .io / .ai`, USPTO/EUIPO/IP India searches, App Store + Play Store conflict scans, common-law product scans. Pick **two top candidates** and a Plan-B fallback, then do that work.

---

## Recommended next action

1. **Discard "LifeOS" everywhere.** Update the spec, the master plan, the README, the dashboard. (I can do this with one find-and-replace once a replacement is chosen.)
2. **Pick 2 candidates** from the table above (or propose your own coined names — the table is a starting point, not a constraint).
3. **I'll do the same-depth research** on those 2 candidates and produce a fresh decision doc. That cycle takes ~30 minutes.
4. **Once a candidate clears,** acquire the domain immediately (typical `.com` for a coined name is $10-15/year if available, premium domainers may want $1k-$5k for premium coined names).
5. **Engage a trademark lawyer** in your target jurisdictions (US, EU, India) to do a *real* clearance search. Lawyers run TESS, EUIPO, Indian IP databases with proper Boolean logic, design-mark search, and dilution analysis. **This research doc is not a legal clearance** — it's a preliminary kill-screen. A $500-$1,500 lawyer review before launch is cheap insurance.

---

## Legal note

This document is a preliminary research screen using publicly available sources. It is **not a legal opinion** and is **not a trademark clearance**. A registered trademark attorney must perform a formal clearance search before any name is committed to in marketing, product, or domain purchases. The author of this document is not a lawyer.

Specifically, the following were **not** done:
- Comprehensive Boolean search across all 45 Nice trademark classes.
- Design-mark / phonetic-equivalent search.
- Search of foreign-language trademark databases (CTM, WIPO Madrid, Indian IP India, etc.) by class.
- Common-law trademark search beyond top web results.
- Review of pending applications, oppositions, or recent filings.

---

*End of decision doc. Pick two candidates and I'll start the next research round.*
