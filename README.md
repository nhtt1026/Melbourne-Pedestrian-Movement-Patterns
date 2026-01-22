# Melbourne Pedestrian Movement Patterns: End-to-End Azure Data Solution

## About
An end-to-end Azure Data Factory (ADF) ETL pipeline and Power BI dashboard that turns City of Melbourne pedestrian sensor counts into planning-ready insights on CBD/Southbank hotspots, daily peak windows, and late-night surges for safer, better-managed streets.

---

## 1) Project Context:

The City of Melbourne uses a network of pedestrian sensors to understand where and when crowding occurs, then translates those patterns into practical actions for safer and more comfortable streets.  

**Data source:** [City of Melbourne Open Data Portal – Pedestrian Counting System (Monthly counts per hour)](https://data.melbourne.vic.gov.au/explore/dataset/pedestrian-counting-system-monthly-counts-per-hour/information/)

**Timing note:** The open dataset is updated over time, but this portfolio analysis is based on a data snapshot downloaded on Oct 15, 2025. The dashboard examples in this project focus on the **13 Oct 2023 – 5 Oct 2025** analysis window shown in the report filters.

---

## 2) Solution Overview:
This project delivers a cloud-based pipeline and dashboard that:
- Ingests pedestrian count + sensor reference data on a **15-minute schedule** to simulate near real-time monitoring.
- Stores raw files in Blob Storage (traceable folder structure for each ingestion cycle).
- Cleans and transforms the data into **hourly summaries per sensor**, including inbound/outbound totals and peak-time indicators.
- Loads curated tables into **Azure SQL Database** for BI consumption.
- Visualises results in Power BI to support **infrastructure prioritisation, signal timing, and peak/event operations**.

---

## 3) Architecture:
**Data Source → Raw → Transform → Serve → Visualise**
- Source: City of Melbourne pedestrian datasets (counts + sensor locations)
- Raw zone: Azure Blob Storage (`staging/`)
- Transform: ADF Mapping Data Flows (cleaning, hourly aggregation, peak ranking)
- Serve: Azure SQL Database (curated tables)
- BI: Power BI dashboard connected to SQL

<img width="2078" height="592" alt="image" src="https://github.com/user-attachments/assets/0e1beaf0-e514-4c4e-9b95-ff3eedb27cc3" />

---

## 4) Data Pipeline:
### 4.1 Ingestion:
- ADF pipeline connected to 2 CSV sources (`pedestrian count` + `pedestrian sensor`) stored in Blob Storage.

<img width="2616" height="542" alt="image" src="https://github.com/user-attachments/assets/4aee5bc5-b44e-46c8-baab-138d9789f519" />

<img width="2422" height="502" alt="image" src="https://github.com/user-attachments/assets/9b8a84c7-4d98-4aaf-a955-820e58eb7d88" />

<img width="2388" height="476" alt="image" src="https://github.com/user-attachments/assets/e4963316-8996-4155-8fd1-a3071c1e36cf" />

- Pipeline runs every **15 minutes**; each cycle lands raw files into organised directories for traceability.

<img width="2086" height="956" alt="image" src="https://github.com/user-attachments/assets/e0b93cfd-0cf5-483e-84cb-0f9e134ff1a1" />

### 4.2 Data Transformation:
- Handle missing/invalid values (standardise unknowns, remove invalid records):
   -  `pedestrian count`:
  
<img width="1928" height="1158" alt="image" src="https://github.com/user-attachments/assets/a907f4cc-a515-4f71-bf0a-557f1fa3a35e" />

<img width="1996" height="1032" alt="image" src="https://github.com/user-attachments/assets/1709a661-4e52-4ebd-b277-95b58944a0a5" />

   -  `pedestrian sensor`:

<img width="1490" height="1080" alt="image" src="https://github.com/user-attachments/assets/e74ffa08-2820-4c9a-b556-a2ec64b9c063" />

<img width="1966" height="900" alt="image" src="https://github.com/user-attachments/assets/b0b0450d-7d02-4fd6-8aad-abe91d1f50e7" />

- Create `HourStart` from date + hour fields

<img width="1990" height="1054" alt="image" src="https://github.com/user-attachments/assets/46f5a8c6-91a6-4878-877a-97ac3eaffd29" />

<img width="2256" height="802" alt="image" src="https://github.com/user-attachments/assets/1450b2aa-dacc-4c8a-8f74-5a0132898705" />

- Aggregate minute-level records into **hourly counts per sensor**:
  - `Sum_Direction_1`, `Sum_Direction_2` (inbound/outbound)
  - `Hourly_Counts` (total across directions)

<img width="1846" height="1164" alt="image" src="https://github.com/user-attachments/assets/8f79d1c2-ab27-4a27-8c1d-20ffe969b732" />

<img width="2652" height="873" alt="image" src="https://github.com/user-attachments/assets/85becf50-89fc-4384-87eb-2212eac8acf1" />

- Peak time logic using window ranking (e.g., `DailyRank` by location/date)

<img width="2586" height="446" alt="image" src="https://github.com/user-attachments/assets/178d5971-b1f5-49a4-8653-dcdffa7eada1" />

<img width="2572" height="660" alt="image" src="https://github.com/user-attachments/assets/abf2c02e-851a-4806-9dfb-8c425f676966" />

<img width="2654" height="987" alt="image" src="https://github.com/user-attachments/assets/96c9b3ac-8e96-4fa0-afd1-087ac4351a78" />

### 4.3 Load curated tables into Azure SQL Database for consistent BI querying:
- Debug before triggering data pipeline:

<img width="1892" height="1034" alt="image" src="https://github.com/user-attachments/assets/de360652-257b-4d96-91dc-40bea04434e9" />

- Real-time data flow trigger every 15 mins:

<img width="1888" height="828" alt="image" src="https://github.com/user-attachments/assets/0f22d923-2df1-4a95-a520-0be3eecafdb1" />

- Load all transformed tables into SQL database:

<img width="1852" height="866" alt="image" src="https://github.com/user-attachments/assets/ac95463b-8397-4930-9cf2-35d398ddee5f" />

---

## 5) Data Model (SQL) - Taken the data model capture from Power BI:
> List the final tables you load (e.g., `dim_sensor`, `fact_hourly_counts`, `fact_peak_by_location`), keys, and relationships.

Recommended minimum:
- `dim_sensor` (sensor metadata + coordinates)
- `fact_ped_hourly` (HourStart, Location, inbound, outbound, total)
- Optional: `fact_peak_hour` (Location, Date, PeakHourStart, PeakHourlyCounts)

---

## 6) Power BI Dashboard:

### 6.1 Headline KPIs:
- Total pedestrians: **38,000**
- Average per hour: **380**
- Peak hour: **3,000** (single location, single hour)

<img width="1753" height="952" alt="image" src="https://github.com/user-attachments/assets/7b2e08b5-b421-491c-b12a-9c0c7777500d" />

### 6.2 Pedestrian Flow Trends Over Time (for seasonality & long-term change):

<img width="1794" height="890" alt="image" src="https://github.com/user-attachments/assets/4eb6acf0-f6d3-4536-ba58-0cab0812b6eb" />

- This chart highlights clear seasonality and longer-term shifts in pedestrian activity. Foot traffic **rises strongly toward mid-2025** (peaking around **~7.1K in Jul 2025**), which supports planning **higher-capacity operations** and **maintenance scheduling** in periods when the CBD is most active. The uplift versus 2024 (roughly **~2.0–2.3K**) also provides a useful benchmark for evaluating whether foot traffic is structurally increasing over time.

- The sharp spike near mid-2025 and the pronounced drops (e.g., **~1.3K early 2024** and **~1.7K at the end of the series**) should be treated as **investigation triggers**. These patterns may relate to **major events, construction works, disruptions, weather impacts, or partial/incomplete reporting** in the latest period.

### 6.3 Pedestrian Volume Map:

<img width="1536" height="753" alt="image" src="https://github.com/user-attachments/assets/dacfdf53-44a4-444d-97f8-aaef450d131e" />

- The map shows pedestrian activity concentrating most strongly in **Melbourne’s CBD and Southbank**, especially around **major transport hubs, retail streets, and riverfront destinations**. These hotspots indicate where footpaths and crossings are under the most daily pressure, and where small design changes can improve safety and comfort for the largest number of people.

- For city planning, this supports **place-based investment**: prioritise upgrades in the CBD core (wider footpaths, safer intersections, clearer crossings) and strengthen Southbank’s high-activity routes with **better lighting, wayfinding, and pedestrian-friendly links** between stations, key streets, and popular venues.

### 6.4 Directional Flow Comparison (Inbound vs Outbound at Top Sensor Locations):

<img width="1536" height="781" alt="image" src="https://github.com/user-attachments/assets/39113463-5b0a-4e40-ad9e-3ece35c1d40a" />

- **Directional imbalance flags "source" vs "destination” streets**: Several locations show stronger **outbound** than inbound (e.g., **Eli124_T** ~1.53K outbound vs ~1.18K inbound, **Col620_T** ~0.86K vs ~0.47K, and **Eli368_T** ~0.98K vs ~0.75K), suggesting these streets act as dispersal routes after work or events.
- **Consistent inflow indicates high-attraction nodes**: Sensors such as **Swa31** and **RMIT_T** show stronger **inbound** movement, consistent with **destinations** like retail, campus, or major stops.
- **Crossing demand remains high even when flows are balanced**: Where inbound and outbound are close (e.g., **VAC_T ~0.68K vs ~0.66K)**, the issue is less about direction and more about **2-way friction**. These are strong candidates for **safer, faster crossings and more space at corners.**
- **City planners should use time slicing to validate pressure shifts through the day**: Filter this view by hour and day to confirm whether the imbalance flips (morning inflow vs evening outflow), then tune signal timing and crowd management to match real demand.

### 6.5 Peak Hour Distribution:

<img width="1536" height="768" alt="image" src="https://github.com/user-attachments/assets/6e1c7a8a-f6c7-4038-bb4c-cff85dcd176f" />

- This chart shows a clear daily cycle in pedestrian movement. Activity stays very low overnight (roughly 0:00–6:00), then rises steadily through the morning. The strongest concentration sits in **late morning to early afternoon (around 10:00–14:00)**, with the **highest point around 12:00 (~5.8K)**, indicating the most consistent **high-demand period** for sidewalks, crosswalks, and station entrances.
- A second, smaller peak appears **late at night (around 22:00, ~3.4K)**, which suggests a distinct late-evening dispersal pattern rather than a typical commuter peak. This supports targeted night-time safety actions (lighting, clearer crossings, and crowd guidance) in busy precincts during late hours.

### 6.6 Pedestrian Intensity Heatmap by Hour & Day:

<img width="639" height="877" alt="image" src="https://github.com/user-attachments/assets/48824286-817c-469d-ba93-1c9d424c2224" />

- The strongest concentration appears on **Friday around midday (12:00)**, suggesting CBD activity is most intense during end-of-week work and retail periods.
- **Weekday lunchtime pressure** is also significant. **Monday (~14:00)** and **Tuesday (~13:00)** show clear spikes, pointing to a recurring **lunch and early-afternoon surge** likely driven by office, university, and retail movement. This supports targeted measures such as smoother crossing operations and footpath capacity checks during weekday lunchtime.
- **A clear late-night surge shows up on Friday**. The spike around **22:00 on Friday** points to **the night-time economy or event-related movement**, where safety and crowd flow need extra attention.
- **Weekends look flatter and more spread out**. Activity is present, but it is less “spiky,” which supports **lighter, targeted resourcing** rather than heavy weekday-style controls.
- **Implication**: Melbourne city planners can use **time-based interventions**. For example, strengthen crossing capacity and staffing around **Friday or the early-week lunchtime**, then shift to **lighting, surveillance, and night transport coordination** for **Friday late-night peaks**, instead of applying the same settings all week.

## Recommendations:

- **Protect capacity during peak windows:** Late morning to early afternoon (especially Mon & Tues) carries the highest consistent demand, so keep key routes open and detours clear, safe, and accessible when works are unavoidable.
- **Tune intersections for Friday late-night conditions:** Friday shows a distinct late surge (~22:00), supporting targeted night safety measures (lighting, clearer crossings, crowd guidance) in busy precincts.
- **Prioritise CBD/Southbank upgrades first:** Hotspots cluster around transport hubs, retail streets, and riverfront destinations, where small design changes can benefit the largest number of pedestrians.  

## Suggested Next Investigations:

- **Explain peaks using external drivers**: Overlay pedestrian counts with **weather, public events, and planned disruptions** (street works, station closures, major detours) to separate true demand growth from temporary effects. This makes “why did it spike?” explanations more defensible when planners are justifying operational or capital decisions.
- **Measure “before vs after” impacts of upgrades**: Use the time series to compare footfall **before and after** changes at specific sites (new crossings, widened footpaths, signal timing updates, temporary closures). Pair this with the heatmap windows to check whether upgrades reduce pressure in the highest-demand periods, not just in averages.
- **Segment sensors by behaviour, not by a single label**: Use each sensor’s hour-by-day “time signature” to identify whether it is commuter-driven (AM/PM peaks), retail/lunch-driven (midday peak), or night-economy-driven (late-night uplift). Many CBD sensors will show mixed patterns, so a **primary + secondary pattern** (or simple score-based approach) is more realistic than assigning 1 category.
- **Add a simple forecasting layer for planning**: Extend the dashboard with short-term forecasts (next week/month) and scenario checks to estimate how works or new developments may shift footfall.
