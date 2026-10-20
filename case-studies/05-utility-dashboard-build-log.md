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
