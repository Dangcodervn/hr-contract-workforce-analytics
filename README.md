# HR Contract & Workforce Analytics

A Power BI analytics project examining workforce composition and employee turnover at **Topica Edtech Group** (Vietnam, 2008–2019), built from 2,586 raw HR contract/status records.

## Dashboard

### Overview
![Overview](Images/Overview.png)

### Turnover
![Turnover](Images/Turnover.png)

## Key Insights

All figures below were independently recomputed from `HR_DATA.csv` rather than taken from any prior report.

- **Attrition rate: 39.6%** (1,023 of 2,586 employees have left) — note this corrects an earlier internal report that cited 50%.
- **88.8% of departures were voluntary resignations** (not company-initiated or mutual agreement).
- **Hiring volume grew from 6 (2008) to a peak of 841 (2018)**, then declined to 776 (2019). The 2018 peak lines up with Topica's **$50M Series D funding round (Nov 2018)** — hiring visibly accelerated starting January 2019, roughly two months after the round closed.
- **Location matters more than headcount alone suggests**: Ho Chi Minh City employees have a 52.2% attrition rate vs. 40.7% in Hanoi, despite Hanoi being the larger office.
- **Full-time Collaborators (LX1)** have the highest attrition rate of any job level (63.6%) — higher than the much larger "Specialist" group (40.3%), even though Specialists account for more total departures in absolute terms.
- **Online Operations** is the job function with the single highest turnover rate (59.4%), ahead of the higher-profile Admissions Consultant function (56.0%).

## Data Quality Notes

This dataset is a **snapshot of each employee's latest HR transaction**, not a full event history — a structural constraint that shapes what can and can't be reliably analyzed:

- Point-in-time headcount reconstruction (e.g. "headcount by month") is **not reliable** with this data, since an employee's prior employment stints aren't retained — only validated through direct testing, documented for anyone extending this analysis.
- ~4.5% of records show internally inconsistent dates (rehire cases where the record's hire date postdates its own termination date); these are flagged and excluded from tenure calculations rather than silently estimated.
- Metrics built on counted *events* (hires, exits) are reliable; metrics that require reconstructing *state at an arbitrary past date* are not, given this data's structure.

## Tech Stack

- **Power BI Desktop** (PBIP / TMDL project format)
- **Power Query (M)** for data cleaning and column derivation
- **DAX** for measures, including explicit time-intelligence patterns (`USERELATIONSHIP`, `DATEADD`) to support a role-playing date dimension (hire date vs. exit date)

## Repository Structure

```
├── HR_DATA.csv                  # Raw HR contract/status records (2,586 rows)
├── Definition_Data.xlsx         # Column definitions provided with the source data
├── HR analytical report.docx    # Original reference report (see Data Quality Notes above)
├── Images/                      # Dashboard screenshots
└── PowerBI/                     # Power BI project (PBIP format)
    ├── HR Contract & Workforce Analytics.pbip
    ├── HR Contract & Workforce Analytics.Report/
    └── HR Contract & Workforce Analytics.SemanticModel/
```

## Opening the Project

Requires Power BI Desktop with PBIP support enabled (File > Options > Preview features). Open `PowerBI/HR Contract & Workforce Analytics.pbip`.
