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

| Feature | Status | File |
|---------|--------|------|
| Guestlist (add/edit/delete/checkin) | ✅ Live | index.html |
| VIP list | ✅ Live | index.html |
| Tables list | ✅ Live | index.html |
| Map view (tap table → info sheet) | ✅ Live | mapa.html |
| Reservation from map | ✅ Live | mapa.html |
| Check-in from map | ✅ Live | mapa.html |
| Table linking (vincular mesas) | ✅ Live | mapa.html |
| Clear table (with confirm) | ✅ Live | mapa.html |
| Multi-map support | ✅ Live | editor.html |
| Push / Push All to Firebase | ✅ Live | editor.html |
| Objects: door, plant, divider, area | ✅ Live | editor.html |
| Area labels (editable text) | ✅ Live | editor.html |
| Object rotation | ✅ Live | editor.html |
| New map = empty | ✅ Live | editor.html |
| Duplicate map = exact copy | ✅ Live | editor.html |
| EN / NB / ES translation (all 3 files) | ✅ Live | all |
| Language saved per user in Firebase | ✅ Live | index.html |
| PWA installable | ✅ Live | manifest |
| Chair object (render logic) | 🟡 Button exists, no render | editor.html |
| TV / Stage / Sofa objects | 🔴 Not started | — |
| maxPeople per table | 🔴 Not started | — |
| Table states (free/reserved/full) | 🟡 Partial (color logic exists) | mapa.html |
| Staff App / Owner separation | 🔴 Not started | — |
| Owner Control Center | 🔴 Not started | — |
| Push notifications | 🔴 Not started | — |
| Products module | 🔴 Backlog | — |
| RRPP (promoters) module | 🔴 Backlog | — |
| Dashboard / Analytics | 🔴 Backlog | — |
| Payments | 🔴 Backlog | — |

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

### ✅ READY (defined, can start immediately)
- **Chair object render logic** — button exists in editor, needs SVG render + drag/resize
- **maxPeople per table** — field in editor properties panel → stored in Firebase → shown in map info sheet

### 🔨 IN PROGRESS
- **Sprint 1.5 — Architecture refactor** — separate Staff App from Owner Control Center

### 👁 COUNCIL REVIEW
*(empty)*

### 🧪 TESTING
*(empty)*

### ✅ DONE (Sprint 1 — Foundation)
- Multi-map ✓
- Push / Push All ✓
- Objects (door, plant, divider, area) ✓
- Area labels ✓
- Object rotation ✓
- New map empty / Duplicate exact copy ✓
- EN / NB / ES translation across all 3 files ✓
- Language saved per Firebase user profile ✓
- Reservation from map (add/edit/checkin) ✓
- Table linking (vincular) + clear table ✓

---

## SPRINT STATUS

| Sprint | Name | Status | Goal |
|--------|------|--------|------|
| Sprint 1 | Foundation | ✅ 90% complete | Stable base |
| Sprint 1.5 | Architecture Refactor | 🔨 Next | Separate Staff / Owner |
| Sprint 2 | Owner Control Center | ⬜ Planned | Full owner panel |
| Sprint 3 | Reservations | ⬜ Planned | maxPeople + states + full flow |
| Sprint 4 | Products | ⬜ Backlog | Products, packs, menu |
| Sprint 5 | Promoters (RRPP) | ⬜ Backlog | RRPP module |
| Sprint 6 | Analytics | ⬜ Backlog | Dashboard, stats |

---

## DEVELOPMENT RULES

1. Every feature must solve a real problem during a working night at the club
2. No agent approves alone — Nightclub Ops Manager has veto
3. No feature from backlog enters a sprint without Council review
4. Lead Developer audits real code state before estimating — no guessing
5. Update this file every time a feature ships or a decision is made
6. Never build twice — audit before implementing
7. Architecture decisions require CTO sign-off

---

## OPEN DECISIONS / TO DEFINE

- [ ] Exact split: which screens go to Staff App vs Owner Control Center?
- [ ] Does the editor stay as `editor.html` or merge into Owner Control Center?
- [ ] Naming convention for `owner.html` / `admin.html`
- [ ] Firebase security rules (currently open — needs tightening before first external client)
