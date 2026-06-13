# v2 Wireframe Changelog

Design review session: 2026-06-06  
Reviewer: Daniel + partner  
Implemented in: `phase2-designs/v2/`  
Last updated: 2026-06-13

---

## Status key
- ✅ Done — implemented in v2
- 🔲 Pending — needs implementation
- 📝 Note only — behaviour/engineering note, no UI change required
- ➖ Deferred — explicitly skipped for now

---

## Original review items

| # | Screen | Element | Change / Note | Status |
|---|--------|---------|---------------|--------|
| 1 | Wallet / Credits card | `Top up` button (`.topup-btn`) in card footer | **Remove** | ✅ Done |
| 2 | Wallet / Passes section | Section scope | **Include Locker passes** — Locker Access section added with lock icon and same pass card component | ✅ Done |
| 3 | Wallet / Passes section | Renew button | **Remove** | ✅ Done |
| 4 | Wallet / Passes section | Pass visibility rules | Show Expiring, Active, Unactivated. Show recently expired (past 3 months) only if no current passes exist. Example expired card added (30D West Coast Pass, greyed out) | ✅ Done |
| 5 | Wallet / Passes section | Pass icon (`.pass-ico`) | Archery arrow icon for range passes; lock icon for locker access | ✅ Done |
| 6 | Wallet / Pass cards | Card proportions | Match credit wallet card ratio | ➖ Deferred |
| 7 | Home / Alerts section | Action buttons (`.a-act`) on all alerts | **Remove all** | ✅ Done |
| 8 | Home / Announcements section | Both `INFO` announcement cards | **Remove** — announcement maintenance feature not ready on admin portal | ✅ Done |
| 9 | Home / On-site sign-in card (`.card.signin`) | Reference | Maps to `05 Sign-in + Sign-out.html` | 📝 Note only |
| 10 | Book / Step 1 — Activity & venue (`#p0`) | Bottom of panel | **Add T&C paragraph** (copy TBD) | ✅ Done |
| 11 | Book / Step 2 — Date & timeslots (`#p1`) | Slot row (`.slot-row`) | **Replace** availability bar + count with start–end time range (e.g. `9:00 AM – 11:00 AM`). Dev note placed in wireframe. | ✅ Done |
| 12 | Book / Step 4 — Review (`#p3`) | `Type` row (`.rv-row`) | **Remove** | ✅ Done |
| 13 | Book / Step 4 — Review (`#p3`) | Credit deduction section (`.cred-section`) | **Remove** "Hours booked" and "Rate" rows. Keep: credit type badge (2-letter code), Current balance, Amount to deduct, Balance after. | ✅ Done |
| 14 | Book / Step 4 — Review (`#p3`) | Credit deduction section (`.cred-section`) | **Add** pay with / without credits toggle. "Without credits" → deduction shows $0 with "Payment settled at sign-out" note. | ✅ Done |
| 15 | Global / App header (`.app-header`) | Notification bell button (`.icon-btn`) | **Remove** | ✅ Done |
| 16 | Home / Upcoming Bookings section header | "See all" button (`.sec-link`) | **Remove** | ✅ Done |
| 17 | Home / Range Busyness section header | "View all" button (`.sec-link`) | Navigates to Bookings tab (2nd bottom nav item) | 📝 Note only |
| 18 | Profile switcher sheet (`#sheet`) | "Manage profiles" button (`.add-prof`) | **Remove** | ✅ Done |
| 19 | Profile switcher sheet (`#sheet`) | Post-switch behaviour | After selecting a profile, redirect to Home regardless of which screen the switch was triggered from | 📝 Note only |
| 20 | Login screen | New screen | After login, show profile selector. If only 1 profile exists, skip selector and go straight to Home | ✅ Done |
| 21 | Global / All tabs | Pull-down gesture | **Pull-to-refresh** refreshes the current tab's data | 📝 Note only |
| 22 | Sign-out flow | "Signed out" success modal (`#soSheet`) | **Remove** entirely. Dev note placed | ✅ Done |
| 23 | Sign-out flow | "Confirm Sign Out" button | Navigates to a temporary session bill page — all bookings, credits in/out, outstanding payable. Back → Home. One-time only. Dev note placed | ✅ Done |
| 24 | Sign-out / Session bill page | Undo action | **Add "Undo Sign Out" button** — cancels sign-out and returns user to active session. Only available before navigating away. Dev note placed | ✅ Done |
| 25 | Home / On-site sign-in card (`#homeSignin`) | Booking detected tile | **Move into the card**, below location picker. Appears once location is selected. Tapping opens sign-in sheet | ✅ Done |
| 26 | Sign-in sheet (`#siSheet`) | Sheet body | **Simplify** — remove booking banner. Show only: arrow count + range slider, session notes field | ✅ Done |
| 27 | Account / Profiles section | Active profile tick mark (`.pr-badge`) | **Remove** checkmark from all profile rows | ✅ Done |
| 28 | Account / Delink profile sheet (`#sheetDelink`) | Behaviour notes | (1) No verification email on delink. (2) Member portal: link to new Nockhub account only. (3) Admin portal: link to any existing account. Dev note placed | 📝 Note only |
| 29 | Account / Profile edit form | Secondary contact Name field | **Split** into First name and Last name fields | ✅ Done |
| 30 | Shop / Catalog | Credit Packages list | Package visibility is profile-dependent | 📝 Note only |
| 31 | Shop / Catalog | Categories | **Add "Locker Access"** as new category alongside Credit Packages. Dev note placed | ✅ Done |
| 32 | Shop / Purchases | Filter bar (`.hist-filter`) | **Remove** All / Credits / Passes / Activities filter tabs | ✅ Done |
| 33 | Shop / Purchases | Purchase history rows (`.hist-row`) | **Make tappable** — opens bottom sheet with full purchase details | ✅ Done |

---

## Session additions (2026-06-07)

Additional improvements made during implementation, beyond the original review scope.

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 34 | Global — all 6 screens | Bottom nav | **Cross-page navigation wired** — all 5 nav tabs navigate to the correct HTML file | ✅ Done |
| 35 | Global — all 7 screens | Client / Dev notes toggle | **Replaced** lo-fi-only wording with Client / Dev notes mode. Client mode = greyscale (default). Dev mode = hi-fi + yellow dev note annotations | ✅ Done |
| 36 | Global — `wireframe-skin.css` | `.dev-note` component | Added dev note styles: hidden in client mode, shown in dev mode. Dashed yellow border, "DEV NOTE" monospace header | ✅ Done |
| 37 | Wallet / Credits section | Section title | "CREDIT WALLETS" → "Credits" | ✅ Done |
| 38 | Wallet / Credits section | Credit card icons | **Replaced** SVG icons with 2-letter code badges (RP, JY, MC, CC) for instant scannability | ✅ Done |
| 39 | Wallet / Credits section | Credit amounts | Integer display only — removed decimal places | ✅ Done |
| 40 | Wallet / Credits section | Credit names | Full names shown: Range Practice Credits, Junior Youth Credits, Masterclass Credits | ✅ Done |
| 41 | Wallet / Credits section | Credit card subtitles (`.wc-type`) | **Removed** — name + 2-letter code sufficient | ✅ Done |
| 42 | Wallet / Credits section | Credit card clickability | Added chevron-right affordance (`.wc-chevron`) to all credit cards | ✅ Done |
| 43 | Wallet / Credits section | Status badges | Terminology locked: **Active**, **Expiring**, **Overdue**, **Expired** | ✅ Done |
| 44 | Wallet / Credits + Passes | Date field labels | Standardised to "Valid from" / "Valid till" across all credit and pass cards | ✅ Done |
| 45 | Wallet / Passes section | Section title | "PASSES" → "Range Passes" | ✅ Done |
| 46 | Wallet / Passes section | Pass mock data | 2 passes: 180D West Coast (Expiring, 10 Dec 2025 – 8 Jun 2026) + 90D Island (Active, 9 May – 7 Aug 2026). Dates verified with duration math | ✅ Done |
| 47 | Wallet / Passes section | Expired pass CTA | Expired pass cards show "Renew in Shop →" link in footer; navigates to Shop screen | ✅ Done |
| 48 | Wallet / Credits (MC overdue) | Overdue CTA | MC overdue card footer shows "Top up in Shop →" link; navigates to Shop screen | ✅ Done |
| 49 | Wallet / Credit history | Layout | **Full-page slide-in** replaces bottom sheet. Back arrow navigates back to wallet | ✅ Done |
| 50 | Wallet / Credit history | Sections | Two sections: **Upcoming Activations** (package name, sales ref, credit count, activation date) + **History** (transactions) | ✅ Done |
| 51 | Wallet / Credit history | Transaction icons | Plus circle (credit) / Minus circle (debit) — replaces directional arrows | ✅ Done |
| 52 | Wallet / Credit history | Running balance | **Removed** per-transaction balance — not stored in DB, not worth computing | ✅ Done |
| 53 | Wallet / Credit history | Post-shoot sub-text | Walk-in session entries use "after session" (e.g. "West Coast · after session") not range bay number | ✅ Done |
| 54 | Home / Location chips | Pin icon | **Removed** pin SVG from West Coast and Chai Chee location chips | ✅ Done |
| 55 | Home | Dev note | Location picker reads from `user.home_range`; Chai Chee chip hidden if no active CC pass; sign-in button label updates dynamically | ✅ Done |
| 56 | Book / Step 2 | Dev note | Slot row to show time range string, not availability bar (drop AvailabilityBar widget) | ✅ Done |
| 57 | Book / Step 4 | Dev note | Credit deduction redesign: remove Hours/Rate rows, add pay with/without credits toggle | ✅ Done |
| 58 | Shop / Catalog | Dev note | Locker Access new category, attributes TBD | ✅ Done |
| 59 | Sign-in + Sign-out | Dev note | Sign-out flow redesign: remove modal, add session bill page, add Undo button | ✅ Done |
| 60 | Me / Profiles | Dev note | Delink behavior: no email verification, admin vs member portal linking rules | ✅ Done |
| 61 | Wallet / Credit history | Transaction variations | Added: Booking cancelled (member), Session cancelled by venue, Admin adjustment (positive + negative) across RP, JY, MC, CC histories | ✅ Done |
| 62 | Home / Sign-in card | Sign-in button | Label simplified to "Sign in to Range" (static, not dynamic per location). Button navigates to `05 Sign-in + Sign-out.html` | ✅ Done |

---

## Session additions (2026-06-10)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 63 | Global — all 6 screens | Range names | West Coast A/B/C → Range 1/2/3 · Chai Chee D → Range 1. Applied across all JS data, HTML display text, and booking list examples | ✅ Done |
| 64 | Global — all 6 screens | Caleb Tan profile group | "Junior Youth" / "Junior squad" → "Master Class" across all 6 screens | ✅ Done |
| 65 | Book / Step 1 — Activity list | Junior Youth activity | Removed entirely from booking flow | ✅ Done |
| 66 | Book / Step 1 — T&C note | T&C copy | Real copy integrated: "By proceeding, you agree to SLA's Terms & Conditions and cancellation policy." Tapping link opens a bottom sheet with full booking T&C + cancellation policy text | ✅ Done |
| 67 | Book / Step 2 — Timeslots | Dev note | Removed dev note from Step 2 panel | ✅ Done |
| 68 | Book / Step 2 — Timeslots | Consecutive error | Simplified to "Slots must be consecutive." (removed dynamic next-slot hint) | ✅ Done |
| 69 | Book / Step 4 — Review | Credit badge | Replaced the old junior-credit badge with activity-appropriate credit type (RP for Range Practice, MC for Master Class) | ✅ Done |
| 70 | Book / Step 4 — Review | Credit type selector | Added multi-type selector: RP + CC for Range Practice; MC-only for Master Class. Configured per activity | ✅ Done |
| 71 | Book / Step 4 — Review | Insufficient credit handling | Selected type with insufficient balance → chip error state + warning banner + Continue disabled. Switching to a type with sufficient balance clears the block | ✅ Done |
| 72 | Book / Step 4 — Review | Credit quantities | Integer display throughout (no `.toFixed(1)` decimals) | ✅ Done |
| 73 | Book / Step 4 — Review | Without-credits section | Removed $0 row. Shows only "Payment to settle at sign-out" | ✅ Done |
| 74 | Book / Step 4 — Review | Static venue default | Default display corrected to "Range 1 · West Coast" | ✅ Done |
| 75 | Book / Step 2 — Timeslots | Remaining count | Each slot row now shows remaining count: "X left" for practice; "X spots" for lessons; "Full" when 0 | ✅ Done |
| 76 | Book / Step 2 — Timeslots | Master Class slots | 3 × 2-hour sessions per day (9–11 AM · 1–3 PM · 3–5 PM). Single-select (replacing previous selection) | ✅ Done |
| 77 | Book / Booking detail sheet | Dev note — cancellation window | Added: "Decide: fixed hours before session (e.g. 12 hrs) or end of previous day? Should cutoff differ by activity type?" | ✅ Done |
| 78 | Book / Booking detail sheet | Dev note — past booking info | Added: "Consider: which fields matter for past sessions (sign-in time, credit deducted, instructor, access code)? Receipt link or feedback prompt?" | ✅ Done |
| 79 | Shop / Purchases tab | Review | Month pill filter bar (Jan–Jun). History rows: 1 per category (locker, pass, activity, credits, combo). Tapping a row opens a read-only receipt sheet with per-type fields + Payment + Reference. | ✅ Done |
| 80 | Shop / Paid Activities | Purchase + booking journey | Review full flow: purchasing a paid activity (booking session details, HitPay) and the downstream booking experience. Receipt fields and scenarios (pre-payment, post-sign-out payment) tracked separately — see `paid-activity-receipt` TODO. | 🔲 Pending |

---

## Session additions (2026-06-11)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 81 | Shop / Catalog | Section order | Reordered to: Credits → Range Passes → Locker Access → Combo Packages → Paid Activities | ✅ Done |
| 82 | Shop / Catalog | Package naming | Adopted member-facing naming convention: `4 JY Credits`, `8 MC Credits`, `12 PC Credits` etc. JY remains the product label. | ✅ Done |
| 83 | Shop / Catalog | Credits section | Added PC (Private Coaching) credits: 4 PC and 12 PC. Added `ic-pc` icon (teal single-person) | ✅ Done |
| 84 | Shop / Catalog | Locker Access section | Implemented: 30D/90D × Chai Chee/West Coast. Padlock icon (`ic-locker`, purple). Placeholder prices | ✅ Done |
| 85 | Shop / Catalog | Combo Packages | Replaced placeholder combos with product names (`4 JY Credits w/ Pass`, `12 MC Credits w/ Pass`, etc.) and structured component data | ✅ Done |
| 86 | Shop / Catalog | Product tile | Removed subtitle/subtext from all credit, pass, locker, and combo tiles. Buy button → `>` chevron | ✅ Done |
| 87 | Shop / Catalog | Paid Activities | Moved to full-width `gc-bottom` slot — always renders below all other sections on both mobile and desktop | ✅ Done |
| 88 | Shop / Catalog | Dev note — Credits | Added: "Consider filtering credit types by archer's group (e.g. MC Credits to Master Class only). May require group field on profile schema or package-to-group mapping." | ✅ Done |
| 89 | Shop / Checkout sheet | Per-category detail rows | Redesigned: Credits → `Credits: N × Type` + Validity. Range Pass → Pass Name + Location(s) + Validity. Locker → Locker Access + Location(s) + Validity. Combo → labelled sub-sections per component | ✅ Done |
| 90 | Shop / Checkout sheet | Validity field | Single read-only row: `10 Jun 2026 – 9 Sep 2026` auto-calculated from fixed base date + item `days` property. Replaces old editable activation date | ✅ Done |
| 91 | Shop / Checkout sheet | Credits combined field | Credit Type and quantity merged: `4 × Master Class`. `qty` property added to all credit items and combo credit components | ✅ Done |
| 92 | Shop / Checkout sheet | Promo code | Input field + Apply button. Applies visual ✓ feedback on submit (wireframe only) | ✅ Done |
| 93 | Shop / Checkout sheet | HitPay placeholder | Replaced PayNow QR + card fields with HitPay placeholder box. Privacy note added above Pay button. Simulate button → success screen | ✅ Done |
| 94 | Home / Announcements | Announcement card | Review the announcement card design — content types, severity levels (Info/Warning), window chip usage, and when announcements should appear vs. alerts. Decide final layout before handoff. | ✅ Done — see #99 |

---

## Session additions (2026-06-13)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 95 | Book / Step 2 — Date & timeslots (`#p1`) | Slot row (`.slot-row`) — same-day walk-in | A **full** slot is normally blocked. Exception: **any full slot on the same day (today)** stays bookable as a **walk-in** — amber (`--color-warning`) treatment, label `Full · Walk-in`, selectable ring. Full slots on **future** days stay blocked (`Full`, × ring). Hours that have already **ended today are hidden entirely** (not shown as disabled). Selecting a walk-in slot shows a persistent amber banner: *"Walk-in — spot not guaranteed. This session is fully booked, but you can still shoot today as a walk-in. Archers with confirmed bookings get priority, and the range warden may ask you to leave if every lane is taken."* The warning re-renders at the top of Step 4 (Review) so it can't be missed before confirming. Demo wiring: today = Jun 5, current hour = 1 PM (`NOW_DAY`/`NOW_HOUR`); calendar now allows selecting today. | ✅ Done |
| 96 | Book / Success screen (`#vSuccess`) | Action buttons (`.suc-btns`) | **Removed** "Go to Home" button. **Renamed** "View bookings" → "Done". **Added** conditional **"Sign in to Range now"** primary button — shown only when the booking falls inside its sign-in window (today, and now ≥ start − 30 min and ≤ end). It jumps straight into the Sign-in flow on screen 05 (location pre-selected, arrows-in + session-notes sheet open). Sign-in window tolerance: **30 min before `start_hour` up to `end_hour`** (e.g. 10–12 booking → 9:30–12:00; 10–13 booking → 9:30–13:00). Location is carried across the nav via a one-shot `localStorage` key (`wf-signin-loc`) because the dev server drops query strings on its extensionless redirect; the `?loc=` param is retained for real static hosts. Home screen `goSignin()` updated to set the same key. | ✅ Done |
| 97 | Book / Step 2 — Date & timeslots (`#p1`) | Slot row ring (`.s-ring`) | Slot tiles now use a plain **checkbox** (rounded-square ring, checkmark when selected) instead of the dynamic hour-sequence number (①②③). Practice and lesson selections both render the same tick; no per-slot hour-count is calculated for display. Square ring (`--radius-sm`) reads as a checkbox; selected fill follows the row state (primary, or amber for walk-in). Blocked-full keeps the × ring. | ✅ Done |
| 98 | Home / Sign-in card (`#homeSignin`) | West Coast location chip | **Pre-selected by default** on page load — chip gets `.sel` class in initial HTML; `selectedLoc` initialises to `'West Coast'`; booking tile shows immediately without requiring a tap | ✅ Done |
| 99 | Home / Announcements | Announcement card (`.ann`) | **Simplified layout** — removed severity badge (`.ann-sev`) and window chip (`.ann-win`). Title format: "[Location] [Range X] reserved for event". Body format: "[N] lanes · [time range]". Closes #94. | ✅ Done |
| 100 | Shop / Purchases tab | Activity receipt + status chip | **Locked activity-payment receipt fields** (pre-paid vs post-paid variants). Pre-paid sheet shows Booking code(s) + Purchase summary (Amount paid, Voucher code if any, Payment method, Purchase date, Sale reference). Post-paid sheet adds Venue / Bow style / Billed duration before the booking codes. Mock data updated: `Trial Lesson` → `Intermediate Archery Course (Recurve)` ($240, prepaid); new `Range Practice` row ($24, postpaid, two booking codes, voucher `WELCOME10`, billed `2 hr`). **Status chip removed from all Purchases rows** (and detail-sheet headers) — entitlement state lives in Wallet. Detail header for activities now shows price only. Closes the `paid-activity-receipt` field-spec sub-task of #80 (the full purchase + booking journey wireframe remains pending). | ✅ Done |
| 101 | Book / Past bookings | Attendance chip | "Signed in" → "Attended" for past sessions; counterpart remains "No sign-in recorded". Past-tense pair is more accurate (member has already signed both in and out by the time the session is "past"). | ✅ Done |
| 102 | Shop / Purchases tab | Activity receipt — trim | Removed **Venue** and **Bow style** from post-paid receipt (post-paid sheet now shows only Billed duration + Booking codes). Removed **Purchase date** row from the Purchase summary block across all activity receipts — date is already on the sheet header. | ✅ Done |
| 103 | Shop / Purchases tab | March mock data | Added `Basic Archery Course (Recurve)` ($180, prepaid) with **8 booking codes** to demonstrate a multi-booking course purchase. Renders as a comma-separated wrapped list in the receipt sheet. | ✅ Done |
| 104 | Shop / Catalog + Purchases | Icon set standardisation | Consolidated product icons to **5 categories**: credits / range pass / locker / combo / activities. All credit products (RP, JY, MC, PC) now share a single bullseye icon. Dropped per-credit-type icon variants (`ic-rp`, `ic-jy`, `ic-jyp`, `ic-mc`, `ic-pc`) from both ICO map and CSS. Renamed canonical credit class to `.ic-credit`. | ✅ Done |
| 105 | Shop / Catalog | Paid Activities — replaced mock products | Replaced placeholder activities (Trial Lesson, Holiday Beginner Course, Private Coaching) with `Basic Archery Course Plus (Recurve)` ($260), `Basic Archery Course Refresher (Recurve)` ($80), `Basic Archery Course Test (Recurve)` ($60). Prices and sub-text are placeholders pending real product catalogue. | ✅ Done |
| 106 | Wireframe-skin | New `.client-note` component | Introduced `.client-note` block in `wireframe-skin.css` (label: `NOTE`, blue solid border, light-blue background). Always visible in both Client and Dev modes. Use when a note describes product-facing behaviour the client should also see during review. Distinct from `.dev-note` (yellow dashed, dev-only). | ✅ Done |
| 107 | Wallet / Range Passes | Expired pass visibility note | Converted "Expired pass visibility" note from `.dev-note` → `.client-note` so it appears in client review (the behaviour rule is product-visible, not a dev-only consideration). | ✅ Done |

---

## Summary

**Original items:**
- ✅ Done: #1, 2, 3, 4, 5, 7, 8, 10, 11, 12, 13, 14, 15, 16, 18, 20, 22, 23, 24, 25, 26, 27, 29, 31, 32, 33 — 26 items
- 🔲 Pending: none
- 📝 Note only: #9, 17, 19, 21, 28, 30 — 6 items
- ➖ Deferred: #6 — 1 item

**Session additions (all done):** #34–78, #81–93, #95–107 — 71 items
**Session additions (pending):** #80 — 1 item (Paid Activity purchase + booking journey)
