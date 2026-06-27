# Gamification Draft — Changelog

Experimental draft exploring two gamification ideas from the Phase 2 brief. Independent of the v3 screens.

- **Idea A** — Arrow shot tracking (entry at sign-out → stats on Home + heatmap on Me)
- **Idea B** — Staff-entered verified scores (shown on Me)

## Session additions (2026-06-20)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 1 | G01 Home | Arrow Stats card | New card: current-month arrows + trend chip + 4-month bar chart (Idea A) | ✅ |
| 2 | G05 Sign-out | Session details | One new optional "Arrows shot" field added to the existing v3 arrows/notes step (Idea A) | ✅ |
| 3 | G06 Me | Arrow Activity + Verified Scores | New: arrows heatmap + avg/session + lifetime; staff-entered verified scores list (Ideas A & B) | ✅ |

## Session additions (2026-06-21)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 4 | Index | Draft index | Removed v3 reference link; collapsed the Idea A / Idea B sections into a single 3-screen list | ✅ |
| 5 | G01 Home | Entire screen | Removed file; Home no longer part of this showcase (Arrow Stats scoped to Me tab only) | ✅ |
| 6 | G06 Me | Arrow activity mini-stats | "avg per session" → "sessions past 30 days" (value: 13) | ✅ |
| 7 | G06 Me | Verified scores — row format | Added category sub-label per row (e.g. Recurve — 70m Open) | ✅ |
| 8 | G06 Me | Verified scores — data | Updated to /720 max score; realistic international competition names | ✅ |

## Session additions (2026-06-27 follow-up)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 12 | G06 Me | Heatmap — metric toggle | Remove Arrows/Sessions toggle. Merge into single view: cell intensity = attendance (sessions that day, always populated), small centred dot overlay = arrows logged (hollow/absent if none, solid if logged). Attendance is primary; arrows is secondary layer. | ✅ |
| 13 | G06 Me | Heatmap — tap interactions | Tap a day cell → anchored popover showing: Date, Arrows shot (or —), Sessions attended. Tap a month label → anchored popover showing: Month, Arrows shot (monthly total), Sessions attended (monthly total). Popover dismisses on tap outside. | ✅ |
| 14 | G06 Me | Stat cards — reorder + default | Default stat cards reordered: (1) Arrows this week, (2) Arrows this month, (3) Sessions this month. Cards visible by default; popover replaces the need for week/month drill-down in cards. | ✅ |
| 15 | G06 Me | Verified scores — subtitle line | Change subtitle from "Recurve — 70m Open" format to "Bow style · Distance · Face size" (e.g. "Recurve · 70m · 122cm"). Competition name stays as title, date stays below. | ✅ |
| 16 | G06 Me | Heatmap — visual encoding follow-up | Revised heatmap encoding: cell shading now represents arrows shot; bordered cells mark days where the archer shot. Removed the dot overlay. Session count remains available in day/month popovers. | ✅ |
| 17 | G01 Home / G06 Me | Hall of Fame placement | Reintroduced Home screen and moved the full Hall of Fame section there. Me now keeps Arrow Activity and Verified Scores only. | ✅ |
| 18 | G01 Home | Hall of Fame tab labels | Renamed customer-facing leaderboard tabs from Behavioral / Performance to Training / Scores. | ✅ |
| 19 | G01 Home | Rest-of-page placeholder | Added/clarified the Home placeholder to show that Alerts, Announcements, Range sign-in, and Upcoming bookings are unchanged and outside this showcase. | ✅ |
| 20 | G06 Me | Verified scores row hierarchy | Updated rows so bow style + scoring format is the headline, competition is the sub-headline, and date sits at the bottom; examples now cover Recurve, Compound, and Barebow formats. | ✅ |
| 21 | G01 Home / G06 Me | Bottom nav links | Linked Home on the Me wireframe to G01 Home, and linked Me on the Home wireframe back to G06 Me. | ✅ |
| 22 | G01 Home | Scores bow filter | Limited the Scores leaderboard bow filter to Recurve, Compound, and Barebow. | ✅ |
| 23 | G01 Home | Hall of Fame tab label | Renamed the customer-facing Scores tab to Competition. | ✅ |
| 24 | G01 Home | Competition period tabs | Reordered period tabs so This quarter is first and active by default, with All-time second. | ✅ |
| 25 | G01 Home | Competition row content | Simplified Competition leaderboard rows to show name, score, competition title, and date only; removed format line from each row. | ✅ |
| 26 | G01 Home | Competition personal best handling | Folded personal-best context into the All-time leaderboard by showing the archer's own ranking as the highlighted self row, instead of using a separate My best tab. | ✅ |
| 27 | G01 Home | Competition format filter | Changed the Competition filter from bow-style-only chips to scoring-format chips that combine bow style, distance, and face size so rankings compare like with like. | ✅ |
| 28 | G01 Home | Competition mock states | Added format-specific mock leaderboard data, including cases where Caleb has a highlighted rank and cases where he has no verified score for the selected format. | ✅ |
| 29 | G01 Home | Competition record copy | Changed Competition overflow copy from members to verified scores and updated sample data to show that one archer can hold multiple ranked score records. | ✅ |
| 30 | G01 Home | Competition empty state copy | Standardized no-score empty states to "No verified score for this format yet" and removed the extra "No ranking yet" heading. | ✅ |

## Session additions (2026-06-27)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 9 | G06 Me | Arrow activity — stats row | Fixed stats hierarchy per spec: month total (1,240) → week total (312) → sessions this month (13); was showing lifetime total + sessions past 30 days | ✅ |
| 10 | G06 Me | Arrow activity — metric toggle | Added Arrows / Sessions segmented control at top of heatmap card (client asked: can it toggle metric values?) | ✅ |
| 11 | G06 Me | Hall of Fame section | New section: Behavioral leaderboard (sessions attended, quarterly, top 3 + self rank) + Performance leaderboard (bow type filter, all-time / quarterly toggle, score rows with distance + face size + competition name) | ✅ |
