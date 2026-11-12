# ⏱️ Shop-floor Systems Downtime

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-1557b0?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query%20(M)-217346?style=for-the-badge)
![SharePoint](https://img.shields.io/badge/SharePoint-0078D4?style=for-the-badge&logo=microsoftsharepoint&logoColor=white)

> Dashboard that measures **non-productive downtime** caused by system failures (server, application, network and PLC outages) across sites and business units.

*The report itself (page names, measures, labels) is in Spanish.*

## 📌 Questions it answers

- How many hours and minutes of **downtime** did we have this month, and how does it compare with the **previous month**?
- Which **causes** generate the most downtime?
- Which **sites** and **business units** are hit the hardest?
- How many incidents were there, and what is the average downtime per incident?

## 🔄 Data flow

1. Incidents are logged in an Excel file on **SharePoint**: date, cause, site, shift, business unit, ticket and duration.
2. **Power Query** reads the file with `SharePoint.Files`, removes empty rows and converts durations (`hh:mm`) to **minutes** so they can be summed.
3. The model adds Month and Year columns plus a `TablaMeses` table for sorting.

## 📐 Measures

| Measure | What it measures |
|---|---|
| Total Downtime (min) / (hs) | Total downtime |
| Cantidad Incidentes | Number of logged incidents |
| % Downtime | Downtime minutes over a full day (1,440 min) |
| Downtime Mes Anterior | Month-over-month comparison with `PREVIOUSMONTH` |
| Downtime por Sitio | Downtime per site |
| … Visual | Formatted versions for cards and labels |

## 🔒 Data

The repository contains **only the model and the report design**, without the Excel file or the `.pbix`. The original log holds internal information and people's names.

## ▶️ How to open it

1. Open `Downtime.pbip` in Power BI Desktop.
2. Point the `Downtime` query to an Excel file with the same structure (sheet `Downtime`).
3. Refresh.
