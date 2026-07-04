# v5 Wireframe Changelog

Design review session: 2026-06-14 (v4 baseline; see history below)
Reviewer: Daniel
Implemented in: `phase2-designs/v5/` (branched from v4)
Last updated: 2026-07-04

---

## Client feedback intake (2026-07-04)

Client feedback on the published v4 wireframes. Implemented in v5 on 2026-07-04.

| # | Screen | Element | Change / Note | Status |
|---|--------|---------|----------------|--------|
| 66 | 06 Me | Edit Profile — Gamification opt-out | Added a **"Leaderboard"** toggle (switch, default ON = opt-in) at the bottom of the Edit Profile form: "Show my shooting activity and scores on leaderboards". Label deliberately avoids the word "gamification" — internal term only, per Daniel. Switch CSS copied from 06a Club for consistency. Dev-note captures the new user-level boolean `gamification_opt_in` (default `true`), saved with the profile edit; whether opt-out also hides the archer's own private stats is TBC with client. | ✅ |
| 67 | 04b Checkout | Start Date picker — validity dates | Added a "Start Date" detail section above the product detail sections: date input autofilled to today (mock today = 10 Jun 2026), `min` = today, with a client-visible hint. All "Validity" rows (`.validity-val`, `data-days`) recalculate live from the chosen start date via `setStartDate()`; dates before today clamp back to today. One start date drives all components of a combo. Dev-note captures the BE contract: optional `start_date` on the purchase API (default today), valid-till computed server-side as `start_date + validity_days`, server-side `start_date ≥ today` validation. | ✅ |

---

## Product decisions locked (2026-07-04)

Three open product decisions resolved with Daniel; wireframe notes flipped from "Decide:" to settled, spec (`member-app-feature-spec.md` §5.3, §5.5, §10 rows 3/13/14) updated to match.

| # | Screen | Element | Change / Note | Status |
|---|--------|---------|----------------|--------|
| 68 | 02 Make a Booking | Cancellation-window client-note (booking detail sheet) | **Decided: no change to cancellation window.** Members self-cancel anytime before the session's start hour (current app behaviour); no fixed-hours cutoff, no per-activity-type variation; lesson-specific cutoff KIV. Note converted client-note → dev-note with the locked rule. The 12-hr late-cancel wording in the booking T&C sheet is left as-is (policy copy, not in-app enforcement). | ✅ |
| 69 | 04a Paid Activity | Email receipt dev-note + client-note (success view) | **Decided: no SLA confirmation email** — HitPay's automatic payment receipt is the only email, for both 04a and 04b. Members see bookings/purchases in-app; guest branded email (`guest/post-payment`) unchanged; credit-paid bookings send no email (unchanged). Dev-note rewritten to the locked rule; the "Will you require an additional booking confirmation email?" client-note removed. Zero backend email work. | ✅ |
| 70 | 04 Shop | Credit package visibility dev-note (Credits section) | **Decided: per-package group eligibility** — optional `eligible_group_ids` array inside `package.info` JSONB (sibling of `member_display`); absent/empty = visible to all. No DB migration (`user.group_id` exists). Filter applies to the Shop catalogue only — never Wallet holdings or credit spending (`access/post-access` untouched). Backend: one predicate in `member/get-user` catalogue query + optional field in `admin_config/post-config` package model. Admin package dialog gains a group multi-select (tracked under Admin Phase 2 Delta / 2.5). | ✅ |

---

## Status key
- ✅ Done — implemented in v3
- 🔲 Pending — needs implementation
- 📝 Note only — behaviour/engineering note, no UI change required
- ➖ Deferred — explicitly skipped for now

---

## Review items

| # | Screen | Element | Change / Note | Status |
|---|--------|---------|---------------|--------|
| 1 | All | Client view | Strip all colors across the board in Client view (Dev notes view keeps colors). | ✅ |
| 2 | All | Clickable cards | All clickable cards (e.g. booking cards on 02 Make a Booking — Upcoming & Past) must show a right-side `›` chevron. Apply consistently across the app. | ✅ |
| 3 | 04 Shop | Paid Activities — product row | Remove the `prod-sub` subtitle line (e.g. "Extended beginner course", "For returning archers") from all paid activity rows. | ✅ |
| 4 | 01 Nav + Home | Upcoming Bookings — `.book-row` | Make rows clickable like the booking cards in the Book tab — open the same bottom modal sheet on tap. | ✅ |
| 5 | 02 Make a Booking | Booking detail modal — `#detBowRow` | Remove the "Bow style" row from the booking detail modal across all booking cards. | ✅ |
| 6 | 01 Nav + Home | Range busyness section (`.gc-right`) | Remove the entire Range busyness section. Replace with a dev-note: "Range busyness to be explored in later phases — deprioritised for now." | ✅ |
| 7 | All | Notes visibility rule | Client notes show in BOTH Client view and Dev view. Dev notes show ONLY in Dev view. Audit and apply across every screen. | ✅ |
| 8 | 01 Nav + Home & 05 Sign-in + Sign-out | `#signinBtn` button label | Change "Sign in to Range" → "Sign In". Apply on both home tile and 05 screen. | ✅ |
| 9 | 01 Nav + Home & 05 Sign-in + Sign-out | `#nbNote` "No booking found" copy | Add a line explaining the early-arrival window so users don't panic. Final copy applied: "Note that Sign-In unlocks 15 mins before your booked session starts. Else, make a booking or sign in with access code." | ✅ |
| 10 | 02 Make a Booking | Walk-in slot note (`.slot-note` inside `#slotErrWrap`) | Tighten copy. Final copy applied: **Walk-in only.** "You may be asked to leave if the range fills up — confirmed bookings get priority." Applied to both Range Practice and Lessons flows, and to the review step. | ✅ |
| 11 | 02 Make a Booking | Walk-in vs booked mixed selection | Add dev-note: when an archer selects multiple consecutive hours where some are full (walk-in) and some are available (proper booking), decide whether to split into separate bookings or find a cleaner way to handle the mixed state. Needs product decision. | ✅ |
| 12 | 05 Sign-in + Sign-out — Session Bill (`.sc-coverage`) | Add a dev-note flagging the un-punctual sign-in/sign-out bill reconciliation as outstanding. Capture the working formula:<br>`excess_mins = (signed in before booking start? mins-to-start : 0) + (signed out after last booking end? mins-past-hour-mark : 0)`<br>`Total_mins_payable = sum(rp_booking_mins_consumed) + unaccounted_complete_hours_consumed_in_mins + excess_mins`<br>Minus 60 mins per RC/CC credit used inside an RP booking.<br>Example: RP 2–3pm, JY 3–5pm, sign-in 1:45, sign-out 6:45.<br>Cross-link discussion on Notion: [Phase 2.2.10 Enhanced Sign-In / Sign-Out Mechanics](https://www.notion.so/Phase-2-2-10-Enhanced-Sign-In-Sign-Out-Mechanics-30e92478a0f28024b1fbe9fdcc896ca5#37f92478a0f280a1bb0ddc2baed50357). | ✅ |
| 13 | 05 Sign-in + Sign-out — `#siSheet` "Make a booking" button | Currently only calls `closeAll()` — wire it to navigate into the Make a Booking journey (02). | ✅ |
| 14 | All | Button label audit | Sweep every screen and reconcile button labels for consistency (casing, verb choice, "Make a booking" vs "Book a slot" vs "Book now", "Sign In" vs "Sign in", etc.). Produce a single label vocabulary and apply. | ✅ |
| 15 | 05 Sign-in + Sign-out | "Undo Sign Out" affordance | Added as a new scenario tab in 05. Shows home sign-in card in undo state: "Recently signed out" eyebrow, booking tile, "Undo Sign Out" CTA, client note. Dev-note captures eligibility conditions (TBC: N-minute window + active booking still running). | ✅ |
| 16 | 05 Sign-in + Sign-out — Session Bill (`.cred-section`) | Decision: settlement is offline at the counter only. Removed credit deduction panel and "Partner decision needed" note. Outstanding payable row is shown with a counter-settle note. | ✅ |
| 17 | 03 Wallet | Orphaned top-up sheet | Consistency scrub: removed the dead in-Wallet top-up bottom sheet (`#sheetTopup`, `openTopup`/`pickPkg`, `PKGS`/`PN`/`PS`/`CHK`, `.topup-btn`/`.renew-btn`/`.pkg-*` CSS). It was never invoked — cards route to history or "Top up in Shop →". Also eliminated mismatched top-up prices (5/10/20 packs @ $25/$45/$80) that didn't exist in Shop. Shop is the single source of truth for packages/pricing. | ✅ |
| 18 | 04 Shop | Legacy modal checkout | Consistency scrub: removed the dead bottom-sheet checkout (`#coSheet`, `renderCheckout`/`renderActivityCheckout`, `payMethodHTML`/`pickPayMethod`, `openHitPay`/`processPayment`, `applyPromo`, `calcValidity`, `closeCheckout`, and all `.co-*`/`pay-tab`/`loc-chip`/`time-chip`/`success-*` CSS). The live path (`openCheckout`) navigates to the full page `04b Checkout.html` / `04a Paid Activity.html`; the modal was unreachable and had drifted from `04b`. Verified both pages render with no JS errors and the live checkout entry is intact. | ✅ |
| 19 | 03 Wallet, 04b Checkout, 04 Shop | Label vocabulary scrub | Locked canonical terms: "Masterclass Credits" → **"Master Class Credits"** (Wallet card + JS meta); checkout detail label "Pass" → **"Pass Name"** (04b, matches Shop history); Shop history detail "Reference" → **"Sale reference"** (matches activity branch + 04b). Confirmed user-facing "Voucher" and "Club Credits" already consistent. Left intentionally untouched: booking `CREDIT_LABELS` "(CODE)" convention (`Club (CC)` etc.) and the separate "Renewal discount" auto-row in 04b. | ✅ |
| 20 | 04b Checkout, 04a Paid Activity | Checkout CTA + success copy | Primary checkout CTA locked to **"Proceed to Pay"** (confirmed on 04b and 04a). Removed the "…added to your account and is ready to use" success sub-line (deleted with the Shop modal; verified absent on 04b/04a). Activity time-picker mismatch resolved by deleting the Shop modal (item 18); 04a's real calendar + timeslot flow is the single source. | ✅ |
| 21 | 04 Shop, 04a Paid Activity, 04b Checkout | Currency format | Locked all displayed money to **`$X.00`** (leading `$`, exactly 2 decimals, no "SGD" prefix). Shop history prices get `.00`; 04a drops `SGD ` → `$`, adds a `money(n)=Number(n).toFixed(2)` helper for all dynamic totals/discounts (percentage voucher labels left as `−N%`); 04b already used `.toFixed(2)`. | ✅ |
| 22 | 03 Wallet | Date format | Standardised all "Valid till" dates to weekday-prefixed form **"Valid till Wed, 10 Jun 2026"**. Added correct weekdays: 31 Aug → Mon, 31 Dec → Thu, 7 Aug → Fri, 7 Apr → Tue. | ✅ |
| 23 | 03 Wallet | Negative glyph | Standardised the negative sign to **U+2212 `−`** everywhere: balance (`&#8722;` entity → literal `−`) and the transaction-list render (was ASCII hyphen via `+t.amt`, now `(t.amt<0?'−':…)+Math.abs(t.amt)`). | ✅ |

---

## Button label vocabulary (locked in v3)

All primary CTA buttons use **Title Case**. Secondary inline links (e.g. "View all") use **sentence case**.

### Sign-in / Sign-out (range session)

| Concept | Label |
|---------|-------|
| Range sign-in CTA (home card + 05 screen) | **Sign In** |
| Sign-in sheet confirm (booking found) | **Sign In · {Location}** |
| Sign-in sheet confirm (no booking, access code) | **Sign In with Access Code** |
| Sheet title text | **Sign In** |
| Sign-out CTA (active session card) | **Sign Out** |
| Sign-out sheet final step (counter) | **Confirm Sign Out** |
| Sign-out sheet final step (payment) | **Pay ${amount}** |
| Bill page undo link | **Undo Sign Out** |
| Bill page payment confirm | **Confirm Payment** |
| Sign-out flow proceed to payment step | **Proceed to Payment** |
| No-booking sheet: navigate to booking | **Make a Booking** |

### App session (00 Login / 06 Me)

| Concept | Label |
|---------|-------|
| Login primary CTA | **Log In** |
| Back to login navigation | **Back to Login** |
| App logout CTA (06 Me) | **Log Out** |
| Forgot password link (inline) | **Forgot password?** (sentence case — secondary inline) |
| Send password reset | **Send Reset Link** |
| Set new password confirm | **Confirm** |

### Bookings (02)

| Concept | Label |
|---------|-------|
| Create new booking button | **New Booking** |
| Stepper back | **Back** |
| Stepper forward / default | **Continue** |
| Post-booking: go to range sign-in | **Sign In to Range Now** |
| Post-booking: dismiss | **Done** |
| Cancel booking (within window) | **Cancel Booking** |

### Wallet (03)

| Concept | Label |
|---------|-------|
| Top-up/renew CTA — no selection | **Proceed to Checkout** (disabled) |
| Top-up CTA — selection made | **Checkout · ${price}** |
| Renew pass CTA — selection made | **Renew · ${price}** |

### Shop (04)

| Concept | Label |
|---------|-------|
| Checkout CTA | **Proceed to Pay** (navigates to 04b Checkout / 04a Paid Activity; updated from "Pay ${price}.00" — Shop now opens a full checkout page, not an inline pay button) |
| Voucher code action | **Apply** |
| Post-payment dismiss | **Done** |

### Paid Activity (04a)

| Concept | Label |
|---------|-------|
| Form sticky CTA | **Proceed to Pay** |
| Voucher code action | **Apply** |
| HitPay dropin close | **Close** |
| Payment confirmed (dev sim) | **Payment Confirmed** |
| Success: home navigation | **Back to Home** |
| Failure: retry | **Try again** |
| Failure: navigate back | **Back to Shop** |
| Failure: cancel | **Cancel and return to Shop** _(borderline — flagged, left as-is for now)_ |
| Pending: booking check | **Check Book tab** |

### Punted / left as-is

- **"Cancel and return to Shop"** (04a failure view) — verbose but descriptive, no direct duplicate. Left unchanged pending copy review.
- **"Simulate: Confirm Payment"** and **"Simulate success/failure/pending"** (04a dev tools) — dev-only scaffolding, not user-facing, intentionally informal.
- **"Toggle dev notes"** (04a) — dev tool button, excluded from label scope.
- **"Payment Confirmed"** (04a dev sim step) — simulates a gateway state, not a user-initiated action label.
- **Segment/tab controls** (`Upcoming`/`Past`, `Catalog`/`Purchases`, `PayNow`/`Card`/`Pay at counter`) — these are tab labels, not CTAs; casing left unchanged.

---

## Session additions (2026-06-17)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 17 | 04a Paid Activity | Email receipt note (`.client-note`) | Moved detailed dev reasoning to `.dev-note` (hidden in client view). Client note simplified to: "Will you require an additional booking confirmation email after successful payment?" | ✅ |

---

## Summary

All 16 review items complete as of 2026-06-15. v3 is feature-complete for client review.

## Session additions (2026-06-21)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 18 | 06 Me | Hero (`.me-hero`) | Removed the avatar + name hero block; screen now opens at the Profile section | ✅ |
| 19 | Index | Page title | Dropped "v3" from the title; show "Updated 21 Jun 2026" in the eyebrow instead | ✅ |

## Session additions (2026-06-21)

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 20 | 02 Make a Booking | Booking detail sheet — "Past booking" note | Changed from `client-note` to `dev-note`; hidden in client view | ✅ |
| 21 | 03 Wallet | Credit cards — expiring state | Removed amber card tint and icon colour; only the "Expiring" badge retains warn colour | ✅ |
| 22 | 03 Wallet | Pass cards — expiring state | Removed amber card/date/footer warn colour; only the "Expiring" badge retains warn colour | ✅ |
| 23 | 03 Wallet | Credit transaction history | Removed "after session" debit and "venue cancellation" credit entries from RP, JY, MC — not valid scenarios | ✅ |

## Session additions (2026-06-27) — 2.10 Sign-in / Sign-out lock-in

Billing algorithm + edge cases locked via Notion 2.10 page. Wireframe brought in line.

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 24 | 05 — Active session card | sNB toggle | Removed the "Sign-in · Access Code" scenario toggle — no longer needed | ✅ |
| 25 | 05 — Home (sign-in card scenario) | Home placeholder | Added a dashed "Other home sections" placeholder visible in both client and dev views so the home-page context is clear | ✅ |
| 26 | 05 — Active session card · `.sc-coverage` | "No Booking" label | Relabeled all "No Booking" walk-in rows to "Range Practice" — backend NB-booking-vs-NULL distinction is not surfaced to the archer; the `WALK-IN` chip carries the meaning | ✅ |
| 27 | 05 — Active session card · `.scc-row` | Status icons | Removed status icons from all coverage rows. Row tint (green/amber) + chip already carry the signal; less visual noise | ✅ |
| 28 | 05 — Bill page · dev-notes | Consolidated formula/reconciliation notes | Replaced two separate dev-notes with a single dev-note linking to Notion 2.10 page | ✅ |
| 29 | 05 — Bill page · `.sc-coverage` | Coverage rows match active session | Bill now itemises all four slices: 2× Paid bookings + 2× Unpaid walk-ins. Row 4 shows actual sign-out time (`3:00 PM – 3:25 PM · 25 mins`) | ✅ |
| 30 | 05 — Bill page · billing math | Hardcoded mock to algorithm | Payable hours = 3 (2h25min rounds up at 15-min tolerance); 3 × $5/hr = **$15**. Replaced old `elapsed - 2h × $5` formula | ✅ |
| 31 | 05 — Bill page · `.bill-session` | Session period header | Added an eyebrow + bold time-range + duration/location strip above the coverage list. Differentiates session metadata from billable line items | ✅ |
| 32 | 05 — Bill page · rental row | Equipment rental row | Added rental as a coverage-style row showing bow name + `$15`. `WAIVED` chip when a lesson (Master Class) is in coverage. Updated `GEAR` prices ($5 arrows, $15 bow sets) | ✅ |
| 33 | 05 — Bill page · `.client-note` | Range Pass chip explainer | Added client-visible note: if archer holds a valid Range Pass, walk-in slices would show a `RANGE PASS` chip instead of UNPAID and not add to total | ✅ |
| 34 | 05 — Sign-out flow · step 2 | "Arrows shot today" field | Added optional numeric input (placeholder `e.g. 96`) below the Arrows End slider. Resets with the sign-out flow | ✅ |
| 35 | 05 — Sign-out flow · step 2 | Access code collapsed by default | Replaced the always-visible access code section with a text button: "Have an access code? It may reduce what's payable." Expands on tap; copy explains private events are pre-paid | ✅ |

## Session additions (2026-06-27) — Booking page v4 copy + slot rules

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 36 | 02 Make a Booking | Activity cards | Added required credit labels under each activity name | ✅ |
| 37 | 02 Make a Booking | Timeslots | Allows mixed walk-in/reserved selection for visibility, but shows a warning and disables Continue until one type is unselected | ✅ |
| 38 | 02 Make a Booking | Timeslot + review copy | Updated walk-in, full-slot, consecutive-slot, sign-out charge, and refund copy | ✅ |
| 39 | 02 Make a Booking | Review credits | Added dev-only credit scenario controls for available, insufficient, and no eligible credit states; lessons are credit-only while Range Practice can fall back to sign-out charge | ✅ |
| 40 | 02 Make a Booking | Master Class review credits | Simplified lesson credit UI: hide the pay-with-credits toggle and explanatory copy, showing credit type, deduction, and balances directly | ✅ |

## Session additions (2026-06-28) — 2.9 Me screen + Shop checkout page

### 06 Me

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 41 | 06 Me | Emergency contact label | "Secondary contact" → "Emergency contact" in both view mode and edit form | ✅ |
| 42 | 06 Me | Gender field (edit form) | Replaced segmented control with `<select>` dropdown; options: Male / Female / Prefer not to say | ✅ |

### 04 Shop

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 43 | 04 Shop | Catalog rows — description subtitle | Added `.prod-sub` CSS + `desc` field on all items; renders a subtitle line under each product name in the catalog | ✅ |
| 44 | 04 Shop | `openCheckout()` routing | Non-activity items now navigate to `04b Checkout.html?item=<id>` instead of opening a bottom sheet | ✅ |
| 45 | 04 Shop | Dev notes | Added dev notes to Credits, Passes, Locker, and Combo sections flagging the new `description` backend DB field required on `sale_mgmt` records | ✅ |
| 46 | 04 Shop | Combo data — c7 | Added `c7` combo item: 4 JY Credits + 30D Pass + 30D West Coast Locker — demonstrates credit + pass + locker component combo | ✅ |

### 04b Checkout (new file)

Full-page checkout for credits, passes, lockers, and combo packages. Replaces the old bottom sheet flow.

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 47 | 04b Checkout | Product hero | Icon + name + price (large) at top of page | ✅ |
| 48 | 04b Checkout | "About" description block | Renders `it.desc` only when present; label is "ABOUT" | ✅ |
| 49 | 04b Checkout | Detail sections | Per-type breakdown: Credits (qty × type, validity), Pass (name, locations, validity), Locker (name, locations, validity), Combo (one section per component) | ✅ |
| 50 | 04b Checkout | Auto discount row | When `auto_discount` is present in API response, shows green "Renewal discount –10%" row by default; plain-text "Use a voucher instead →" link toggles to voucher mode. "← Use renewal discount" link toggles back. Discount `display` field is flexible — BE can send percentage or flat amount. | ✅ |
| 51 | 04b Checkout | Voucher input | Shown by default when no `auto_discount`; otherwise hidden behind the toggle. `applyVoucher()` updates total (demo: –$5.00) | ✅ |
| 52 | 04b Checkout | Total row | Reflects active discount mode: discounted total when auto discount is on, full price when in voucher mode (until voucher applied) | ✅ |
| 53 | 04b Checkout | Payment method selector | PayNow / Credit Card segmented control + HitPay privacy note | ✅ |
| 54 | 04b Checkout | HitPay placeholder → success | "Proceed to Pay" → HitPay drop-in placeholder → "Payment confirmed" screen with summary card (Item, Amount paid, Method, Date, Sale reference) | ✅ |
| 55 | 04b Checkout | Sale reference format | `[PREFIX][YYYYMMDD][HHMMSS]` — prefix by item type: RC (credit), WC (pass), LK (locker), CB (combo). Matches existing sale reference format. | ✅ |
| 56 | 04b Checkout | Dev/client toggle | Canonical `wf-mode` toggle wired in; dev notes visible in dev mode only | ✅ |

### Button label additions (04b)

| Concept | Label |
|---------|-------|
| Checkout page primary CTA | **Proceed to Pay** |
| Post-payment dismiss | **Done** |
| Voucher code action | **Apply** |

## Session additions (2026-06-28) — 2.15 Club credits & club-admin (member portal)

Wireframes for SoW 2.15 club model. Scope/model settled on the Notion 2.15 Planning Snapshot. A **Club role** dev toggle (Regular member / Privileged · uses credits / Club admin) was added to 03 and 06 to demonstrate `user.club_role` gating. Built directly (design work, not mechanical); verified in preview — no console errors, both Client and Dev views toggle-safe.

### 03 Wallet

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 57 | 03 Wallet | Club role dev toggle (`.role-bar`) | Added a 3-state pill bar (member / privileged / admin) above the frame. Drives CC-card gating + ledger archer-name visibility | ✅ |
| 58 | 03 Wallet | Club Credits card (`#ccCard`) | **Access-gated**: hidden for regular members; shown for privileged + admin. Dev-note (`#ccDevNote`) explains the rule + that member-level balance visibility is TBC with client | ✅ |
| 59 | 03 Wallet | Club ledger (`TXNS.CL` + render) | Debit rows now carry the **consuming archer's name** (`who`). Rendered (bold `.txn-who`) **only in admin view**; privileged sees the same ledger without names. Mock data updated to drop the redundant "allocated by SDSC" subtitle | ✅ |

### 06 Me + 06a Club (new file)

Originally built club management as an in-`06 Me` overlay (items 60–63 below). **Refactored 2026-06-28** to keep 06 Me lean: club management moved into its own **`06a Club.html`** drill-in screen; 06 Me keeps only a single role-gated entry point. The 3-state club-role dev toggle was dropped per Daniel — a client-note now states the entry is admin-only.

| # | Screen | Element | Change | Status |
|---|--------|---------|--------|--------|
| 60 | 06 Me | Club role dev toggle (`#roleBar`) | ~~Second pill bar mirroring 03~~ — **removed in refactor**; no toggle on Me | ↩︎ superseded |
| 61 | 06 Me | Club section card | ~~Role-gated section with club name + role chip + manage-members row~~ — **replaced** by a single **"Manage club"** entry row under Characteristics, with a client-note that it's club-admin only | ✅ |
| 62 | 06a Club | Club Members screen (new file) | Standalone drill-in (modeled on 06 Me's shell, back → 06 Me). Member rows grouped by credit access, each with a **credit-access toggle switch** and a **remove (expel)** action. Admin's own row is locked (disabled toggle, no expel). Added to index as `06a` | ✅ |
| 63 | 06a Club | Remove member (expel) | ~~Bottom-sheet confirm before removing a member~~ — **removed**; member removal is out of scope this phase (back-office only). Captured as a stretch-goal dev-note on 06a | ↩︎ superseded |
| 64 | 03 Wallet | Club role toggle → 2-state | Collapsed the 3-state role demo to a 2-state `use_credit` toggle (`No access` / `Can use credits`); archer names in the club ledger now show unconditionally (no longer admin-gated) | ✅ |
| 65 | 03 Wallet | Transaction field standardisation | All credit ledgers (RP/JY/MC/CC) use one row shape — title = event category, subtitle = `context`/`ref`. Dropped the meaningless top-up "channel"; dropped admin-adjustment refs; added session date to CC spend rows. Renamed contradictory JY spend title "Master Class lesson" → "Junior Youth" (canonical activity TBC). CC allocation reuses the "Credit Top-up" title | ✅ |
