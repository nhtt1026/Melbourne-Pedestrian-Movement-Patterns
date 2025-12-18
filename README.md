## Project Context:
The City of Melbourne is strengthening its urban mobility strategy by understanding how pedestrians move across the city using a network of sensors that capture directional counts at multiple locations. The goal is to identify when and where crowding happens, then translate those patterns into practical actions for safer and more comfortable streets.

**Data source:** [City of Melbourne Open Data Portal – Pedestrian Counting System (Monthly counts per hour)](https://data.melbourne.vic.gov.au/explore/dataset/pedestrian-counting-system-monthly-counts-per-hour/information/)

## Key Objectives:
1. Where are the highest pedestrian concentration areas across Melbourne’s sensor network?
2. What time patterns define pedestrian activity (daily peaks and weekly rhythms)?
3. How do inbound vs outbound movements behave at the busiest locations?
4. What targeted interventions can city planners apply to improve pedestrian capacity, flow, and safety?

## Dashboard Overview:
The dashboard is designed as an operational planning lens for city planners: it surfaces citywide activity, spatial hotspots, directional flow differences, and hour-by-hour pressure points to support infrastructure and safety decisions.

<img width="1753" height="952" alt="image" src="https://github.com/user-attachments/assets/9a9ed44a-709e-4526-97d6-3a2c84b9666c" />

## Key Findings:
### 1) Pedestrian Flow Trends Over Time (for seasonality & long-term change):

<img width="1794" height="890" alt="image" src="https://github.com/user-attachments/assets/4eb6acf0-f6d3-4536-ba58-0cab0812b6eb" />

- This chart highlights clear seasonality and longer-term shifts in pedestrian activity. Foot traffic **rises strongly toward mid-2025** (peaking around **~7.1K in Jul 2025**), which supports planning **higher-capacity operations** and **maintenance scheduling** in periods when the CBD is most active. The uplift versus 2024 (roughly **~2.0–2.3K**) also provides a useful benchmark for evaluating whether foot traffic is structurally increasing over time.

- The sharp spike near mid-2025 and the pronounced drops (e.g., **~1.3K early 2024** and **~1.7K at the end of the series**) should be treated as **investigation triggers**. These patterns may relate to **major events, construction works, disruptions, weather impacts, or partial/incomplete reporting** in the latest period.

### 2) Pedestrian Volume Map:

<img width="1536" height="753" alt="image" src="https://github.com/user-attachments/assets/dacfdf53-44a4-444d-97f8-aaef450d131e" />

- The map shows pedestrian activity concentrating most strongly in **Melbourne’s CBD and Southbank**, especially around **major transport hubs, retail streets, and riverfront destinations**. These hotspots indicate where footpaths and crossings are under the most daily pressure, and where small design changes can improve safety and comfort for the largest number of people.

- For city planning, this supports **place-based investment**: prioritise upgrades in the CBD core (wider footpaths, safer intersections, clearer crossings) and strengthen Southbank’s high-activity routes with **better lighting, wayfinding, and pedestrian-friendly links** between stations, key streets, and popular venues.

### 3) Directional Flow Comparison (Inbound vs Outbound at Top Sensor Locations):

<img width="1536" height="781" alt="image" src="https://github.com/user-attachments/assets/39113463-5b0a-4e40-ad9e-3ece35c1d40a" />

- **Directional imbalance flags "source" vs "destination” streets**: Several locations show stronger **outbound** than inbound (e.g., **Eli124_T** ~1.53K outbound vs ~1.18K inbound, **Col620_T** ~0.86K vs ~0.47K, and **Eli368_T** ~0.98K vs ~0.75K), suggesting these streets act as dispersal routes after work or events.
- **Consistent inflow indicates high-attraction nodes**: Sensors such as **Swa31** and **RMIT_T** show stronger **inbound** movement, consistent with **destinations** like retail, campus, or major stops.
- **Crossing demand remains high even when flows are balanced**: Where inbound and outbound are close (e.g., **VAC_T ~0.68K vs ~0.66K)**, the issue is less about direction and more about **2-way friction**. These are strong candidates for **safer, faster crossings and more space at corners.**
- **City planners should use time slicing to validate pressure shifts through the day**: Filter this view by hour and day to confirm whether the imbalance flips (morning inflow vs evening outflow), then tune signal timing and crowd management to match real demand.

### 4) Peak Hour Distribution:

<img width="1536" height="768" alt="image" src="https://github.com/user-attachments/assets/6e1c7a8a-f6c7-4038-bb4c-cff85dcd176f" />

- 

## Recommendations for City Planners
### 1) Upgrade pedestrian capacity where pressure is structurally highest
The CBD and Southbank should be prioritized for wider footpaths, kerb extensions, and additional crossing opportunities (including mid-block crossings) to reduce congestion and improve comfort during the midday peak. Shaded seating and weather protection will also matter because the highest demand occurs in daytime conditions.  [oai_citation:14‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)

### 2) Adjust intersection operations for Friday-night safety and flow
The late-night Friday peak suggests a targeted safety window. Near nightlife and entertainment areas (e.g., Swanston Street and Flinders Street), longer pedestrian green times and “pedestrian-only crossing moments” (vehicles stopped briefly while people cross) can reduce conflict risk and speed up dispersal when crowds are leaving venues.  [oai_citation:15‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)

### 3) Use light-touch crowd guidance during known peak windows
For Friday midday and late-night periods, introduce temporary lane markings or one-way walking guidance at busy intersections and event spaces, supported by clear wayfinding signs. This reduces “counter-flow friction” without relying on physical barriers, and can be scaled up during major events.  [oai_citation:16‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)

### 4) Improve accessibility and reduce micromobility conflict in the core
In high-traffic areas, prioritize tactile paving, audible crossings, and smoother kerb transitions so mobility constraints do not become safety risks in crowded conditions. Pair this with slow-speed zones and clearer separation for scooters and bicycles inside the CBD to reduce pedestrian conflict points.  [oai_citation:17‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)

### 5) Turn the dashboard into a weekly operating rhythm
Use automated pedestrian reporting to guide weekly planning decisions such as maintenance timing, event readiness, and targeted resourcing. Over time, the same sensor patterns can validate whether interventions are working by tracking whether peak-hour pressure is reducing at known hotspots.  [oai_citation:18‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)

## Suggested Next Investigations
- Pinpoint the specific sensors driving the 10PM Friday peak to confirm whether the pattern is venue-led, transport-led, or corridor-led.  [oai_citation:19‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)  
- Compare “before vs after” around any planned upgrades (kerb extensions, crossings, slow-speed zones) using the same heatmap structure to quantify impact.  [oai_citation:20‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)  
- Add event calendars and weather overlays to explain spikes that are not seasonal (e.g., festivals, sports nights, heatwaves).

## Deliverable
- Power BI dashboard focused on pedestrian movement patterns and actionable planning insights for City of Melbourne urban mobility and safety planning.  [oai_citation:21‡21538241_Assignment2_HoangThanhTrucNguyen_Report.pdf](sediment://file_00000000119071fa9c298f18aae53a3f)
