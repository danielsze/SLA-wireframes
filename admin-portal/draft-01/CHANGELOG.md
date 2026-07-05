# Admin Phase 2 Wireframes — CHANGELOG

Statuses: ✅ Done · 🔲 Pending · 📝 Note only · ➖ Deferred

## AS-IS capture (P1)

| # | Cluster | File | Status |
|---|---------|------|--------|
| 1 | Package dialog | `as-is/01 Package Dialog.html` | ✅ Done (captured from `package_dialog.dart` + `packages_table.dart`, edit-mode passCredit branch shown; activity/rental branches noted in dev-notes) |
| 2 | Range Overview | `as-is/02 Range Overview.html` | ✅ Done (access table 12 cols from `access_table.dart`; sign-out + payment dialogs as separate sections; chips/search/date filters from `overview_dashboard.dart`) |
| 3 | Archer360 profile | `as-is/03 Archer360 Profile.html` | ✅ Done (Archer tab + tabs chips; single-pass range-pass form from `profile_range_pass.dart`; credit holdings + transactions tables) |
| 4 | Sales dialog | `as-is/04 Sales Dialog.html` | ✅ Done (sales table 8 cols; create-sale dialog: general/payer, package section with pass+credit side-by-side, pricing; from `create_sale_package_section.dart` et al.) |
| 5 | Config > Club | `as-is/05 Config Club.html` | ✅ Done (clubs table: Club/Affiliated/Remarks/Actions with hard-delete flow noted; club dialog: name/affiliate/remark, from `clubs_table.dart` + `club_dialog.dart`) |
| 6 | Range Timetable | `as-is/06 Range Timetable.html` | ✅ Done (full timetable wireframe with range chip headers, instructor-booking counts, availability, lanes, and booking overlays; captured 2026-07-05 per Daniel request) |

## Phase 2 delta (v1/)

| # | Cluster | Delta items | Status |
|---|---------|-------------|--------|
| 1 | Package dialog | 2.5 group+style eligibility, description, renewal discount; 2.7 locker settings | ✅ Done (A: dual multi-selects + hint post-Remarks; B: textarea description + hint; C: subsection w/ Discount Type dropdown + Value input; D: Locker checkbox + Locker Settings block side-by-side w/ Pass+Credit) · locker multi-location per Daniel 2026-07-05 |
| 2 | Range Overview | 2.7 location-valid pass column (+1 more pill on multi-pass archers); 2.10 staff-assisted sign-in dialog (net-new) + session-level settlement bill (rebuild) | ✅ Done in `v1/02` |
| 3 | Archer360 profile | 2.7 pass holdings rebuild + locker view; 2.14 Verified-Score entry | ✅ Done (A: pass holdings multi-table + locker holdings view; B: locker table; C: Scores chip + verified-score CRUD form + table) |
| 4 | Sales dialog | 2.7 locker branch | ✅ Done (A: third "Locker" block added to pass/credit row — location/days-valid readonly, start-date editable, valid-till read-only auto-computed from start-date + days-valid; row wraps at 3 blocks; B: package dropdown label updated to show "Range Pass + Credit + Locker Bundle"; C: banner note re-added; dev-notes complete) |
| 5 | Config > Club | 2.15 CC balance/ledger/top-up/roles, soft-deactivate, usage report entry | ✅ Done (A: CC Balance + Status columns, credits icon, soft-deactivate title; B: Club Credits detail section with summary, top-up dialog, ledger table, club roles table) |
| 6 | Chips/badges | 2.11 signed-in-count badge on overview (✅ in `v1/02`); instructor-count badge on timetable (✅ in `v1/06`) | ✅ Done: both 2.11 badge halves now wireframed (overview in `v1/02`, timetable in `v1/06`) |
