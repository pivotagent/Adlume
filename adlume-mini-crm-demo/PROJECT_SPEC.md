# Adlume — Project Spec v0.1

## Product goal
Help SME operators with little analytics experience understand paid-ad costs, traffic, objective-specific results and the next checks to make — without pretending different objectives are interchangeable.

## Initial users
- Education providers: Messenger conversations and lead acquisition.
- E-commerce sellers: purchase volume and documented revenue.
- Beginners who need plain-language explanations and safe data import.

## Canonical domains (proposal)
- `CRM-MAP-001` — CRM Master Map
- `DATA-001` — Source Inventory & Data Intake
- `DATA-002` — Canonical Ads Schema & Lineage
- `RPT-001` — Executive Dashboard
- `ANL-001` — Campaign / Channel Analytics
- `ANL-002` — Objective-specific KPI Calculator
- `DQ-001` — Data Quality Validation
- `INS-001` — Evidence-based Action Suggestions
- `CONN-001` — Platform Connector Contract
- `SEC-001` — Auth, Secrets & Tenant Isolation
- `BILL-001` — Subscription & Usage Limits

## Metric definitions
- Cost per result = total spend / total results for a consistent result definition and scope.
- CTR = total clicks / total impressions.
- CPC = total spend / total clicks.
- CPM = total spend / total impressions * 1000.
- Purchase ROAS = attributed revenue / spend only when revenue and attribution source are known.
- A missing value is unknown unless the source contract states otherwise.

## Non-goals for the first demo
- No live API sync or claim of platform authorisation.
- No persistent server storage, login, multi-tenant security, subscription billing, or production deployment.
- No automated bid/budget changes.
- No ML predictions until enough reliable, labelled historical data is available.

## Release gate
A release cannot be called validated until files, code paths, tests and runtime behaviour have actual supporting evidence. Repository commits alone are not runtime validation.
