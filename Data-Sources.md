# DATA SOURCES AND COVERAGE

This document records the external sources considered for the Real Madrid business and sporting performance project.

| Source | Intended Use | Initial Assessment |
|---|---|---|
| OpenFootball | Historical La Liga fixtures and results | Primary historical results source |
| Real Madrid official website | Annual accounts and financial reports | Primary financial source |
| API-Football | Fixtures, events, lineups and player statistics | Coverage requires API audit |
| football-data.org | Fixture and results cross-check | Secondary verification source |
| FBref | Player and team statistical cross-checks | Manual use subject to data-use policy |
| StatsBomb Open Data | Event-level tactical analysis | Selected competition coverage only |
| Transfermarkt | Transfer history and market-value cross-checks | Manual use only; automated scraping excluded |

## Source Links

- OpenFootball: https://github.com/openfootball/espana
- Real Madrid financial archive: https://www.realmadrid.com/en-US/about-real-madrid/the-club/transparency/management-reports-financial-statements-archive
- API-Football documentation: https://www.api-football.com/documentation-v3
- API-Football coverage: https://www.api-football.com/coverage/
- football-data.org: https://www.football-data.org/
- FBref: https://fbref.com/
- StatsBomb Open Data: https://github.com/hudl/open-data
- Transfermarkt: https://www.transfermarkt.com/

## Data Collection Principles

1. Record the source and retrieval date for every dataset.
2. Preserve original files before transformation.
3. Validate match counts, dates, duplicate records and missing values.
4. Distinguish reported values from estimates.
5. Respect licensing, terms of use and API restrictions.
6. Document incomplete coverage and unresolved discrepancies.

**Important:** Inclusion in this register does not mean that a source has been fully audited or that all requested seasons and statistical fields are available.