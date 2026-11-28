# Factory Data and Reporting System (Overview)

**Author:** Divine C. Alloyshius
**Contact:** alloychimezie@gmail.com · +234 814 760 3384
**Status:** Utility, Maintenance, Factory Downtime and Mill & KCP dashboards in daily use. Presented to management as *Think on Data* on 21 November 2026.

![The three projects and the problems they solve](../screenshots/08-system-three-projects.png)

## Why this started

I joined the production team in October 2024, in charge of production reporting. I quickly saw that the factory produces a lot of data every day, but much of it is not properly recorded or put to full use. With a one-year diploma in Data Analysis behind me, I set myself one goal:

> **No data in the factory should go unrecorded or unused.**

Every section, from the Mill and KCP to Utility, Refinery, Fractionation, Tankfarm, Packaging and Maintenance, should record its data in one structured way, and that data should become reports that executives, managers, supervisors and technical officers can use to make decisions.

## How the pieces fit together

```
Master Lists (equipment, technicians, causes)
        │
        ├──► 7 section Maintenance Logs ──► Maintenance Performance Dashboard
        │              ▲ job number
        └──► Factory Downtime Report (5 departments)
                       │ utility downtime (boiler overlap rule)
                       │ mill and KCP stoppage hours
                       ▼
Daily utilities entry ──► Utility Dashboard + Weekly / Monthly / Quarterly report
Mill production file  ──► Mill & KCP Performance Dashboard + Weekly / Monthly report
```

| Project | Case study |
|---|---|
| Utility Dashboard | [05-utility-dashboard.md](05-utility-dashboard.md) |
| Maintenance Logs and Dashboard | [06-maintenance-system.md](06-maintenance-system.md) |
| Factory Downtime Report | [07-factory-downtime-report.md](07-factory-downtime-report.md) |
| Wrench Time Tracking | [09-wrench-time.md](09-wrench-time.md) |
| Mill & KCP Performance Dashboard | [10-mill-kcp-dashboard.md](10-mill-kcp-dashboard.md) |

## What the factory gains

| Benefit | How |
|---|---|
| More output | Less downtime means more FFB and CPO processed |
| Lower utility cost | Power, steam and diesel use watched against targets, so waste shows up quickly |
| Fewer repeat breakdowns | We see which machines fail most and fix the root cause |
| Time saved | No manual compiling; reports are ready daily, not put together at month end |
| Clear ownership | Every KPI has an owner, so problems are fixed by the people closest to them |

## Presenting it to management

In November 2026 I sent a 15-slide presentation and the files to management for their feedback on any changes needed. The deck covers the goal, the three projects, what the factory gains, where the data stands, why putting data to use matters, the role of a Manufacturing Analyst, the planned summary report, shared ownership, what comes next and what still needs to be in place.

Lessons from preparing it:

- **Lead with the problem, then the benefit.** Managers respond to "more output, less waste, faster fixes" more than to a list of features.
- **Be honest about status.** Test data is labelled as test data. Equipment lists still being completed are shown as "in progress", not "done".
- **Plain words win.** Every slide was rewritten until a busy manager could read it at a glance.

### Think on Data: the management session (21 November 2026)

I then presented the system in person to management, including the mill and utility managers, under one idea: **Think on Data, optimising our efficiency through data.** The aim was to move the factory from being operations-inclined ("did we run today?") to data-inclined ("how well did we run, what did it cost, and what do we fix first?").

The session covered what is live, what the data had already found, why the tools are easy to adopt, and four proposals: a daily, weekly and monthly factory summary report, a review every two weeks with key players from every section, agreed targets with an owner for each section, and training.

What worked:

- **Value first, never blame.** Every finding was framed as something we can now see and work on, not as anyone's failure.
- **Number, meaning, action.** Each finding was presented as the figure, what it means, and what we can do about it.
- **Built on what already exists.** No new software, nothing extra to fill in: the tools read the records the teams already keep.

The session led to ABS (ERP) access being requested for the key players, and to the next step of connecting the dashboards to the ABS server.

## Coming next

- **Refinery, Fractionation & Packaging Dashboard** (built, ready for live data): the refinery to the same standard as the mill dashboard. See [case study 11](11-refinery-fractionation-packaging.md).
- **Tankfarm Stock Dashboard** (in progress): stock by tank across mill and refinery products.
- **Factory Summary Report** (in progress): one daily, weekly and monthly report covering every section, with KPIs against targets and a named owner for each KPI. The aim is shared ownership, so results are not the line manager's responsibility alone.
- **One data source:** working with the ABS team to connect the dashboards to the ABS server (SQL Server), so every report reads from the same live data.
- **Training** for the responsible persons in each section.
- **Review every two weeks** with key players from every section: achievements, challenges, actions with owners and dates, and follow-up.

## Still to be in place

- Equipment lists for the remaining sections (in progress with the maintenance department)
- Electrical and instrumentation work recorded in the job cards
- Official targets agreed with each section manager
- Fibre and shell fed to the boiler, for boiler efficiency
