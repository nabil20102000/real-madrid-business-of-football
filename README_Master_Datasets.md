# Real Madrid — Master Datasets

**Updated:** 18 November 2026

## Project scope

- **Baseline season:** 2015/16.
- **Main analysis period:** 2016/17–2025/26.
- **Club focus:** Real Madrid men's first team for sporting, player and transfer data. Financial records may use the club or consolidated group reporting perimeter, as identified in the source material.
- Opponents and counterparties are retained as context. Match and transfer records relate to Real Madrid.

## Master CSV files

| File | Records | Contents |
|---|---:|---|
| `Real_Madrid_All_Matches.csv` | 630 | Real Madrid match/event records: 629 played matches and one cancelled 2015/16 Copa del Rey fixture. |
| `Real_Madrid_Match_Team_Stats.csv` | 630 | Team-level match-log information linked to the match master. Includes 616 Sports Reference match-log rows and 14 Club World Cup result-only rows without corresponding Sports Reference team match logs. |
| `Real_Madrid_Player_Season_Stats.csv` | 386 | Player season aggregates, including the corrected 2022/23 all-competitions export. |
| `Real_Madrid_Player_Competition_Stats.csv` | 345 | Player competition aggregates currently covering Copa del Rey and the 2022 and 2025 FIFA Club World Cups. |
| `Real_Madrid_Player_Match_Stats.csv` | 0 | Header-only template. No individual player-by-match dataset was present in the supplied Sports Reference `md` workbooks. |
| `Real_Madrid_Transfers.csv` | 214 | Transfermarkt transaction overview: 82 arrivals and 132 departures, covering 2015/16–2025/26. |
| `Real_Madrid_Player_ID_Crosswalk.csv` | 158 | Provisional name-based player keys linking names found across player and transfer datasets. |
| `Real_Madrid_Financials.csv` | 204 | Extracted financial metrics. Budgets, reported actuals and reporting scopes must remain distinguishable. |
| `Real_Madrid_Trophies.csv` | 22 | Derived trophy records; verify against official honours before publication. |
| `Real_Madrid_La_Liga_Standings.csv` | 11 | One Real Madrid league-standing record per season. |

Supporting documentation:

- `Dataset_Inventory.csv` — file-level coverage and record counts.
- `Data_Quality_Log.csv` — known issues, limitations and follow-up actions.
- `Source_Register.csv` — source inventory and provenance notes.
- `Data_Cleaning_Report.md` — summary of cleaning and preparation steps.

## Important interpretation notes

### Team match logs are not player match statistics

The Sports Reference `md` workbooks contain **team-level match logs**, with one row per match and fields such as result, goals for/against, possession, attendance, captain, formations and referee. They are not individual player-by-player match performance tables. These records are stored in `Real_Madrid_Match_Team_Stats.csv`.

`Real_Madrid_Player_Match_Stats.csv` remains empty by design until a genuine player-by-match source is available. No player-level match statistics have been inferred from team match logs.

### Transfer data

- All 214 rows from the supplied Transfermarkt overview are retained.
- Exact transfer dates were not supplied in that overview and are left blank rather than inferred.
- Reported numeric fees are retained where available. Loan fees are kept distinct from permanent transfer fees.
- Missing or undisclosed fees are not treated as zero.
- Casemiro's loan return and subsequent permanent transfer are separate transaction events.
- Transfermarkt fee values are source-reported figures, not audited club cash-flow amounts.

### Player identifiers

The `RMPLR-` identifiers are generated from normalized player names. They are **provisional cross-source keys**, not official FBref or Transfermarkt IDs. Name variants and aliases should be reviewed before production database joins.

### Financial data

- The supplied annual reporting basis changes from standalone club accounts through 2020/21 to consolidated group reporting from 2021/22. Use the reporting-scope field and document this break in longitudinal analysis.
- The 2025/26 budget and official results announcement are different data types; do not treat budget figures as actual results.
- The full 2025/26 annual financial statements were not present in the supplied file set at the time this package was prepared.
- Sponsorship and merchandising are not separately quantified consistently across the full period. Do not manufacture separate series where the source reports an aggregate marketing figure.

## Data handling

Original uploaded source files should remain unchanged in `Data/Raw/`. These master CSVs are prepared outputs for `Data/Cleaned/`. Review `Data_Quality_Log.csv` before analysis and do not silently fill missing values.

## Before production use

1. Review provisional player-name keys and aliases.
2. Verify transfer dates and fee details where transaction-level precision is required.
3. Collect individual player-by-match statistics if match-level player analysis is required.
4. Verify derived trophy and league-standing records against official records.
5. Complete any remaining source URL, retrieval-date and licence documentation.
6. Load approved tables into PostgreSQL only after the outstanding quality checks are accepted.
