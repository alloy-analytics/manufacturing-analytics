# Utility Dashboard — Build Log

Author: Divine C. Alloyshius · Presco Plc
Format: what I did · what I found · what's next

---

### Late Sep 2026 — Requirements
- **Did:** Turned the utility mockup into a full data checklist covering every KPI, chart and table, and the exact data point each one needs.
- **Found:** Raw utility data sits on the production server in separate Excel files, one folder per system (power, steam, water, fuel).
- **Next:** Design one source table that every report can read from.

### Early Oct 2026 — Data structure
- **Did:** Designed a long, tidy source table (one row per day). Worked out how to turn row-wise monthly sheets into columns with INDEX formulas (Excel 2019, no TOCOL).
- **Found:** Steam is recorded per boiler (Vickers and Atmindo) in separate rows, with no total row. Solved it with two INDEX lookups added together into one "Steam Generated" column.
- **Next:** Decide where targets live → a separate Targets lookup table, not number formatting.

### Oct 2026 — Downtime Tracker
- **Did:** Built a downtime tracker for the utility section: daily log with equipment and reason, plus weekly, monthly and quarterly reports and availability %.
- **Found:** The utility section had no record of equipment downtime at all.
- **Next:** Confirm the equipment list with the Utility team and hand it over.

### 15 Oct 2026 — Dashboard build
- **Did:** Built the full workbook: Guide, Dashboard, Weekly/Monthly/Quarterly report, ALL DATA, Lists, Targets, Calc engine. 8 KPI cards, 10 charts, summary table, auto insights. Period selector with "Latest Month (auto)", Custom Range and month list. Like-for-like comparison against the previous period.
- **Found:** Data gaps: steam = 0 on some processing days, downtime columns empty, no fibre/shell data for boiler efficiency.
- **Next:** Fix the gaps with the data owners. Add efficiency fields.

### 19 Oct 2026 — Design
- **Did:** Recoloured the whole dashboard to Presco's colour code (forest green, ivory, grey). White chart cards with square corners. Gold dashed target lines. Red only for "worse than target". Replaced a background image that didn't print.
- **Found:** Fewer colours make the problems easier to see. When red only means "bad", a manager finds the issue in seconds.
- **Next:** Link live data, validate 3 days against source, request official targets.

### 21 Oct 2026 — Readable formulas
- **Did:** Replaced 28 shortcut names (like `SelStart` or `dDate`) with direct sheet and cell references in 89 formulas, e.g. `SUMIFS('ALL DATA'!$B$2:$B$1500, ...)` instead of `SUMIFS(dPGen, ...)`. Kept the Targets names (`tEnergy`, `tSteam`...) because they read like plain English.
- **Found:** Every value stayed identical after the change (1,883 cells checked). Shortcut names make formulas shorter but harder for someone else to follow and debug.
- **Next:** Link live utility data and validate 3 days against the source.

### 22 Oct 2026 — Efficiency without a fuel meter
- **Did:** Confirmed with the Utility and Lab teams that fibre/shell fed to the boilers, steam to turbine and calorific values are not recorded. Added two new data columns (Fibre fed, Shell fed) so they can start logging. Kept "Boiler Efficiency" on the dashboard showing **"No data logged"** on purpose, so the gap is visible to management. Replaced Turbine Efficiency with **turbine kWh per ton of steam** and added a new **Diesel Generator kWh per litre** KPI, both calculated from data we already have.
- **Found:** January baseline (clean days only): turbine ≈ 41 kWh per ton of steam; diesel generators ≈ 4.4 kWh per litre. A dashboard can drive data collection, not just report it — a visible blank is a stronger request than an email.
- **Next:** Confirm the 26–31 Jan zero-steam days; push for Steam Consumed and downtime logging.

### 29 Oct 2026 — Housekeeping
- **Did:** Moved all project files from the server folder to a local working folder and re-pointed every link. Set the files to update links on opening without a prompt.
- **Found:** Absolute file paths break when a folder moves. Keeping all linked files in one fixed folder tree avoids it.
- **Next:** Make the dashboard usable on any screen.

### 2 Nov 2026 — Any screen size
- **Did:** Fixed the print area and added a one-step "Zoom to Selection" so the dashboard and report fit any screen, with no macros.
- **Found:** Managers open reports on different laptops and monitors, so the layout has to fit without scrolling.
- **Next:** Protect the dashboard.

### 3 Nov 2026 — Protection and downtime link
- **Did:** Locked the Dashboard and the Weekly and Monthly Report sheets, leaving only the Period, View By and Custom date cells open. Linked the ALL DATA downtime columns to the Utility log of the new Factory Downtime Report and retired the old Downtime Tracker.
- **Found:** Two boilers make "boiler downtime" tricky. Adding both boilers' hours overstates it. Built an overlap rule: only the hours when both boilers were down count, capped at 24 h a day. Tested on six scenarios, including an overnight stop.
- **Next:** Clean up wording and presentation for the management review.

### 3 Nov 2026 — Ready for review
- **Did:** Plain-language clean-up of every title and note, consistent units (Ltr, Ton), sheet renamed to "Weekly and Monthly Report". Included the dashboard in a 15-slide presentation to management.
- **Found:** Small details (symbols, inconsistent units, leftover notes) distract a reader more than missing features.
- **Next:** Management feedback, official targets, user training.

