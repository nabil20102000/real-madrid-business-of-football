# Real Madrid — Master Datasets (Updated 18 November 2026)

## Scope
- Baseline: 2015-16
- Main analysis period: 2016-17 to 2025-26
- Club focus: Real Madrid men's first team, unless a financial source is explicitly club-wide/consolidated.
- Opponents and counterparties are retained as context; match and transfer records are filtered to Real Madrid involvement.

## Core datasets
- `Real_Madrid_All_Matches.csv`: 630 Real Madrid match/event records, including 629 played matches and one cancelled 2015-16 Copa del Rey fixture.
- `Real_Madrid_Match_Team_Stats.csv`: 630 rows linked to the match master. It contains 616 dated Sports Reference team match-log rows plus 14 FIFA Club World Cup result rows without a corresponding Sports Reference team match-log record. Fields such as possession, attendance, captain, formations and referee remain blank when not supplied.
- `Real_Madrid_Player_Season_Stats.csv`: 386 season-level player aggregate records. The corrected 2022-23 all-competitions export is used.
- `Real_Madrid_Player_Competition_Stats.csv`: 345 competition-level aggregate records, currently Copa del Rey and FIFA Club World Cup 2022/2025.
- `Real_Madrid_Transfers.csv`: 214 Transfermarkt transaction rows (82 arrivals, 132 departures) from 2015-16 through 2025-26.
- `Real_Madrid_Player_ID_Crosswalk.csv`: 158 provisional name-derived player identities used to link season, competition and transfer records.
- `Real_Madrid_Financials.csv`: 204 extracted financial metric rows. Actuals, budgets, reporting scope and source references are retained.
- `Real_Madrid_Trophies.csv`: 22 derived trophy records; verify against official honours before publication.
- `Real_Madrid_La_Liga_Standings.csv`: 11 derived seasonal standings records.
- `Real_Madrid_Player_Match_Stats.csv`: header-only template. No individual player-by-match dataset was present in the supplied Sports Reference exports.

## Important distinction: team match logs vs player match stats
The Sports Reference `md` workbooks are Real Madrid team-level match logs. They provide one row per match with team context such as result, goals for/against, possession, attendance, captain, formations and referee. They are not player-by-player match performance tables. These team logs are included in `Real_Madrid_Match_Team_Stats.csv`. Do not treat them as individual player match stats.

## Transfer data notes
- All 214 supplied Transfermarkt rows are retained.
- Exact transfer dates are not present in the supplied season-level overview; `transfer_date` is blank rather than inferred.
- Numeric fees are preserved where reported. Loan fees are stored separately from permanent transfer fees.
- Missing/undisclosed fees are not converted to zero.
- Casemiro's 2015-16 loan return and permanent arrival are distinct events, not duplicates.
- Transfermarkt fee values are reported/estimated source values, not audited club cash-flow figures.

## Player identity notes
`player_id` values use the prefix `RMPLR-` and are generated from normalized player-name slugs. They are provisional cross-source keys, not official FBref or Transfermarkt IDs. Review aliases before production joins.

## Financial notes
- Annual financial reporting scope changes: supplied reports are standalone club basis through 2020-21 and consolidated group basis from 2021-22.
- 2025-26 budget and official results announcement are distinct data types and must not be combined as actual audited accounts.
- Full 2025-26 annual financial statements were not present in the supplied files at the time of this package.
- Sponsorship and merchandising are not separately quantified consistently across the entire period; use disclosed marketing revenue rather than inventing splits.

## Quality control
See `Dataset_Inventory.csv`, `Data_Quality_Log.csv` and `Source_Register.csv` for record counts, coverage, provenance and open issues. Original uploaded raw archives should remain unchanged in `Data/Raw/`; these are cleaned master outputs.

## Next phase
1. Validate provisional player ID aliases.
2. Verify transfer fee/date details where analysis requires transaction-level accuracy.
3. Collect individual player-by-match data only if match-level player performance analysis is in scope.
4. Verify trophy and standings derivations against official records.
5. Complete remaining source URL/licence documentation.
6. Load approved master tables into PostgreSQL.
