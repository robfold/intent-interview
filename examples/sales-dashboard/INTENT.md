# Sales Team Dashboard — Confirmed Intent

Confirmed with the user on 2026-11-21 via interview. Nothing has been built yet.

## Confirmed (user's answers)

- **Outcome:** A screen a manager puts up in the weekly team meeting, showing deals whose
  close date keeps getting pushed back, plus a small strip at the top with this quarter's
  closed amount vs. target.
- **Reason:** Stuck deals slip by. Meetings cover totals, and stalled deals aren't noticed
  until it's too late.
- **Success:** No end-of-quarter surprises. No deal we were counting on falls out of the
  quarter without having been discussed weeks earlier.
- **Limits:**
  - Read-only on HubSpot. It never changes a deal, date, or note.
  - Not a blame board. Deal owners are shown, but reps are never ranked.
- **Out of scope:** Per-rep breakdowns, a full pipeline overview, forecasting, a wall-TV
  leaderboard, and any data entry by reps.
- **"Stuck" means:** The expected close date has been pushed back one or more times.
- **Data source:** HubSpot (deals and close-date property history).

## My judgments (not user answers)

- HubSpot keeps a property history, so the number of close-date pushes per deal can be
  computed from `closedate` history.
- The user did not mark "team only, no public link" or "no new tools for reps" as hard limits.
  Default assumption: keep access limited to the team anyway.

## Open items (decide at build time)

- Threshold: does one push flag a deal, or two or more? Is there a minimum deal size?
- Where the quarterly target comes from (HubSpot goals or a configured number).
- How HubSpot access works (private app token, scopes) and where the dashboard is hosted.
- Sort order of the list (number of pushes, deal amount, days slipped).
