# Cricket Data Analytics — Project Plan

## Origin & Honesty Note
This project started as a follow-along of codebasics' "End to End Cricket
Data Analytics Project Using Web Scraping, Python, Pandas and Power BI"
tutorial. It has since been extended with additional scraped data, a SQL
layer, a prediction layer, and a live Streamlit app. The README will state
this origin clearly — the goal is to show genuine extension of a learning
resource, not to disguise it.

## Architecture

```
Scrape (Python) → Clean (Pandas) → Store (SQLite) → Analyze (SQL) →
Model (ML + SHAP) → Visualize (Power BI + Streamlit)
```

## Repo Structure

```
/data
  /raw            -> untouched scraped output (csv/json), versioned by scrape date
  /processed      -> cleaned data, ready for SQL load
/scraper
  scraper.py       -> core scraping logic, modular functions per data type
  utils.py         -> retry/logging helpers
/sql
  schema.sql        -> table definitions (matches, teams, players, ball_by_ball)
  load_data.py       -> loads /data/processed into SQLite
  queries.sql        -> analytical queries (documented, one per insight)
/models
  train.py            -> feature engineering + model training
  evaluate.py          -> metrics, confusion matrix, SHAP plots
  saved_model.pkl
/app
  streamlit_app.py     -> live dashboard + interactive prediction tool
/powerbi
  cricket_dashboard.pbix
  published_link.txt   -> Power BI "Publish to Web" link
/notebooks
  eda.ipynb             -> exploratory analysis, kept separate from production code
README.md
PLAN.md
requirements.txt
```

## Data Scope (expansion beyond tutorial)
- [ ] Decide seasons/tournaments to add (e.g., IPL 2022-2025, or IPL + WPL)
- [ ] Add ball-by-ball data (not just match summaries)
- [ ] Add player career stats / bios if available from source
- [ ] Add venue-level stats

## SQL Layer
- [ ] Normalize into tables: matches, teams, players, ball_by_ball
- [ ] Write 5+ analytical queries (documented with the business question each answers):
  - Top scorers by venue
  - Team win % by toss decision
  - Powerplay vs death-over performance by team
  - Player form trend (rolling average across matches)
  - Head-to-head team records
- [ ] Point Power BI at the SQL database (not raw CSVs)

## Prediction Layer
- [ ] Choose target: win probability (per match) — start here, simplest scope
- [ ] Features: team form (rolling win %), toss result, venue, head-to-head record
- [ ] Model: Logistic Regression baseline → XGBoost comparison
- [ ] Evaluation: train/test split, accuracy, confusion matrix, ROC-AUC
- [ ] Explainability: SHAP summary + force plots for sample predictions
- [ ] Stretch (only if time allows): player performance prediction (next-match runs)

## Streamlit App (live URL)
- [ ] Dashboard tab: key visuals from the SQL analytical queries
- [ ] Prediction tab: user selects two teams + venue + toss result → live win probability + SHAP explanation
- [ ] Insights tab: written summary of findings, in plain language
- [ ] Deploy on Streamlit Community Cloud, link in README

## Power BI
- [ ] Rebuild/extend the tutorial's dashboard with new data
- [ ] Publish to Web, link in README

## README Structure
1. Problem statement
2. Origin & honesty note
3. Live links (Streamlit + Power BI) — at the very top
4. Architecture diagram
5. What I added beyond the tutorial
6. Key findings (2-3 bullet insights)
7. How to run locally
8. Limitations & next steps

## Cursor AI Working Notes
- Build one module at a time, in the order listed under Repo Structure
- Ask Cursor to keep code simple — no over-engineered abstractions
- Review every generated file; be able to explain it in an interview
- Ask Cursor to add short "why" comments, not just "what" comments
- Commit per module, not one large dump commit
