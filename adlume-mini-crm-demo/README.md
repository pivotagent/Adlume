# Adlume — Mini CRM Performance Ads Analytics

Adlume is a clean, standalone demo project for small and medium businesses learning to analyse ads across Meta, Google and TikTok. The technical project is intentionally independent of any previous repository or pull request.

## Run the demo

1. Download or extract this folder.
2. Open `index.html` in a modern browser.
3. Use filters, inspect channel and campaign summaries, or import `demo/sample_ads_daily.csv`.
4. Export the filtered rows using **Xuất CSV**.

No package install, build step, API key, server, or network connection is required for this static demo. Imported data is stored only in memory for the current browser session. Refreshing the page resets to sample data.

## Current scope

- Responsive Vietnamese dashboard.
- Filters by platform, industry, objective and date range.
- Spend, impressions, clicks and recorded purchase revenue summary.
- Results are separated by objective; Mess, Lead, Purchase and Engagement are not added into a misleading universal conversion count.
- Platform spend shares, daily trend chart, campaign table, transparent rule-based insights, basic quality checks.
- CSV import and export.

## Synthetic data notice

The initial data is simulated for product demonstration. It is not connected to real advertising accounts. Revenue and Purchase results are illustrative. Do not use the values as campaign benchmarks or financial advice.

## CSV fields

Required: `date, platform, industry, objective, name, spend, results`.

Optional: `impressions, clicks, revenue`.

- `platform`: `Meta`, `Google` or `TikTok`.
- `objective`: `Mess`, `Lead`, `Purchase` or `Engagement`.
- `results` must mean the same type of outcome within each objective.
- `revenue` should only be supplied when it comes from a documented revenue source. Do not infer revenue from a purchase count.
- Blank optional values should be treated as unknown, not silently interpreted as factual zero.

## Analytics rules

- Cost per result: `SUM(spend) / SUM(results)` within the same result definition, objective, reporting period and attribution scope; do not average row-level CPL/CPA.
- CTR: `SUM(clicks) / SUM(impressions)`.
- CPC: `SUM(spend) / SUM(clicks)`.
- CPM: `SUM(spend) / SUM(impressions) * 1000`.
- Purchase ROAS: attributed purchase revenue divided by spend for that compatible scope. ROAS is not profit.
- Avoid direct cross-platform comparisons until timezone, currency, conversion definitions and attribution windows are reconciled.
- Preserve platform IDs as strings in any future canonical data model to avoid precision loss.

## Proposed architecture roadmap

1. Demo: static interface and CSV intake.
2. Data foundation: canonical schema, source lineage, validators, database and tenant/auth model.
3. Sheets sync: Google Sheets ingestion with sync logs and incremental import.
4. Platform connectors: Meta Ads first; Google Ads and TikTok Ads as separate adapters with explicit auth, permission and contract tests.
5. Analytics: funnel analysis, cohorts, creative analysis, anomalies and forecasts once quality/volume allow.
6. Commercial SaaS: tenant isolation, token encryption, access control, audit log, billing, limits and support.

## Strict Gate

- Inventory data sources before locking the schema.
- Contract/schema → fixtures → validator → tests → implementation.
- `No Evidence → No Verdict`: do not claim data access, live API sync, deployment, runtime validation or business outcomes without evidence.
- Merge does not equal validation. Release/runtime status requires test or runtime evidence.
- Do not expose secrets, customer datasets or access tokens in sample files.

## Proposed pricing hypothesis

- 99,000 VND/month
- 899,000 VND/year

These are proposed test prices, not validated market willingness-to-pay or a released paid service. Validate support load, infrastructure/API cost and usage limits before launch.
