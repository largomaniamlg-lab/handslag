# LARGOMANIA — MASTER CONTEXT
> Load this file at the start of every new session together with Council.md.
> Last updated: 2026-07-08

---

## THE TEAM

| Role | Who | Responsibility |
|------|-----|----------------|
| CEO / Founder | Joona | Club knowledge, business vision, final decisions |
| CPO | ChatGPT | Roadmap, sprints, UX philosophy, product priorities |
| Lead Developer | Claude | Implementation, refactor, bug fixes, real codebase audit |
| CTO | Claude (Council mode) | Architecture, Firebase, scalability |
| UX Designer | Claude (Council mode) | Flows, screen simplification, fewer clicks |
| Ops Manager | Claude (Council mode) | Real-night veto — "does this help at 01:30 Saturday?" |
| Business | Claude (Council mode) | Nyx analysis, pricing, white label |
| QA | Claude (Council mode) | Break things before they ship |
| Documentation | Claude | Keeps MASTER_CONTEXT.md and Council.md updated |

**Council trigger:** Start a message with `Council:` to activate all agents.
**Veto rule:** Nightclub Ops Manager can block any feature regardless of other votes.

---

## THE PRODUCT

**Name:** Largomania (platform) / Handslag (client brand)
**Model:** White label — each club uses its own brand. "Powered by Largomania" footer.
**Revenue:** Implementation fee + monthly subscription
**Competitor:** Nyx (primary), SevenRooms, OpenTable
**Repo:** https://github.com/largomaniamlg-lab/handslag
**Live app:** https://largomaniamlg-lab.github.io/handslag/

**Philosophy:** Every feature must solve a real problem during a working night at the club.

---

## TECH STACK

- Firebase Realtime Database
- Vanilla JS + SVG (no framework)
- PWA (installable, works offline)
- GitHub Pages (hosting)
- Three files: `index.html` (Staff App), `mapa.html` (Map view), `editor.html` (Owner editor)

**Firebase structure:**
```
events/{date}/{cat}/{guestId}   → guestlist / vip / tables
mapa_v2/__maps                  → map registry
mapa_v2/__active                → which map is live
mapa_v2/{mapId}/tables          → table positions
mapa_v2/{mapId}/objects         → decorative objects
mapa_v2/{mapId}/room            → room dimensions
users/{uid}/lang                → user language preference
users/{uid}/role                → owner / admin / maline
```

---

## CURRENT STATE — FEATURE AUDIT

### ✅ STABLE (tested in production, real devices)

| Feature | File |
|---------|------|
| Guestlist (add/edit/delete/checkin) | index.html |
| VIP list | index.html |
| Tables list | index.html |
| Map view (tap table → info sheet) | mapa.html |
| Reservation from map | mapa.html |
| Check-in from map | mapa.html |
| Table linking / multi-link (1-N) | mapa.html |
| Unlink individual table | mapa.html |
| Clear table (with confirm) | mapa.html |
| Table rename (owner only, from map) | mapa.html |
| "Ver como" preview mode (owner) | index.html |
| Multi-map support | editor.html |
| Push / Push All to Firebase | editor.html |
| Objects: door, plant, divider, area | editor.html |
| Area labels (editable text) | editor.html |
| Object rotation | editor.html |
| New map = empty | editor.html |
| Duplicate map = exact copy | editor.html |
| EN / NB / ES translation (all 3 files) | all |
| Language saved per user in Firebase | index.html |
| Firebase real-time sync | all |
| PWA installable | manifest |

### 🟡 IN PROGRESS / PARTIAL

| Feature | Status | File |
|---------|--------|------|
| Chair object (render logic) | Button exists, no SVG render | editor.html |
| Table states (free/reserved/full) | Color logic exists, not complete | mapa.html |

### 🔴 NOT STARTED

| Feature | Priority |
|---------|----------|
| maxPeople per table | Sprint 3 |
| TV / Stage / Sofa objects | Backlog |
| Staff App / Owner separation | Sprint 1.5 |
| Owner Control Center | Sprint 2 |
| Push notifications | Backlog |
| Products module | Sprint 4 |
| RRPP (promoters) module | Sprint 5 |
| Dashboard / Analytics | Sprint 6 |
| Payments | Backlog |

---

## SPRINT STATUS

| Sprint | Name | Status | Goal |
|--------|------|--------|------|
| Sprint 1 | Foundation | ✅ Complete | Stable base |
| Sprint U1 | User Validation | 🟢 Active (ends ~2026-07-13) | Observe real users, no new features |
| Sprint 1.5 | Architecture Refactor | ⏸ Paused until after U1 | Separate Staff / Owner |
| Sprint 2 | Owner Control Center | ⬜ Planned | Full owner panel |
| Sprint 3 | Reservations | ⬜ Planned | maxPeople + states + full flow |
| Sprint 4 | Products | ⬜ Backlog | Products, packs, menu |
| Sprint 5 | Promoters (RRPP) | ⬜ Backlog | RRPP module |
| Sprint 6 | Analytics | ⬜ Backlog | Dashboard, stats |

---

## USER VALIDATION SPRINT (U1)

**Period:** 2026-07-08 → ~2026-07-13 (Sunday real-world test with team)
**Rule: NO new features. Critical bugs only.**

**Objective:** Observe how real staff use the app during a full service night.

**Feedback classification:**
- `Bug` — something broken
- `UX` — friction or confusion
- `Feature` — new request
- `Improvement` — existing feature that needs polish
- `Future` — idea for backlog

**Key question to ask the team:** "What made you lose time?"
(NOT "what features do you want?" — that produces noise)

**Observation log template:**
```
HH:MM — [who] — [what happened] — [category]
```

---

## SCRUM BOARD

### 🗂 BACKLOG
- TV / Stage / Sofa / Bar objects in editor
- Push notifications (FCM)
- Products module
- RRPP (promoters) module
- Dashboard / Analytics
- Billing / payments
- Branding page ("Powered by Largomania")
- Onboarding flow for new clubs
- Multi-club support
- Chair object render logic

### ✅ READY (defined, waiting for U1 to end)
- **maxPeople per table** — field in editor → stored in Firebase → shown in map info sheet
- **Staff App / Owner separation** — split index.html into Staff and Owner views

### 🔨 IN PROGRESS
*(paused during U1 — no active development)*

### 🧪 TESTING / VALIDATION
- **Sprint U1** — real-world use with club team (target: Sunday 2026-07-13)

### ✅ DONE
- Multi-map ✓
- Push / Push All ✓
- Objects (door, plant, divider, area) ✓
- Area labels ✓
- Object rotation ✓
- New map empty / Duplicate exact copy ✓
- EN / NB / ES translation across all 3 files ✓
- Language saved per Firebase user profile ✓
- Reservation from map (add/edit/checkin) ✓
- Table linking multi (1-N) + unlink individual ✓
- Clear table ✓
- Table rename (owner, from map) ✓
- "Ver como" preview mode (owner only) ✓
- Own role change redirects to preview mode ✓

---

## KNOWN ISSUES

### ✅ RESOLVED

| Date | Issue | Root Cause | Fix |
|------|-------|------------|-----|
| 2026-07-08 | Mobile app appeared not to update after changes | PWA cache / session — not a logic bug. Firebase sync was working correctly. | Hard reload / clear cache on device |
| 2026-07-08 | Links persisting after unlink | `doLink` used stale `_currentInfoTable` reference after Firebase listener replaced the `tables` array. `_saveTablesFirebase` was serializing the NEW array without the second link. Also: migration guard `(!t.links \|\| !t.links.length)` re-triggered on empty array after unlink. | Both fixed: resolve by ID from live `tables` array; migration guard changed to `!('links' in t)` |
| 2026-07-08 | Owner lost their role after using Admin panel role editor | No safeguard against changing own role. | Own role change now activates "Ver como" preview mode instead of writing to Firebase |

### 🔴 OPEN
*(none — all known bugs resolved)*

---

## DEVELOPMENT RULES

1. Every feature must solve a real problem during a working night at the club
2. No agent approves alone — Nightclub Ops Manager has veto power
3. No feature from backlog enters a sprint without Council review
4. Lead Developer audits real code state before estimating — no guessing
5. **Update MASTER_CONTEXT.md after every sprint completion or resolved incident**
6. Never build twice — audit before implementing
7. Architecture decisions require CTO sign-off
8. During User Validation Sprints: observe, don't build. Log everything.

---

## AUTO-UPDATE RULE

After every sprint or major incident, Claude updates:
- `MASTER_CONTEXT.md` — feature audit, sprint status, known issues
- `Council.md` — sprint status table
- Changelog (in commit messages)

The documentation must always reflect the real state of the project.

---

## OPEN DECISIONS / TO DEFINE

- [ ] Exact split: which screens go to Staff App vs Owner Control Center?
- [ ] Does the editor stay as `editor.html` or merge into Owner Control Center?
- [ ] Naming convention for `owner.html` / `admin.html`
- [ ] Firebase security rules (currently open — needs tightening before first external client)
- [ ] Feedback form / observation log format for Sunday test
