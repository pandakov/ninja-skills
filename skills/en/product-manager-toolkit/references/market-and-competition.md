# Market and Competition Resources

Use for the `market` route. Access snapshot: 2026-09-17. See [verification details](access-verification.md) before promising availability. Conditional resources must work signed out in the current session or be skipped.

## Google Trends — search interest, conditional availability

- **Open:** [Explore](https://trends.google.com/trends/explore); [official usage guide](https://developers.google.com/search/docs/monitor-debug/trends-start).
- **Free scope:** public comparison of search interest, regions, and related queries. No account-based analytics or unofficial scraping API is included. The live check received HTTP 429, so query execution was not verified.
- **Professional use:** product manager [Przemysław Wilde describes using Trends in his work](https://przemyslaw.wilde.pl/en/blog/how-google-trends-works-and-how-to-read-it/). This is a firsthand account, not a prevalence survey.
- **Use:** compare the problem's language and existing alternatives in one chart; set the same geography, period, category, and search type. Distinguish a search term from a topic. Record the exact query URL and settings.
- **Return:** a trend/seasonality note and interview or positioning hypotheses. The index is normalized interest, not absolute searches, unique customers, revenue, or TAM. Low volume can hide demand; zero is not proof of absence.
- **Fallback:** use relevant public industry statistics and customer evidence. If unavailable, leave the trend question open; do not manufacture an equivalent search series.

## Google Ads Transparency Center — competitor messaging, conditional availability

- **Open:** [Advertiser search](https://adstransparency.google.com/?region=anywhere).
- **Free scope:** public advertiser/domain lookup and visible ad creatives. Excludes campaign creation, private performance data, and third-party paid ad databases. Search results were not completed in the browser check; verify the operation before use.
- **Professional grounding:** product marketing manager [Mia Taylor's practitioner guide](https://denote.net/blog/google-ads-transparency-center) describes competitive research with the center. It is vendor-authored guidance from an adjacent product-marketing role, not evidence of widespread PM adoption.
- **Use:** search a known competitor's name/domain; set region and date filters; capture visible promises, audiences, formats, and landing-page links. Verify features and prices on the competitor's own public site.
- **Return:** a dated messaging matrix and differentiated claims to test. An ad proves an observed message, not acquisition profitability, budget, conversion rate, or actual product capability.
- **Fallback:** compare official public pricing, documentation, changelogs, and landing pages. Record the missing advertising evidence. Do not click paid ads merely to navigate to a known company site.

## World Bank Open Data — supplemental authoritative data source

- **Open:** [Indicators](https://data.worldbank.org/); example [internet usage indicator](https://data.worldbank.org/indicator/IT.NET.USER.ZS); [documented API query structure](https://datahelpdesk.worldbank.org/knowledgebase/articles/898581).
- **Free scope:** public indicator pages and their available data downloads; the documented API is an optional route, not an installed integration. The indicator and metadata page was readable; a fresh API result/download was not verified in this review.
- **Evidence category:** institutional statistical source, **not a verified PM-used application**. Included separately to support defensible market inputs. Do not cite the institution's reputation as proof that its data matches the target segment.
- **Use:** select the indicator, countries, year, unit, and original data provider. Inspect missingness and definitions; preserve differing reference years rather than treating them as contemporaneous.
- **Return:** sourced inputs or upper-bound context for a market model. Population and internet penetration do not identify paying customers; use eligible buyer counts and a defensible price model for TAM/SAM/SOM.
- **Fallback:** the target country's official statistical releases or user-provided data with methodology. If equivalent evidence is unavailable, return the formula and data gap.

## A practical market-research pass

For an AI inbox assistant, identify known alternatives and read their public pricing and integration pages. Use Trends only to investigate relevant terminology and seasonality if accessible. Use Ads Transparency only for observed messaging. Use national or international statistics only when the metric actually bounds the target segment. Return a sourced alternatives table, remaining unknowns, and questions for real buyers. This recipe is a proposed workflow, not a claim that these sources establish demand.
