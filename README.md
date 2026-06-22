<h1 align="center">T20 Cricket Performance Analysis</h1>
<h3 align="center">An End-to-End Data Analytics Project — Web Scraping → Python → Power BI</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9+-blue.svg" alt="Python">
  <img src="https://img.shields.io/badge/Power%20BI-Dashboard-yellow.svg" alt="Power BI">
  <img src="https://img.shields.io/badge/Status-Complete-success.svg" alt="Status">
</p>

---

## Project Overview

Most cricket performance discussions are built on gut feeling — "he's in good form," "this player is clutch" — rather than numbers. This project pulls T20 International data from ESPN Cricinfo and builds an interactive dashboard to actually test those impressions against batting and bowling stats.

I built this by following codebasics' [End-to-End Cricket Data Analytics Project](https://www.youtube.com/watch?v=4QkYy1wANXA) tutorial, going through the full pipeline myself — scraping the data, cleaning it, building the data model, and designing the dashboard in Power BI.

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (Requests, BeautifulSoup) | Scraping player stats from ESPN Cricinfo |
| Pandas | Cleaning and structuring the scraped data |
| Power Query | Shaping data inside Power BI |
| Power BI + DAX | Building the data model and dashboard measures |
| Jupyter Notebook | EDA before moving into Power BI |

---

## How I Built It

```
Requirement Scoping
        ↓
Web Scraping (ESPN Cricinfo)
        ↓
Data Cleaning & Preprocessing (Pandas)
        ↓
Data Transformation (Power Query)
        ↓
Data Modeling & DAX Measures (Power BI)
        ↓
Interactive Dashboard
```

1. **Requirement Scoping** — Started by deciding what questions the dashboard should answer: who's actually consistent, and what separates the players who win matches from the ones who just look good on paper.
2. **Data Collection** — Scraped batting and bowling stats from ESPN Cricinfo using Python.
3. **Data Cleaning** — Cleaned up missing values and inconsistent formatting, then merged the batting and bowling tables in Pandas.
4. **Data Transformation** — Reshaped the tables in Power Query so they'd model correctly.
5. **Data Modeling** — Wrote DAX measures for strike rate trends, averages, and consistency, and set up the relationships between tables.
6. **Dashboard Building** — Put it all together in Power BI with slicers for team, player, and tournament stage.

---

## What the Dashboard Tracks

- Batting average, strike rate, and boundary %
- Bowling average, economy, bowling strike rate, dot-ball %, maidens
- Players grouped into 5 roles: Power Hitters/Openers, Anchors/Middle Order, Finishers/Lower Order, All-Rounders/Lower Middle Order, Specialist Fast Bowlers/Tail End
- Innings-by-innings trends for batting average and strike rate
- Combined stats when multiple players are selected together
- A "Final 11" team builder that aggregates team-level stats as you pick players

---

## Dashboard Walkthrough

**Power Hitters / Openers**
Compares top power-hitters with trend lines across innings and a Batting Avg vs Strike Rate bubble chart.

![Power Hitters Overview](https://github.com/user-attachments/assets/6434993e-b6be-4c38-a30c-d10bf5f5345f)

**Individual Player Drill-Down**
Click a player's name and it pulls up a breakdown of their performance against each opposition team.

![Player Drill-Down Card](https://github.com/user-attachments/assets/98744977-6dec-4952-95bf-5083b5bb2d97)

**Combined Performance View**
Select two or more players and the dashboard recalculates their combined stats — handy for checking how well a potential opening pair might work together.

![Combined Performance](https://github.com/user-attachments/assets/c4a32d7b-5b34-4487-998e-5c03e6b1a3dd)

**Anchors / Middle Order**
Same setup applied to middle-order batters, where the trade-off between consistency and aggression matters more.

![Anchors Middle Order](https://github.com/user-attachments/assets/aa1d8691-89ba-4eb2-84dd-6c9b77d59fde)

**Finishers / Lower Order**
Looks at both batting and bowling strike rates for finishers, since a lot of these players also bowl.

![Finishers Lower Order](https://github.com/user-attachments/assets/ce182be9-c780-4632-adc6-5f24deb9267f)

**All-Rounders / Lower Middle Order**
Combines batting numbers with bowling economy and strike rate, plotted to find the most efficient all-rounders.

![All Rounders](https://github.com/user-attachments/assets/358b5d5a-43b4-46a2-9071-c4feefb54c58)

**Specialist Fast Bowlers / Tail End**
Pure bowling view — economy, average, strike rate, dot-ball % — for frontline pace bowlers.

![Specialist Fast Bowlers](https://github.com/user-attachments/assets/d5351881-926e-43c5-a541-65831b377321)

**Final 11 — Team Builder**
A searchable list where you can build your own XI. As you add players, it recalculates team-level batting average, strike rate, bowling average, economy, and dot-ball %.

![Final 11 Team Builder](https://github.com/user-attachments/assets/bb915291-7f7f-4eff-9fe8-080844cee567)

---

## What I Found

- Suryakumar Yadav had the highest strike rate among Anchors/Middle Order batters at 189.68 — well ahead of the next best, Glenn Phillips at 158.27. He's technically an anchor by role, but scores like a finisher.
- Virat Kohli's batting average of 98.67 was nearly double the next-highest anchor (Daryl Mitchell, 54.50) — a big gap that says a lot about how consistent he was through the tournament.
- Among Power Hitters, Quinton de Kock had the best boundary percentage (75.81%) even though his strike rate was lower than Rilee Rossouw's — his scoring leaned more on boundaries than running between the wickets.
- Among Finishers, Curtis Campher had the best strike rate (163.64) but the lowest average (12.83), while Sikandar Raza struck a better balance — 147.97 strike rate with a more sustainable 18.50 average. Classic trade-off between explosiveness and reliability.
- Among All-Rounders, Rashid Khan had the best bowling strike rate (18.00) along with a strong batting strike rate (178.13) — genuinely impactful with both bat and ball. Shadab Khan had the best economy (6.35) and the most wickets (11) in the group.
- Among Specialist Fast Bowlers, Anrich Nortje's economy (5.37) and bowling average (8.55) were clearly the best in the group, while Sam Curran took the most wickets (13) despite a slightly higher economy — two different ways of being effective with the ball.
- I built a sample Final 11 with Jos Buttler, Rilee Rossouw, Virat Kohli, Suryakumar Yadav, and Glenn Phillips, and the dashboard projected a team batting average of 39.60, strike rate of 154.54, and bowling economy of 6.47 — a quick way to sanity-check a lineup before committing to it.

---

## Project Structure

```
T20-Cricket-Performance-Analysis/
├── data/                  # Raw and cleaned datasets
├── notebooks/             # Jupyter notebooks for EDA
├── scripts/               # Web scraping scripts
├── dashboard/             # Power BI .pbix file
└── README.md
```

---

## Running It Yourself

1. Clone the repository
   ```bash
   git clone <your-repo-url>
   ```
2. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```
3. (Optional) Re-run the scraper to pull fresh data — cleaned data is already included if you just want to explore
   ```bash
   python scripts/scrape_data.py
   ```
4. Open `dashboard/cricket_analysis.pbix` in Power BI Desktop

---

## Where I'd Take This Next

This dashboard is descriptive — it tells you what happened. The next step is making it predictive and more interactive:

- **Win probability predictor** — A Logistic Regression or XGBoost model using live match state (score, wickets, overs left) to estimate win probability as a game unfolds.
- **Player clustering** — K-Means on batting/bowling stats to see if natural player "types" emerge on their own, rather than relying on the manual role categories I used here.
- **Optimal squad selector** — Use `scipy.optimize` or `PuLP` to recommend a best XI under constraints like budget or role balance, instead of picking manually in the Final 11 view.
- **A web version** — Rebuild the key views in Streamlit so it's shareable as a link instead of needing Power BI Desktop to open.
- **Sharper framing** — Tie each view to a specific question (e.g. "Which players keep a 150+ strike rate against every opposition?") instead of just presenting the numbers.

---

## A Note on How This Was Built

This project follows codebasics' tutorial, *["End To End Cricket Data Analytics Project Using Web Scraping, Python, Pandas and Power BI"](https://www.youtube.com/watch?v=4QkYy1wANXA)*. I used it to learn the full pipeline hands-on — scraping, cleaning, modeling, and dashboarding — and I'm sharing it here as part of my portfolio along with the insights I pulled out of it.

---

## Contact

**Adarsh Gupta**
[LinkedIn](https://www.linkedin.com/in/adarsh-gupta-28163b229) · [adarshguptaaaa@gmail.com](mailto:adarshguptaaaa@gmail.com)







