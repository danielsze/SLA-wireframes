# v3 Wireframe Changelog

Design review session: 2026-06-14
Reviewer: Daniel
Implemented in: `phase2-designs/v3/` (to be branched from v2)
Last updated: 2026-06-14

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
| Checkout CTA | **Pay ${price}.00** |
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

## Summary

All 16 review items complete as of 2026-06-15. v3 is feature-complete for client review.
