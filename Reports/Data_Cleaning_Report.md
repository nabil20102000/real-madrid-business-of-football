# Data Cleaning and Preparation Report

**Project:** Real Madrid — The Business of Football  
**Prepared:** 18 November 2026  
**Purpose:** Brief record of the cleaning and preparation applied to the supplied source files before creating the master CSV datasets.

## 1. Work completed

- Combined the supplied Real Madrid match-result records into `Real_Madrid_All_Matches.csv`, retaining the 2015/16 baseline and the 2016/17–2025/26 main period.
- Integrated the 14 FIFA Club World Cup match records from the 2016, 2017, 2018, 2022 and 2025 editions into the match master.
- Parsed the 11 Sports Reference `md` workbooks. One blank separator row was excluded, leaving 616 dated team match-log records.
- Matched the 616 team match-log records to the canonical match IDs using season, date, competition and opponent checks. The resulting match-team table has 630 rows: 616 with Sports Reference team match-log data and 14 Club World Cup result-only rows without a corresponding Sports Reference team log.
- Repaired the extra quotation layer in the supplied Spanish Super Cup and UEFA Super Cup CSV exports so their fields could be read as separate columns.
- Replaced the incorrect 2022/23 two-match player-statistics extract with the separately supplied corrected all-competitions 2022/23 player export.
- Integrated the supplied Transfermarkt overview into a 214-row transfer table: 82 arrivals and 132 departures.
- Created provisional name-based player keys and a crosswalk to support future joins between season, competition and transfer records.
- Consolidated the supplied financial metrics into the existing financial master while retaining budget and reported-actual distinctions and noting changes in reporting scope.

## 2. Standardization applied

- Standardized competition labels across the match data.
- Normalized text values and common encoding/mojibake issues in names and labels.
- Standardized season labels and match dates for matching and joining.
- Linked team match-log information to the match master through match IDs.
- Preserved source-file and source-row references where available.
- Kept missing values blank when the source did not provide a value; missing transfer fees and dates were not converted into zero or estimated.
- Kept the cancelled 2015/16 Cádiz Copa del Rey fixture as a cancelled event, not a played match.

## 3. Master dataset outputs

| Dataset | Rows | Preparation status |
|---|---:|---|
| All Matches | 630 | Consolidated; includes 629 played matches and one cancelled event |
| Match Team Stats | 630 | 616 team match logs plus 14 result-only Club World Cup rows |
| Player Season Stats | 386 | Consolidated; corrected 2022/23 source used |
| Player Competition Stats | 345 | Consolidated available Copa del Rey and CWC aggregates |
| Transfers | 214 | Transfermarkt overview integrated |
| Player ID Crosswalk | 158 | Provisional name-based keys |
| Financials | 204 | Extracted financial metric rows |
| Trophies | 22 | Derived records; official verification remains open |
| La Liga Standings | 11 | Derived seasonal records |

## 4. Known limitations — not silently corrected

- **Player-match statistics:** The supplied Sports Reference `md` workbooks are team-level match logs, not individual player-match performance data. The player-match master remains a header-only template.
- **Transfer dates:** Exact dates are absent from the supplied Transfermarkt season overview and remain blank.
- **Transfer fees:** 91 of 214 transfer rows have no numeric fee in the supplied source. Fee status is retained; missing fees are not assumed to be zero.
- **Player IDs:** Generated IDs are provisional name-based keys, not official source IDs. Alias review is required before production joins.
- **Club World Cup team detail:** The 14 Club World Cup matches are in the match master, but no corresponding Sports Reference team match-log rows were present in the supplied workbooks.
- **Financial comparability:** Reporting scope changes from standalone club accounts through 2020/21 to consolidated group reporting from 2021/22. The 2025/26 budget and results announcement are not audited annual accounts.
- **Cup match detail:** Some Copa del Rey records lack separate regulation-time scores where extra time was played. The final score is retained; do not infer the 90-minute score.
- **Derived records:** Trophy and La Liga standing records should be checked against official records before publication.

## 5. Overall assessment

The supplied files have been consolidated and standardized into Real Madrid-focused master tables, with source limitations and unresolved issues documented. This is a **first-pass cleaned analytical dataset**, not a claim that every field is complete or every derived record has received final independent verification.

The next quality-control step is to review the open items in `Data_Quality_Log.csv` before using the tables for final statistical analysis, PostgreSQL loading or Power BI reporting.
