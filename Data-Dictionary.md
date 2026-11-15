# Data Dictionary
## Real Madrid: The Business of Football

### 1. Project Overview

This document defines the datasets, fields, data types, and business meanings used in the Real Madrid Football Analytics project.

**Project period:**
- Baseline season: 2015–16
- Main analysis period: 2016–17 to 2025–26

**Scope:** Real Madrid men's first team, including sporting performance, financial performance, player statistics, transfers, and investment analysis.

The dictionary will be updated as datasets are collected, validated, and integrated.

---

### 2. Dataset Categories

| Dataset | Description | Primary Source |
|---|---|---|
| Match Results | Match dates, opponents, scores and results | OpenFootball |
| League Performance | League position, points, wins, draws and losses | OpenFootball / football-data.org |
| Player Statistics | Appearances, minutes, goals and assists | API-Football / FBref |
| Team Statistics | Goals, shots, possession and other team metrics | API-Football |
| Transfer Records | Player transfers, fees and transfer dates | Transfermarkt (manual verification) |
| Financial Records | Revenue, expenses, profit and financial indicators | Real Madrid official financial reports |
| Competition Records | Competition participation and trophies | Official competition sources |
| API Coverage | Availability, completeness and freshness of API data | API-Football |

---

### 3. Match Results Dataset

| Field | Description | Data Type |
|---|---|---|
| match_id | Unique match identifier | String |
| season | Football season, e.g. 2024–25 | String |
| competition | Competition name | String |
| match_date | Date of the match | Date |
| home_team | Home team name | String |
| away_team | Away team name | String |
| home_goals | Goals scored by home team | Integer |
| away_goals | Goals scored by away team | Integer |
| match_result | Win, draw or loss from Real Madrid's perspective |