# Factory Downtime Report

**Author:** Divine C. Alloyshius, Manufacturing Analyst · Presco Plc
**Contact:** divine.alloyshius@siat-group.com · +234 814 760 3384
**Category:** Downtime & Availability Analytics · Operations Reporting
**Tools:** Microsoft Excel 2019 (no VBA, no add-ins)
**Status:** In daily use. Presented to management for feedback in November 2026.

## Overview

Downtime is any time a department did not run as scheduled, whatever the cause: no fruit, no power, no steam, a breakdown, cleaning, full tanks. Equipment breakdowns are only one part of it.

Before this report, stoppages were not recorded in one place, so nobody could say how many hours each department lost in a month, or why. This workbook gives every department one simple log and turns those logs into a factory-wide management summary.

## The business problem

| Before | Impact |
|---|---|
| Stoppages noted in different places, or not at all | No total of hours lost per department or for the factory |
| No common way to describe the reason | Impossible to say whether the factory stops mostly for raw material, utilities, breakdowns or planned work |
| Breakdowns not linked to maintenance jobs | No way to see the technician, cause and work done behind a stoppage |
| No comparison with the previous period | No way to tell whether things were getting better or worse |

## The solution

**One workbook with five department logs:** Mill, KCP, Utility, Refinery (which also covers Tankfarm, as Tankfarm runs under Refinery) and Fractionation.

**Each log (one row per stoppage):**

- Date, shift (Day / Night), start time, end date if it ran past midnight, end time. Downtime hours calculate themselves.
- Downtime category from the department's own list (up to 15 per department). Planned / Unplanned and the **reason group** fill in automatically.
- Station and equipment (from the maintenance Master List) when the cause is a breakdown, plus the **maintenance job number**. The technician, cause and work done are then pulled from the maintenance log automatically.
- Status (Ongoing / Resolved) is automatic: no end time means the stoppage is still ongoing.
- A Data Check column flags rows with missing information or wrong times.

**Eight reason groups shared by every department**, so the factory summary can add them up: Raw material / supply, Equipment breakdown, Utility supply, Planned maintenance / cleaning, Storage / dispatch, Manpower, Process / quality, Other.

**Management Summary** (pick any period: day, week, month, quarter, year or custom):

- Factory downtime, factory availability, stoppages, unplanned share, equipment breakdown hours, change against the previous period
- Department table: scheduled hours, downtime, availability, stoppages, planned vs unplanned, top reason, previous period, month-to-date, year-to-date
- Why the factory stopped: hours by reason group per department
- Station detail per department and the top 10 equipment by downtime
- Key messages written automatically in plain sentences

**Department Report:** pick one department and a period to see categories, stations, shifts, top equipment, the trend and the full list of stoppages.

## Linked to the rest of the system

- **Maintenance:** a breakdown row carries the maintenance job number, so downtime and maintenance tell the same story.
- **Utility Dashboard:** the Utility log feeds the utility dashboard's downtime columns (boiler, turbine, generator, water plant, cooling water) day by day.
- **Two boilers, one boiler figure:** the factory has two boilers (Atmindo and Vickers). One boiler down while the other runs is not a boiler outage. Helper columns work out only the hours when **both** boilers were down at the same time, so the utility dashboard never shows more than 24 hours a day and never counts a single-boiler stop as lost steam.

| Situation | Boiler downtime |
|---|---|
| Atmindo down 06:00 to 14:00, Vickers down 10:00 to 12:00 | 2 h (only the overlap) |
| Both down all day | 24 h, not 48 |
| Only one boiler down | 0 h |
| Both down overnight, 23:00 to 02:00 | 3 h |

## Challenges and how they were solved

| Challenge | Solution |
|---|---|
| Presco runs **two shifts**, not three | Shift list set to Day / Night everywhere. |
| Extra columns (Reported By, Action Taken) duplicated what the maintenance log already holds | Removed them. Kept only what the downtime report needs, and look up the rest by job number. |
| "New" shown when there was no previous data looked like an error | Shows "n/a" instead. |
| Tankfarm stoppages are really refinery stoppages | Tankfarm removed as a department; Refinery covers it. Fractionation added as its own department. |
| Utility dashboard reads this file while it is closed | Used SUMPRODUCT (which works on closed files) instead of SUMIFS (which does not). |
| Counting boiler downtime fairly | Overlap formula between the two boilers' stoppages, tested on six scenarios including overnight stops. |
| Formulas could be overwritten by users | Logs protected: input columns stay open, formula columns are locked, filters still work. |
| A rebuild once left duplicate cells and Excel asked to repair the file | Found and removed the duplicates, and added a duplicate-cell and file-structure check before any file is saved. |

## Benefits and use cases

- **Management:** hours lost per department and for the whole factory, the main reasons, and whether it is improving.
- **Department managers and supervisors:** their own report, by category, station and shift.
- **Maintenance:** breakdown downtime tied to job numbers and technicians.
- **Utility:** equipment downtime flows into the utility dashboard with no double entry.
- **Accountability:** every stoppage has a date, a time, a reason and an owner.

## Roadmap

- [x] Five department logs, management summary, department report
- [x] Linked to maintenance job numbers and to the Utility Dashboard
- [x] Boiler overlap rule
- [x] Formula protection
- [x] In daily use; presented to management for feedback (Nov 2026)
- [ ] Decide whether Packaging needs its own downtime log
- [ ] Train all department users
- [ ] Feed the planned Factory Summary Report

## Skills demonstrated

Downtime and availability analytics · Data model design · Linked workbooks · Time-interval logic in Excel · Data validation · Report design for managers
