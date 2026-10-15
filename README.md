Tata-Power-Electric-Vehicle-Charging-Infra-Insights-Excel-Based-
Tata Power EV Charging Analytics Dashboard analyzing charging demand, station utilization, customer behavior, revenue, CAPEX, EBITDA, ROI, payback period, &amp; district-wise EV demand gaps. The dashboard identifies high-potential locations &amp; supports data-driven decisions for infrastructure optimization, pricing, capacity expansion, &amp; future investment. 

# Tata Power EV Charging Infrastructure Analytics

## 📊 Advanced Excel Business Analytics Project (Power Query + Power Pivot + DAX)

An end-to-end Excel case study evaluating the performance, profitability and expansion potential of Tata Power's EV charging network across 18 Bengaluru districts. Operational sessions, customer behaviour and project-level financials are combined in one data model and presented as a **4-page interactive Excel dashboard** for senior management, strategy teams and operations managers.

The project turns raw operational and financial data into decisions on:

- Charging demand and time-of-day behaviour
- Station utilisation and plug efficiency
- Customer segments, income tiers and EV models
- CAPEX, EBITDA, payback and 5-year ROI
- Demand-supply gap and where to deploy next

---

## 🎯 Business Problem

You are a Data Analyst at Tata Power. Management wants to guide investment, pricing and infrastructure decisions by answering:

1. How is charging demand evolving, and can stations handle it?
2. Which stations are over- or under-utilised, and are plugs used efficiently?
3. Which customers and EV models drive usage and revenue?
4. Which districts and projects deliver the best ROI, and what is the payback period?
5. Where should new stations be prioritised, given demand and ROI?
6. How big is the gap between existing infrastructure and projected EV demand?

---

## 🗂️ Project Structure

```
TATA_POWER_EV_ANALYTICS/
│
├── Data/
│   ├── charging_sessions.csv
│   ├── charging_stations.csv
│   ├── customers.csv
│   ├── districts.csv
│   └── roi_bengaluru_districts.csv
├── Documentation/
│   └── data_dictionary_Tata_Power.txt
├── Excel/
│   └── WORK_TATA_POWER.xlsx          # Power Query + Data Model + 4-page dashboard
├── Images/
│   ├── data_model.png
│   ├── page1_business_usage.png
│   ├── page2_station_utilization.png
│   ├── page3_customer_demand.png
│   └── page4_roi_expansion.png
├── Presentation/
│   └── Tata_Power_EV_Charging_Analysis.pptx
└── README.md
```

---

## 🛠️ Tech Stack

| Area | Tools / Techniques |
|---|---|
| Spreadsheet & dashboard | Microsoft Excel (PivotTables, PivotCharts, Slicers, Timelines) |
| Data preparation | Power Query (import, clean, type, merge) |
| Data modelling | Power Pivot, star-style relationships |
| Calculations | DAX measures (`DIVIDE`, `SUM`, `COUNT`, `DISTINCTCOUNT`) |
| Visuals | Column, bar, line, area, pie and combo charts, KPI cards |
| Reporting | PowerPoint summary deck |

---

## 📦 Dataset

5 tables, about **114,000 session records** plus reference and planning tables.

| Table | Rows | Columns | Description |
|---|---:|---:|---|
| `charging_sessions` | 114,000 | 7 | One row per charging session (customer, station, time, kWh, tariff, cost) |
| `charging_stations` | 65 | 7 | Existing stations: district, operator, plugs, latitude / longitude |
| `customers` | 8,000 | 4 | Income tier, EV model, battery capacity |
| `districts` | 18 | 5 | Projected EVs, plugs and regular customers per district |
| `roi_bengaluru_districts` | 98 | 26 | Proposed projects: CAPEX breakdown, revenue, OPEX, EBITDA, payback, subsidy, ROI, priority tier |

**Session period:** 11 Aug 2024 – 8 Nov 2024 (90 days). August (21 days) and November (7 days plus one session on 8 Nov) are part-months.

Full column definitions are in [`Documentation/data_dictionary_Tata_Power.txt`](Documentation/data_dictionary_Tata_Power.txt).

---

## 🧩 Data Model

![Data model](Images/data_model.png)

```
districts (1) ───────────────< charging_stations (1) ───────────────< charging_sessions >─────────────── (1) customers
    │ district_name              station_id                              station_id / customer_id
    │
    └──────< roi_bengaluru_districts
             District = district_name
```

| Relationship | Cardinality | Join key |
|---|---|---|
| `customers` → `charging_sessions` | One-to-many | `customer_id` |
| `charging_stations` → `charging_sessions` | One-to-many | `station_id` |
| `districts` → `charging_stations` | One-to-many | `district_name` |
| `districts` → `roi_bengaluru_districts` | One-to-many | `district_name` = `District` |

`districts` is the central dimension: it links the operational side (stations and sessions) to the financial planning side (ROI projects).

---

## 🔎 Dashboard Pages

### Page 1: Business and Usage Overview

**Questions:** How is demand evolving? Can stations handle it? When do customers charge?

**KPIs:** Total sessions · Total energy (kWh) · Total revenue · Active customers · Avg revenue per session · Avg kWh per session

| KPI | Value |
|---|---:|
| Total charging sessions | 114,000 |
| Total energy consumed | 2,859,772 kWh |
| Total revenue | ₹4,96,93,947 (≈ ₹4.97 Cr) |
| Active customers | 8,000 |
| Avg revenue per session | ₹435.91 |
| Avg kWh per session | 25.09 |

**Visuals:** monthly demand trend with month slicer, charging pattern by hour of day.

### Page 2: Station Utilisation and Operational Efficiency

**Questions:** Which stations are over- or under-used? Are plugs used efficiently? How is load spread?

**KPIs:** Sessions per station · Sessions per plug · Plugs vs actual usage · Avg kWh per station · District-wise station density

| KPI | Value |
|---|---:|
| Stations | 65 (18 districts, 6 plugs each = 390 plugs) |
| Sessions per station | 1,754 |
| Sessions per plug | 292 |
| Avg kWh per station | 43,996 |

**Visuals:** sessions and kWh per station (ranked), stations per district, sessions vs existing vs projected plugs by district.

### Page 3: Customer and Demand Behaviour

**Questions:** Which customers drive usage and revenue? How does income tier shape behaviour? Which EV models and batteries dominate? Which segments have potential but low engagement?

**KPIs:** Unique customers · Sessions per customer · Avg kWh per customer · Revenue per customer · Usage by income tier · Usage by model and battery

| KPI | Value |
|---|---:|
| Unique customers | 8,000 |
| Sessions per customer | 14 (14.25) |
| Avg kWh per customer | 357.5 |
| Revenue per customer | ₹6,211.74 |

**Visuals:** revenue and energy share by income tier, usage by EV model with battery capacity, average battery by model.

### Page 4: Financial Performance and Expansion Strategy (ROI Focus)

**Questions:** Which districts and projects return the most? What is the payback by charger type? How do CAPEX, land lease and infrastructure affect profit? Where should we build next? What is the demand-supply gap?

**KPIs:** CAPEX per project · Annual revenue and EBITDA · Payback (with / without subsidy) · 5-year ROI · Existing stations vs projected EVs · Demand-supply gap · Priority tier

| KPI | Value |
|---|---:|
| Total CAPEX | ₹13,921.62 lakh (≈ ₹139.2 Cr) |
| Annual revenue | ₹4,628.64 lakh |
| Annual OPEX | ₹1,390.11 lakh |
| Annual EBITDA | ₹3,238.53 lakh (70% margin) |
| Payback without subsidy | 4.3 years |
| Payback with subsidy | 4.1 years |
| 5-year ROI (portfolio) | 16% |

**Visuals:** CAPEX per project, ROI by district, payback by charger type, priority tier vs proposed sites, demand-supply and infrastructure gap.

---

## 🧮 DAX Measures

| Measure | Logic |
|---|---|
| `Total_Charging_Sessions` | `COUNT(charging_sessions[session_id])` |
| `Total_Energy_Consumed (kWh)` | `SUM(charging_sessions[kwh_charged])` |
| `Total_Revenue` | `SUM(charging_sessions[total_cost])` |
| `Number_of_Active_Users` / `Unique_customer_count` | `DISTINCTCOUNT(customers[customer_id])` |
| `Avg_Revenue_Per_Session` | `DIVIDE([Total_Revenue], [Total_Charging_Sessions])` |
| `Avg_Kwh_Per_Session` | `DIVIDE([Total_Energy_Consumed (kWh)], [Total_Charging_Sessions])` |
| `Session per customer` | `DIVIDE([Total_Charging_Sessions], [Unique_customer_count])` |
| `Avg_kph_per_customer` | `DIVIDE([Total_Energy_Consumed (kWh)], [Unique_customer_count])` |
| `Avg_Revenue_per_customer` | `DIVIDE([Total_Revenue], [Unique_customer_count])` |
| `Total_CAPEX (lakhs)` | `SUM(roi_bengaluru_districts[Total_CAPEX_Lakh])` |
| `Total_Revenue (lakhs)` | `SUM(roi_bengaluru_districts[Annual_Revenue_Lakh])` |
| `Annual_OPEX (lakhs)` | `SUM(roi_bengaluru_districts[Annual_OPEX_Lakh])` |
| `Total_EBITDA (lakhs)` | `[Total_Revenue (lakhs)] - [Annual_OPEX (lakhs)]` |
| `Payback_Period (Without_Subsidy)` | `DIVIDE([Total_CAPEX (lakhs)], [Total_EBITDA (lakhs)])` |
| `Payback_Period (With_subsidy)` | `DIVIDE([Total_CAPEX (lakhs)] - SUM([Subsidy_Amount_Lakh]), [Total_EBITDA (lakhs)])` |
| `5yr_ROI%` | `DIVIDE([Total_EBITDA (lakhs)] * 5 - [Total_CAPEX (lakhs)], [Total_CAPEX (lakhs)])` |

---

## 📈 Key Findings

### Demand is steady, not growing
Sessions per day hold at about **1,280** in every month, and energy at about **32,100 kWh per day**.

| Month | Days covered | Sessions | Sessions / day |
|---|---:|---:|---:|
| Aug (from 11th) | 21 | 26,820 | 1,277 |
| Sep | 30 | 38,604 | 1,287 |
| Oct | 31 | 39,606 | 1,278 |
| Nov (to 7th) | 7 | 8,970 | 1,281 |

Monthly totals rise only because August and November are part-months.

### Half of all energy is charged between 08:00 and 15:59

| Band | Share of kWh | Avg kWh per hour |
|---|---:|---:|
| 08:00 – 15:59 | 50% | ~180k |
| 16:00 – 19:59 | 20% | ~142k |
| 20:00 – 07:59 | 30% | ~71k |

### Load is evenly spread across districts and stations
- **287 – 297** sessions per plug in all 18 districts (network 292).
- Station sessions range from 1,635 to 1,862 (−6.8% to +6.2% against the average).
- No station or district is a clear outlier today.

### Mid-range customers generate the most revenue

| Tier | Customers | Revenue share | Energy share | ₹ per kWh |
|---|---:|---:|---:|---:|
| High | 1,190 | 26% | 31% | 14.48 |
| Low-Mid | 3,990 | 26% | 33% | 13.85 |
| Mid-Range | 2,820 | 48% | 36% | 23.12 |

### Mid-size batteries drive usage
EVs with 25–40 kWh batteries average about 140k kWh per model, against 106k (under 25 kWh), 79k (40–65 kWh) and 109k (over 65 kWh). Top models by energy: Mahindra XUV400 EC Pro (158k kWh) and Hyundai Kona Electric (157k kWh).

### Returns are strong but uneven

| Metric | Result |
|---|---|
| Highest district ROI (5-year) | Bommanahalli 133%, Electronic City 78%, JP Nagar 66% |
| Lowest in the top-10 chart | Hebbal 19%, Rajajinagar 33% |
| Payback by charger (with subsidy) | AC 7.4 kW 2.0 yrs · AC 22 kW 3.0 · DC 50 kW 5.7 · DC 150 kW 9.6 |
| Subsidy effect | Only about 0.2 year at portfolio level |
| Priority tiers (98 proposed sites) | High 54 · Medium 7 · Low 37 |
| CAPEX concentration | Top 10 projects = ₹3,474 lakh (25% of total) |

### Large demand-supply gap

| Metric | Value |
|---|---:|
| Existing plugs | 390 |
| Projected plugs | 1,067 (+677, 2.7×) |
| Projected EVs | 35,200 |
| Projected EVs per planned plug | ≈ 33 |

---

## 💡 Business Insights

1. **Demand is flat, so expansion is a forecast decision.** Present load is balanced; the case for new capacity rests on projected EV growth (35,200 EVs against 390 plugs), not on congestion.
2. **Daytime carries the network.** Half of energy is charged 08:00–15:59 and overnight load is about 39% of peak, which supports off-peak pricing.
3. **Mid-range customers pay about 60% more per kWh** (₹23.12 against ₹13.85–14.48). Test whether tariff, charger type or time of day explains it.
4. **Charger choice drives payback.** AC Level-2 pays back in 2–3 years; 150 kW ultra-fast needs 9.6 years, beyond a 5-year horizon.
5. **Big builds concentrate risk.** Ten projects hold 25% of CAPEX, so stage-gate them.
6. **Prioritise by ROI and plug gap together.** Analyst rule used: *Deploy first* = ROI ≥ 45% and gap ≥ 50 plugs (Jayanagar, HSR Layout, Banashankari); *Quick win* = ROI ≥ 50% and gap < 50 (Bommanahalli, Electronic City, JP Nagar, Marathahalli); *Phase 2* = ROI 30–45% and gap ≥ 60 (Rajajinagar, Yelahanka); *Pilot only* = ROI < 30% (Hebbal).

---

## 📁 Main Deliverables

- `WORK_TATA_POWER.xlsx`: Excel workbook with the Power Query steps, data model, DAX measures and the 4-page dashboard
- `Tata_Power_EV_Charging_Analysis.pptx`: 28-slide editable summary deck
- Raw CSV datasets and the data dictionary

---

## ⚠️ Limitations and Data Notes

- **Synthetic portfolio dataset.** Findings are not real-world measurements of the Indian EV charging market.
- **Short window.** Sessions cover only 90 days (11 Aug – 8 Nov 2024), with part-months at both ends. The data dictionary states "2024-08-01 to 2024-12-31", but the file ends on 8 Nov 2024. No seasonality or growth trend can be concluded.
- **Plug count is uniform.** All 65 stations have exactly 6 plugs, which the data dictionary flags as a likely placeholder. Sessions-per-plug results depend on it.
- **Utilisation measures need correcting.** In the workbook, `Avg_utilization_per_station` and `Session/Plug_Ratio` divide sessions by the count of plug rows (65), which returns 1,754 (sessions per station). The correct sessions-per-plug is `DIVIDE([Total_Charging_Sessions], SUM(charging_stations[plugs_count]))` = **292**. `Avg. Kwh/Station` should be `DIVIDE([Total_Energy_Consumed (kWh)], DISTINCTCOUNT(charging_sessions[station_id]))` = **43,996** (the 25.1 shown is kWh per session).
- **ROI scope.** The portfolio 5-year ROI is 16%. The district ROI chart shows the top 10 districts only, and its pivot grand total (47%) covers those visible districts.
- **No per-model vehicle counts.** "High-potential, low-engagement" segments are judged from energy totals and should be validated with customers per model.
- **Cost split.** Land lease, equipment and civil costs are included in total CAPEX and OPEX; separate profitability impact is not isolated in the dashboard.
- **Rule-based prioritisation.** The district priority thresholds above are project-defined, not dataset fields. The dataset's own `Priority_Tier` (High / Medium / Low) applies at project level.

---

## 🚀 Future Improvements

- Extend session history to 12+ months for seasonality and growth analysis
- Validate real plug counts per station
- Add charger-level utilisation and uptime analysis
- Test time-of-day and income-tier pricing scenarios
- Add geographic mapping using station latitude and longitude
- Score every district on ROI and gap (ROI is currently shown for 10 districts)
- Build demand forecasting and an expansion recommendation model

---

## 👨‍💻 Project Focus

**Data Analytics | Microsoft Excel | Power Query | Power Pivot | DAX | Business Intelligence | EV Infrastructure**

This project shows how Excel's data model can be used not only for reporting, but also for:

**Data → Model → Analysis → Insight → Business Decision**

---

### 👤 Author

**Yavan Pratap** · Cohort 13, WsCube Tech
[LinkedIn](https://linkedin.com/in/yavan-pratap-singh) · yavan.pratap13@gmail.com
