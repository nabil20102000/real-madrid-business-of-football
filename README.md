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
| match_result | Win, draw or loss from Real Madrid's perspective | String |
| venue | Match venue, if available | String |
| match_status | Completed, postponed or other status | String |
| source | Original data provider | String |

### 4. League Performance Dataset

| Field | Description | Data Type |
|---|---|---|
| season | Football season | String |
| competition | League name | String |
| position | Final league position | Integer |
| matches_played | Total matches played | Integer |
| wins | Total wins | Integer |
| draws | Total draws | Integer |
| losses | Total losses | Integer |
| goals_for | Total goals scored | Integer |
| goals_against | Total goals conceded | Integer |
| goal_difference | Goals for minus goals against | Integer |
| points | Total league points | Integer |

### 5. Player Statistics Dataset

| Field | Description | Data Type |
|---|---|---|
| player_id | Unique player identifier | String |
| player_name | Player's full name | String |
| season | Football season | String |
| competition | Competition name | String |
| position | Player's playing position | String |
| appearances | Number of appearances | Integer |
| starts | Number of starting appearances | Integer |
| minutes_played | Total minutes played | Integer |
| goals | Goals scored | Integer |
| assists | Assists recorded | Integer |
| yellow_cards | Yellow cards received | Integer |
| red_cards | Red cards received | Integer |
| shots | Total shots, if available | Integer |
| shots_on_target | Shots on target, if available | Integer |
| source | Original data provider | String |

### 6. Transfer Dataset

| Field | Description | Data Type |
|---|---|---|
| transfer_id | Unique transfer identifier | String |
| player_id | Player identifier | String |
| player_name | Player's name | String |
| transfer_date | Date of transfer | Date |
| season | Relevant football season | String |
| transfer_type | Incoming, outgoing, loan or return | String |
| previous_club | Previous club | String |
| new_club | New club | String |
| transfer_fee | Reported transfer fee | Decimal |
| fee_currency | Currency of reported fee | String |
| fee_status | Confirmed, reported, undisclosed, free, loan or unknown | String |
| market_value | Estimated market value, if available | Decimal |
| source | Original data provider | String |

**Important:** Transfer fees, estimated market values, and accounting amortisation are separate financial concepts. They must not be treated as interchangeable.

### 7. Financial Dataset

| Field | Description | Data Type |
|---|---|---|
| financial_id | Unique financial record identifier | String |
| reporting_period | Financial reporting period | String |
| season | Related football season, where applicable | String |
| metric_name | Financial indicator name | String |
| metric_category | Revenue, expense, profit, debt or investment | String |
| amount | Reported financial amount | Decimal |
| currency | Original reporting currency | String |
| unit | EUR, EUR thousands or EUR millions | String |
| entity_scope | Football section, club total or consolidated group | String |
| source_document | Name of financial report | String |
| source_page | Page containing the reported figure | Integer |
| notes | Additional scope or methodology notes | String |

### 8. API Coverage Dataset

| Field | Description | Data Type |
|---|---|---|
| provider | API provider name | String |
| competition | Competition name | String |
| season | Requested season | String |
| endpoint | API endpoint tested | String |
| coverage_available | Whether the provider reports coverage | Boolean |
| records_returned | Number of records returned | Integer |
| audit_date | Date of coverage audit | Date |
| limitations | Missing data or known limitations | String |

### 9. Calculated KPIs

| KPI | Calculation |
|---|---|
| Revenue Growth (%) | ((Current Revenue - Previous Revenue) / Previous Revenue) × 100 |
| Net Profit Margin (%) | (Net Profit / Revenue) × 100 |
| Personnel Expense Ratio (%) | (Personnel Expenses / Revenue) × 100 |
| Transfer Net Spend | Transfer Spending - Transfer Income |
| Points Per Match | League Points / League Matches Played |
| Goals Per Match | Goals Scored / Matches Played |
| Goal Difference | Goals Scored - Goals Conceded |
| Goals Per 90 | (Player Goals / Minutes Played) × 90 |
| Assists Per 90 | (Player Assists / Minutes Played) × 90 |
| Goal Contributions Per 90 | ((Goals + Assists) / Minutes Played) × 90 |
| Shot Conversion (%) | (Goals / Total Shots) × 100 |

KPIs will only be calculated when the required source fields are available and validated. Cup competitions will not use league points-per-match calculations.

---

### 10. Data Quality and Validation Rules

1. Each match must have a unique identifier or a validated composite key.
2. Match dates must follow a consistent date format.
3. Scores must be numeric and non-negative.
4. Duplicate match records must be investigated.
5. Player statistics must be linked to the correct player, season and competition.
6. Transfer fees must retain their original currency and reporting status.
7. Financial records must retain their original reporting unit and entity scope.
8. Missing values must not automatically be replaced with zero.
9. API coverage indicators must not be interpreted as proof of complete data.
10. Every dataset must retain source and retrieval information.

### 11. Important Limitations

- Individual player salaries will not be invented or estimated from aggregate personnel expenses.
- Transfermarkt market values are estimates, not actual transfer fees.
- Financial reporting periods may not align exactly with football seasons.
- Historical player and match statistics may have incomplete coverage.
- Correlation between financial investment and sporting success does not establish causation.

### 12. Document Maintenance

This dictionary will be updated as new datasets, fields, sources and analytical requirements are introduced.

**Document status:** Initial version — subject to revision following data collection and validation.