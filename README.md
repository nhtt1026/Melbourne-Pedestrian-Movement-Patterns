## Project Context:

The City of Melbourne is strengthening its urban mobility strategy by understanding how pedestrians move across the city using a network of sensors that capture directional pedestrian counts at multiple locations. The goal is to identify when and where crowding happens, then translate those patterns into practical actions for safer, more comfortable, and better-managed streets.

**Data source:** [City of Melbourne Open Data Portal – Pedestrian Counting System (Monthly counts per hour)](https://data.melbourne.vic.gov.au/explore/dataset/pedestrian-counting-system-monthly-counts-per-hour/information/)

**Timing note:** The open dataset is updated over time, but this portfolio analysis is based on a data snapshot downloaded on Oct 15, 2025. The dashboard examples in this project focus on the **13 Oct 2023 – 5 Oct 2025** analysis window shown in the report filters.

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

- This chart shows a clear daily cycle in pedestrian movement. Activity stays very low overnight (roughly 0:00–6:00), then rises steadily through the morning. The strongest concentration sits in **late morning to early afternoon (around 10:00–14:00)**, with the **highest point around 12:00 (~5.8K)**, indicating the most consistent **high-demand period** for sidewalks, crosswalks, and station entrances.
- A second, smaller peak appears **late at night (around 22:00, ~3.4K)**, which suggests a distinct late-evening dispersal pattern rather than a typical commuter peak. This supports targeted night-time safety actions (lighting, clearer crossings, and crowd guidance) in busy precincts during late hours.

### 5) Pedestrian Intensity Heatmap by Hour & Day:

<img width="639" height="877" alt="image" src="https://github.com/user-attachments/assets/48824286-817c-469d-ba93-1c9d424c2224" />

- The strongest concentration appears on **Friday around midday (12:00)**, suggesting CBD activity is most intense during end-of-week work and retail periods.
- **Weekday lunchtime pressure** is also significant. **Monday (~14:00)** and **Tuesday (~13:00)** show clear spikes, pointing to a recurring **lunch and early-afternoon surge** likely driven by office, university, and retail movement. This supports targeted measures such as smoother crossing operations and footpath capacity checks during weekday lunchtime.
- **A clear late-night surge shows up on Friday**. The spike around **22:00 on Friday** points to **the night-time economy or event-related movement**, where safety and crowd flow need extra attention.
- **Weekends look flatter and more spread out**. Activity is present, but it is less “spiky,” which supports **lighter, targeted resourcing** rather than heavy weekday-style controls.
- **Implication**: Melbourne city planners can use **time-based interventions**. For example, strengthen crossing capacity and staffing around **Friday or the early-week lunchtime**, then shift to **lighting, surveillance, and night transport coordination** for **Friday late-night peaks**, instead of applying the same settings all week.

## Recommendations for City Planners:
- **Prioritise upgrades where people already concentrate**: Focus footpath capacity, crossing safety, lighting, and wayfinding in the **CBD core and Southbank** because these areas carry the highest day-to-day pedestrian load.
- **Tune crossings for weekday lunchtime surges**: Strengthen intersection operations and footpath pinch-point management around the recurring **weekday lunch and early afternoon peaks** (especially Mon and Tues). This is where small timing and layout changes can remove friction quickly.
- **Treat Friday late-night as a separate operating mode**: The **Friday ~22:00 spike** suggests night-time economy or event dispersal. Prioritise safer night crossings, clearer guidance to night transport, and targeted staff presence in busy precincts during these hours.
- **Use “inbound vs outbound” to target dispersal corridors**: Locations that skew outbound are likely carrying end-of-day movement. Improve corner capacity, crossing clearance time, and pedestrian waiting space at these corridors rather than applying the same treatments everywhere.
- **Plan works and maintenance around seasonal foot traffic**: Use the trend chart to schedule disruptive works (closures, resurfacing, utilities) in the lowest-footfall periods. And during peak periods, keep main walking routes open (or provide clear, well-lit, step-free detours) to avoid crowding, unsafe spillover into roads, and accessibility issues.

## Suggested Next Investigations (Future Work):

- **Explain peaks using external drivers**: Overlay pedestrian counts with **weather, public events, and planned disruptions** (street works, station closures, major detours) to separate true demand growth from temporary effects. This makes “why did it spike?” explanations more defensible when planners are justifying operational or capital decisions.
- **Measure “before vs after” impacts of upgrades**: Use the time series to compare footfall **before and after** changes at specific sites (new crossings, widened footpaths, signal timing updates, temporary closures). Pair this with the heatmap windows to check whether upgrades reduce pressure in the highest-demand periods, not just in averages.
- **Segment sensors by behaviour, not by a single label**: Use each sensor’s hour-by-day “time signature” to identify whether it is commuter-driven (AM/PM peaks), retail/lunch-driven (midday peak), or night-economy-driven (late-night uplift). Many CBD sensors will show mixed patterns, so a **primary + secondary pattern** (or simple score-based approach) is more realistic than assigning one category.
- **Add a lightweight forecasting layer for planning**: Extend the dashboard with simple **short-term forecasts** (next week or month) using recent patterns plus known drivers (school holidays, scheduled events). This helps planners staff resources, schedule maintenance, and test “what if” scenarios without needing a complex model.
