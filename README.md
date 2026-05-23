# Public Sector

Industry-vertical index for the **public-sector / government API landscape** across U.S. federal, state, and local levels. Catalogs the federal API gateway, the open-data catalog, the regulatory and procurement surfaces, the headline agency APIs, the state-and-local platform vendors, and the civic-tech layer — and pins them all to a shared agency / dataset / regulation data model so consumers can normalize across publishers.

> The data-schema shape of a *government agency*, *government dataset*, and *government regulation* — wired together with a JSON-LD context that bridges DCAT-US, schema.org, and the Open Civic Data identifiers.

## Cross-Reference

This umbrella topic repo binds together the **211 U.S. federal agencies** profiled in Kin Lane's 2026-05-05 [roundup of US federal agencies and their APIs](https://apievangelist.com/2026/05/05/a-roundup-of-us-federal-agencies-and-their-apis/) — each of which has its own `api-evangelist/<agency-slug>` repo with `apis.yml`, vocabulary, and where applicable OpenAPI specs.

## What's in This Repo

| Artifact | File | Purpose |
|---|---|---|
| APIs Index | [apis.yml](./apis.yml) | Catalogs the 21 anchor surfaces in the public-sector landscape (federal gateway, federal catalogs, headline agency APIs, state/local platforms, civic-tech layer). |
| Agency Schema | [json-schema/public-sector-agency-schema.json](./json-schema/public-sector-agency-schema.json) | JSON Schema for a government agency record, aligned with schema.org/GovernmentOrganization and Open Civic Data jurisdictions. |
| Dataset Schema | [json-schema/public-sector-dataset-schema.json](./json-schema/public-sector-dataset-schema.json) | JSON Schema for a government dataset, aligned with DCAT-US 1.1 and round-trippable with CKAN `package_show`. |
| Regulation Schema | [json-schema/public-sector-regulation-schema.json](./json-schema/public-sector-regulation-schema.json) | JSON Schema for a Federal Register / Regulations.gov document. |
| Agency Structure | [json-structure/public-sector-agency-structure.json](./json-structure/public-sector-agency-structure.json) | Flattened structural view of the agency record. |
| Dataset Structure | [json-structure/public-sector-dataset-structure.json](./json-structure/public-sector-dataset-structure.json) | Flattened structural view of the dataset record. |
| Regulation Structure | [json-structure/public-sector-regulation-structure.json](./json-structure/public-sector-regulation-structure.json) | Flattened structural view of the regulation record. |
| JSON-LD Context | [json-ld/public-sector-context.jsonld](./json-ld/public-sector-context.jsonld) | Semantic context binding the three core types to schema.org, DCAT, DCT, and Open Civic Data. |
| Vocabulary | [vocabulary/public-sector-vocabulary.yml](./vocabulary/public-sector-vocabulary.yml) | Controlled vocabulary for entities, identifiers, protocols, formats, government levels, branches, governance statutes, vendors, civic-tech projects, personas, and workflows. |
| Agency Example | [examples/public-sector-agency-example.json](./examples/public-sector-agency-example.json) | GSA as a worked example. |
| Dataset Example | [examples/public-sector-dataset-example.json](./examples/public-sector-dataset-example.json) | CFPB Consumer Complaint Database as a worked example. |
| Regulation Example | [examples/public-sector-regulation-example.json](./examples/public-sector-regulation-example.json) | An EPA oil-and-gas NSPS proposed rule as a worked example. |

## The Landscape

### Federal Gateway and Catalogs

- **[api.data.gov](https://api.data.gov)** — GSA Technology Transformation Services. Free API management gateway used by ~25 agencies for 450+ APIs.
- **[data.gov](https://www.data.gov)** / **[catalog.data.gov](https://catalog.data.gov)** — CKAN-powered federal open data catalog. Action API at `/api/3/action/` for `package_search`, `package_show`, `organization_list`.
- **[GovInfo](https://www.govinfo.gov)** — GPO authoritative publishing: bills, Federal Register, CFR, Public Laws, U.S. Courts opinions.

### Federal Regulatory and Legislative

- **[Regulations.gov v4](https://www.regulations.gov)** — Dockets, documents, comments. `X-Api-Key` header; commenting capped at 50/min and 500/hr.
- **[Federal Register API](https://www.federalregister.gov/developers/api/v1)** — Daily Federal Register publication. No key required for read.
- **[Congress.gov API](https://api.congress.gov)** — Library of Congress legislative data: bills, members, committees, congressional record.

### Federal Procurement and Spending

- **[SAM.gov](https://sam.gov)** — 11 production APIs (Entity Management, Exclusions, Federal Hierarchy, Contract Opportunities, Awards, Assistance Listings, Subaward Reporting).
- **[USAspending.gov](https://www.usaspending.gov)** — Treasury's DATA Act spending feed (contracts, grants, loans, direct payments).
- **[Treasury Fiscal Data](https://fiscaldata.treasury.gov)** — Debt to the Penny, Monthly Treasury Statement, exchange rates.

### Federal Statistics and Science

- **[Census Data API](https://api.census.gov/data)** — ~1,784 datasets across Decennial, ACS, PEP, CPS, SIPP, CBP, Economic Census.
- **[Bureau of Economic Analysis](https://www.bea.gov/tools/)** — GDP, income, trade, regional and industry accounts.
- **[api.weather.gov](https://api.weather.gov)** — NOAA NWS forecasts / alerts. User-Agent only; "All of the information presented via the API is intended to be open data."
- **[api.nasa.gov](https://api.nasa.gov)** — APOD, NeoWs, DONKI, Earth, EONET, EPIC, Insight, Mars Rover, Exoplanet, Open Science Data Repository.
- **[FEC openFEC](https://api.open.fec.gov)** — Candidates, committees, filings, contributions, disbursements.

### State and Local Platforms

- **[Socrata Open Data API (Tyler Data and Insights)](https://dev.socrata.com)** — JSON + SoQL; powers federal (data.cdc.gov, healthdata.gov), state, county, and city open data portals worldwide.
- **[Tyler Technologies](https://www.tylertech.com)** — Largest SLG vendor. Courts & Justice, ERP, Public Safety, Civic Services, Property & Assessment, K-12, Recreation, Data & Insights.
- **[OpenGov](https://www.opengov.com)** — ERP / budgeting / financial reporting / permitting / licensing / procurement cloud for SLG.

### Civic-Tech Layer

- **[OpenStates / Plural Policy](https://openstates.org)** — REST v3 at `v3.openstates.org`. State bills, legislators, jurisdictions, committees, events across all 50 states.
- **[GovTrack](https://www.govtrack.us)** — Long-running Congress tracker; bulk data downloads at `govtrack.us/data` widely reused.
- **[Open Civic Data](https://opencivicdata.readthedocs.io)** — OCD-IDs for political geographies plus normalized civic-object models. Underlies OpenStates' scrapers and Google's Civic Information API.

## The Data Model

Three entities, three schemas, one shared JSON-LD context:

```
PublicSectorAgency        ⊆  schema:GovernmentOrganization
PublicSectorDataset       ⊆  dcat:Dataset                  (DCAT-US 1.1)
PublicSectorRegulation    ⊆  schema:Legislation
```

Identifiers favor stable, externally maintained URIs:

- **[Open Civic Data Division Identifiers](https://github.com/opencivicdata/ocd-division-ids)** for jurisdictions (`ocd-division/country:us/state:ca/place:los_angeles`)
- **Regulations.gov Docket IDs** for dockets (`EPA-HQ-OAR-2024-0001`)
- **Federal Register Document Numbers** + citations (`2026-05022` / `91 FR 21789`)
- **OMB Bureau / Program Codes** from Project Open Data
- **SAM.gov UEI** for federal-eligible entities

## Governance Backbone

This index is shaped by the statutes that compel U.S. agencies to publish APIs and data:

- **Open Government Data Act of 2018** — Title II of the Evidence Act; requires federal agencies to publish information as open data.
- **DATA Act of 2014** — Standardized federal spending reporting (USAspending.gov).
- **Foundations for Evidence-Based Policymaking Act of 2018** — Chief Data Officers; `/data.json` catalogs.
- **Administrative Procedure Act** — Notice-and-comment rulemaking on Regulations.gov.
- **FOIA** — Per-agency eFOIA portals.

## Out of Scope (Captured Elsewhere)

- Per-agency profiles live in their own repos under [github.com/api-evangelist](https://github.com/api-evangelist) — see the [2026-05-05 federal agencies roundup](https://apievangelist.com/2026/05/05/a-roundup-of-us-federal-agencies-and-their-apis/) for the full 211-agency index.
- Per-vendor OpenAPI specs for Tyler / Socrata / OpenGov live in the vendor repos, not this topic repo.
- Pricing, rate-limits, and FinOps artifacts are skipped — the public-sector topic is not a single commercial provider.

## License

Public domain (US Government default for federal data; this index itself is published as open content).
