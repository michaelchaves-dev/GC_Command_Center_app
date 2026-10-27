# Granite State Gem — GC Command Center

**Slice 1 — front-end rebuild, demo mode.** A single static page, no build
step, no backend, $0 to run or host.

> **Demo / pilot-honest:** Everything in this build is sample demo data —
> fictional projects, people, budgets, and dates created for illustration.
> It is **not** a live production system and contains **no real client
> data**. The page itself is labeled "Demo" for the same reason.

Target repo (created by Michael, empty as of Oct 26, 2026):
`github.com/michaelchaves-dev/GC_Command_Center_app` — this local build
has **not** been pushed there yet. Nothing ships publicly until Michael
approves the exact content.

## What's in Slice 1

Faithful rebuild of the reference app (the Perplexity build at
granitestategem.pplx.app), per
`~/workspace/granitestate-gem-buildout-2026-10-26.md`:

- **Project list** — 4 realistic New Hampshire demo projects (kitchen
  remodel in Concord, deck build in Meredith, historic addition in
  Portsmouth, bathroom renovation in Keene), contracts in the
  $48,750–$285,000 range.
- **Per-project tabs** — Overview / Budget / Schedule.
  - Overview: progress, phase, team, blockers (e.g. a delayed stone
    slab), recent updates.
  - Budget: line items by category/vendor with budgeted vs. spent,
    remaining, over/under variance, and totals.
  - Schedule: dated trade visits with vendor, task, and status
    (Done / Booked / Pending / Delayed), plus a working
    **Schedule-a-Trade** form in contractor roles (adds to the list
    in-page only; nothing is sent).
- **Role switching** — Owner / GC / Admin / Homeowner / Subcontractor /
  Vendor. The role changes what's visible:
  - Owner, GC, Admin: full working view (all projects, full budgets,
    scheduling).
  - Homeowner: read-only, limited to their own project, budget
    *summary* only (no vendor line items or internal notes).
  - Sub / Vendor: read-only schedule and overview; budget tab hidden.
- **Contractor view / Client view** toggle mirroring the reference app.
- **Public client mode (standout feature)** — passcode-gated,
  account-free, read-only view of the client's own project: progress,
  what's next, and contractor updates. No budgets, no other projects.
  - **Demo passcode: `GEM2026`** — labeled as a demo passcode in the UI
    itself. A production build would never display it.

Branding: deep navy + gold, "Granite State Gem — GC Command Center,"
with the Subtract Architect Studios tagline "Intelligence by
Subtraction."

## How to run

Option 1 — just open it:

```bash
open index.html        # macOS
xdg-open index.html    # Linux
```

Option 2 — local web server (closer to how it will be hosted):

```bash
cd ~/workspace/builds/gc-command-center
python3 -m http.server 8000
# then visit http://localhost:8000 in a browser
```

No dependencies, no install, no build step. All state is in-memory demo
data in the page's JavaScript — refreshing resets any Schedule-a-Trade
additions.

## Files

- `index.html` — the entire app (markup, styles, demo data, logic).
- `README.md` — this file.

## Next slices (not in this build)

- **Slice 2 — Real data layer (Michael's call):** accounts +
  persistence (e.g. Supabase free tier) so a real GC can run a real
  project. Cost/complexity review before building. The Perplexity
  backend/data do **not** transfer — this rebuild replaces them.
- **Slice 3 — Domain:** point `granitestategem.com` DNS at the Vercel
  deployment once Slice 1/2 is approved as the public face (deploy
  itself also waits on Michael's approval of the exact content).
- **Slice 4 — Productize:** demo script, pricing, and pilot framing to
  sell this to other GCs / home-services businesses under Subtract
  Architect Studios.
