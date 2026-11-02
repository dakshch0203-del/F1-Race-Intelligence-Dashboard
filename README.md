# F1-Race-Intelligence-Dashboard
my project link:https://public.tableau.com/app/profile/daksh.choudhary6980/viz/F1RaceIntelligenceDashboard_17936383525320/Story1?publish=yes
# FORMULA 1 Race Intelligence Dashboard Analysis Report (2010 – 2026)

## Project Overview
This repository contains the complete analytical workflow, relational data model, and visualization assets for the **Formula 1 Race Intelligence Dashboard Analysis (2010–2026)**. Built using **Tableau Public**, this project transforms 6,464 granular race records into an interactive multi-scenario decision-support tool. 

The analytical engine addresses real-world operational scenarios across three distinct domain perspectives:
- **Team Strategy (Scenario 1 - Mr. Arnold):** Constructor points trajectories & tyre compound performance by circuit type.
- **Media & Broadcast Analytics (Scenario 2 - Ms. Lisa):** Driver career points leaderboards & global Grand Prix geographic footprint.
- **Technical Regulation & Reliability (Scenario 3 - Mr. Gilchrist):** Constructor DNF breakdown and power-unit reliability metrics.

---

## Data Architecture & Model Design

The underlying dataset (`F1 Racing Project Dataset.xlsx`) consists of five normalized tables integrated into Tableau Public using explicit primary/foreign key relationships:

| Table Name | Records | Primary / Foreign Keys | Core Attributes |
| :--- | :--- | :--- | :--- |
| `race_results` | 6,464 | `Race Id`, `Circuit Id`, `Driver`, `Season` | Points, Finish Position, Dnf, Dnf Reason, Team |
| `circuits` | 382 | `Circuit Id` | Circuit Name, Country, Circuit Type, Length (Km) |
| `championship_standings` | 1,240 | `Season`, `Driver`, `Team` | Season Rank, Cumulative Points |
| `qualifying_results` | 6,464 | `Race Id`, `Driver` | Grid Position, Qualifying Time |
| `lap_intelligence` | 18,400+ | `Race Id`, `Driver` | Fastest Lap, Tyre Strategy, Pit Stops |

### Relationship Mapping:
- **`race_results` $\rightarrow$ `circuits`** via `Circuit Id` (Many-to-One)
- **`race_results` $\rightarrow$ `championship_standings`** via `Driver` + `Season` (Many-to-One)
- **`race_results` $\rightarrow$ `qualifying_results`** via `Race Id` + `Driver` (One-to-One)

---

## Key Business Insights & Analytical Findings

### 1. Scenario 1: Constructor Strategy & Tyre Optimization
* **Constructor Dominance:** Red Bull Racing and Mercedes exhibit high long-term points stability, whereas midfield teams show distinct performance spikes based on regulatory cycle updates.
* **Tyre Strategy Analysis:** Cross-tabulating starting tyre compounds against circuit classifications (Street, Permanent, Hybrid) demonstrates that **Medium compounds** deliver the highest average points yield across all circuit types, whereas Soft compounds degrade significantly faster on high-downforce street tracks.

### 2. Scenario 2: Broadcast Analytics & Global Footprint
* **Driver Performance:** Driver career leaderboards highlight peak point tallies dominated by multi-time World Drivers' Champions (Max Verstappen and Lewis Hamilton).
* **Geographic Distribution:** Interactive mapping reveals that Europe remains the operational epicenter with the highest density of hosted Grand Prix events, while emerging tracks in North America and the Middle East represent rapid calendar expansion post-2020.

### 3. Scenario 3: Technical Regulation & DNF Failures
* **Reliability Hazards:** Non-collision Did-Not-Finish (DNF) analysis indicates that **Power Unit (Engine)** and **Gearbox mechanical failures** account for over 58% of non-driver-error retirements.
* **Constructor Variability:** Midfield teams experience higher rates of hydraulic and electrical failures compared to top three constructors, reinforcing the need for standardized component regulation.

---

## Technical Features & Dashboard Capabilities

- **Interactive Cross-Filtering:** Selecting any constructor, driver, or country dynamically updates all connected worksheets across the $2 \times 2$ matrix layout.
- **Dynamic Aggregation:** Implemented `CNTD(Race Id)` distinct counting logic for accurate global country mapping.
- **Filtered Null Handling:** Filtered non-retirements out of the DNF matrix to isolate genuine mechanical failure categories.
- **Responsive Layout:** Formatted using an **Automatic Desktop Grid Canvas** ensuring seamless web presentation and screen adaptability.

---

## Project Repository Structure

```text
├── F1 Racing Project Dataset.xlsx     # Source database (5 normalized sheets)
├── README.md                          # Comprehensive project documentation
└── assets/
    ├── Dashboard_Overview.png         # Screenshot of 2x2 Interactive Dashboard
    └── Global_GP_Map.png              # Screenshot of Geographic Analysis
