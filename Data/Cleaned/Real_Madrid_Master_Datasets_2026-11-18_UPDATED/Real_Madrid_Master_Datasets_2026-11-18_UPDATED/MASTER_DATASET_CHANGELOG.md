# Master Dataset Changelog — 18 November 2026

1. Integrated the user-provided Transfermarkt export: 214 transaction rows across 2015-16 to 2025-26.
2. Parsed all 11 Sports Reference `md` match-log workbooks: 616 dated team-level match/event rows, excluding one blank separator row.
3. Linked all 616 team match-log rows to the canonical match IDs with zero unmapped records and no duplicate match IDs.
4. Created `Real_Madrid_Match_Team_Stats.csv` with 630 rows: 616 Sports Reference match logs plus 14 CWC result-only rows with `match_log_available=false`.
5. Enriched `Real_Madrid_All_Matches.csv` with match time, day, match report label, match-log notes and missing team match context fields.
6. Generated provisional name-based player IDs and a 158-row crosswalk across season, competition and transfer tables.
7. Updated source register, dataset inventory and data-quality log.
8. Kept `Real_Madrid_Player_Match_Stats.csv` header-only because supplied `md` files are team-level logs, not individual player-match performance exports. No player-level match statistics were fabricated.
9. Preserved transfer date blanks and fee-status distinctions; 91 of 214 records have no numeric fee.
