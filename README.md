# Australian Road Deaths: Who, Where and When

**Australia aims to halve road deaths by 2030, yet they are rising again. Who is dying, where and when, and where should road safety effort go first?**

A data visualisation project analysing every road death recorded in Australia from 1989 to 2025, combining an interactive **Power BI** report with **R** (ggplot2, ggridges, plotly) visualisations.

> Group project for STAT8124 *Advanced Methods in Data Visualisation*, Macquarie University (2026).

---

## Key findings

| Question | Finding |
|---|---|
| **A. Are deaths falling towards the 2030 target?** | Deaths fell from **2,800 (1989)** to **1,097 (2020)**, then rose every year to **1,309 (2025)**, 15% above the 2018–20 baseline and more than twice the 2030 target (< 571). Six of eight states are above their own baseline. |
| **B. Who is dying?** | Drivers are the largest group, but the recent rise is driven by **motorcyclists (+36%)**, **people aged 65–74 (+35%)**, **75+ (+32%)** and **pedestrians (+23%)** versus the 2018–20 average. Motorcyclists climbed from the 4th to the 2nd largest road-user group since 1989. |
| **C. Where?** | About **two in three deaths occur outside major cities**, concentrated on 100 km/h+ roads, while city deaths have risen faster since 2020 (+24% vs +6%). |
| **D. When?** | Deaths peak on **Friday afternoons**; weekend days average more deaths than weekdays (and more than the Christmas period). Each road user group has its own "danger hour", e.g. pedestrians around 6–7 pm. |
| **E. Priorities** | High-speed regional roads, motorcycle safety, older road users and pedestrians, and Friday afternoons and weekends. |

*All figures are counts of people killed, not rates; they are not adjusted for population or distance travelled.*

---

## Repository structure

```
├── ARDD_Fatalities_Cleaned_Jun2026.csv     Cleaned dataset used by both R and Power BI
├── Road_Deaths_Visualisation1.Rmd          R Markdown notebook: all R figures (A1–E1)
├── Road_Deaths_Visualisation1.nb.html      Rendered notebook, viewable in a browser, incl. interactive plotly charts
├── STAT8124 Road Deaths Story.pbix         Power BI report (5 pages)
└── STAT8124 Road Deaths Story.pdf          PDF export of the Power BI report
```

## Data

- **Source:** Bureau of Infrastructure and Transport Research Economics (BITRE), *Australian Road Deaths Database (ARDD)*, data current to June 2026.
- **Unit:** one row per person killed (58,837 records; 53,109 fatal crashes; January 1989 to June 2026).
- **Licence:** Creative Commons Attribution 3.0 Australia (CC BY 3.0 AU), © Commonwealth of Australia.
- **Original data:** [data.gov.au: Australian Road Deaths Database](https://data.gov.au/data/dataset/australian-road-deaths-database)

### Preparation
- Kept all records; one cleaned file is used by both R and Power BI.
- Recoded missing values (`-9`, `Unknown`, and an undocumented `99:99:99` time code).
- Stored Crash ID as text to preserve its 19-digit precision.
- Added crash hour, six age groups, five road-user groups and a city vs regional grouping.
- Flagged 2026 as a partial year.
- **Two time windows:** 1989–2025 for long-run trends; 2017–2025 for location and timing analysis, because location fields are about 99% complete only from 2017.

## Tools

- **R:** tidyverse (ggplot2, dplyr, readr), scales, ggridges, plotly, htmlwidgets, lubridate, zoo
- **Power BI:** five-page interactive report with shared slicers (year, state, road user, age, gender) and a decomposition tree

## How to reproduce

1. Clone or download this repository.
2. Open `Road_Deaths_Visualisation1.Rmd` in RStudio, with the CSV in the same folder, and run all chunks. Missing packages install automatically, and figures are saved to `STAT8124_R1_Figures/`.
3. Open `STAT8124 Road Deaths Story.pbix` in Power BI Desktop, or view the PDF export.

## Limitations

- The data record deaths only, with no population, traffic volume or distance travelled, so the analysis describes **where deaths occur, not relative risk**.
- No information on crash causes or trip purpose; interpretations are hypotheses, not causal claims.
- The Easter indicator exists only from 2006; heavy rigid truck involvement is 35% missing.

## Team

Group 7, STAT8124, Macquarie University.

## Licence

Code in this repository is released under the [MIT License](LICENSE). The underlying data remain © Commonwealth of Australia (BITRE) under CC BY 3.0 AU.
