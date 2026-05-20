# PinkTaxWatch

**An independent public-interest data observatory tracking menstrual product affordability across nine European markets.**

PinkTaxWatch combines verified retail price observations, VAT rates, and wage-normalized affordability metrics into a comparable index across Germany, Austria, Hungary, Czechia, the United Kingdom, Ireland, Denmark, the Netherlands, and Belgium. The project is independent, non-commercial, and built around a deliberate methodological choice: human-observed retail prices over automated scraping, and verified policy data over aggregated estimates.

A complementary activism layer surfaces active petitions and policy contacts in each covered market. This is a deliberate hybrid — observatory and action hub — with the observatory's data claims kept strictly to what can be sourced and verified.

> **Status:** Live. Content rewrites, UX iterations, and dataset expansions ongoing.

---

## Table of contents

- [What this is](#what-this-is)
- [Markets covered](#markets-covered)
- [Methodology](#methodology)
- [Data sources](#data-sources)
- [Site structure](#site-structure)
- [Tech stack](#tech-stack)
- [Local development](#local-development)
- [Data governance and versioning](#data-governance-and-versioning)
- [Contributing](#contributing)

---

## What this is

The "pink ta (https://www.pinktaxwatch.com/) x" — the structural premium paid by women on essential products and services — is widely discussed but rarely quantified consistently across borders. Existing comparisons tend to be either national and anecdotal, or aggregated to a degree that loses the methodology trail.

PinkTaxWatch addresses this gap by maintaining a verified, transparent dataset of:

- **Retail prices** for menstrual products, hand-recorded from named retailers with dated observations
- **Applicable VAT rates** for menstrual products, sourced from primary national tax authority documentation
- **Net wage normalization** using Eurostat's `earn_nt_net` Family Case A1 (single, no children, 100% of national average wage)
- **A verified policy timeline** of menstrual-product VAT reductions and removals across global jurisdictions

The combined output is an affordability index comparing menstrual product cost as a share of net income across the covered markets, with the underlying methodology fully disclosed.

The project serves three audiences:

1. **Readers and the general public** — accessible affordability comparisons and policy context
2. **Journalists and researchers** — citable, source-tagged data with methodology transparency
3. **Advocates and policymakers** — a structured reference point for cross-market comparison

---

## Markets covered

Nine European markets are currently in scope:

- Germany (DE)
- Austria (AT)
- Hungary (HU)
- Czechia (CZ)
- United Kingdom (UK)
- Ireland (IE)
- Denmark (DK)
- Netherlands (NL)
- Belgium (BE)

Scope expansion is deliberate and methodology-led. Additional markets and a perimenopause/postmenopause cost extension are flagged as future scope.

---

## Methodology

A condensed summary is below. The full methodology, including decision rationale and versioning history, is published at [`/methodology`](#) on the live site and tracked in this repository as `METHODOLOGY_v1.0.0.md`.

**Price observations**

- Hand-recorded from named retailers (e.g. DM, Rossmann, Tesco) with observation dates
- Substitution SKUs and temporary sale prices are flagged by the human observer — a methodological advantage over automated scraping
- Retailer inventory and refresh cadence are documented per source

**VAT verification**

- Per-country, sourced from primary national tax authority documentation
- Verification dates recorded; updates triggered by published rate changes

**Wage normalization**

- Eurostat `earn_nt_net` Family Case A1 (single, no children, 100% of national average wage)
- FX conversion via European Central Bank reference rates

**What this project does not claim**

- This is not a meta-analysis, systematic review, or epidemiological study. Methodology badges suggesting otherwise are explicitly not used.
- Headline disparities and rankings are reported only where the underlying observations and verification dates support them.

---

## Data sources

The data layer is intentionally simple at this scale: a Google Sheets workbook published as CSV and fetched by the frontend. Snowflake, Databricks, and automated scraping were evaluated and rejected — the first two for being disproportionate to the data volume, and the third for legal exposure and methodological disadvantage (loss of human-flagged substitution and sale-price context).

Each source entry in the workbook records:

- Source name (retailer or authority)
- Observation or verification date
- Refresh cadence
- Storage location
- Known risk flags

A complete source inventory is published on the [`/methodology`](#) page.

---

## Site structure

The site is organized into the following primary surfaces:

**Sections (W1–W8)** — A curated sequence of editorial sections covering project framing, the interactive market map, key affordability facts, the policy simulator (per-country VAT scenarios), the verified policy timeline (W5: "Policy chamber"), cross-market comparison cards, dispatch entry, and sources and transparency disclosure.

**Dispatches** (`/dispatches`) — Editorial pieces examining specific aspects of menstrual product affordability and policy. Individual dispatch routes are linked from the hub.

**Policy archive** (`/policy`) — Verified policy entries documenting menstrual-product VAT reductions and removals across global jurisdictions, with primary-source citations.

**Methodology** (`/methodology`) — Full methodology disclosure, including data sources, decision log, and versioning history.

**Site index** (`/site-index`) — A structured, scannable index of all published content. Intended for transparency, QA, and citation workflows.

**Petition routes** — A per-market action hub surfacing active petitions and policy contacts for each of the nine covered markets.

A machine-readable `sitemap.xml` is published at the site root.

---

## Tech stack

- **Frontend:** React, TypeScript, Tailwind CSS, TanStack Router
- **Build environment:** Lovable
- **Data layer:** Google Sheets (CSV published to web)
- **Typography:** Fraunces (editorial headlines), JetBrains Mono (metadata and labels), Inter (body)
- **Visual identity:** SVG geometry, radial burgundy and coral glows, dark theme throughout

---

## Local development

```bash
# Clone the repository
git clone [repo URL]
cd pinktaxwatch

# Install dependencies
npm install

# Start the development server
npm run dev
```

Environment variables and configuration steps will be documented here as they're finalized.

---

## Data governance and versioning

- Methodology decisions are governed by versioned markdown documents (e.g. `METHODOLOGY_v1.0.0.md`) under source control
- Source inventory is maintained with snapshot dates and refresh cadence per source
- Data changes affecting headline figures are surfaced in dispatch updates with dates and source links
- Localization is maintained in English and Hungarian

---

## Contributing

PinkTaxWatch is currently maintained by a single project lead with technical input from a small advisory group. The project is not open to external contributions to the dataset at this stage — methodology integrity depends on a controlled observation process.

Editorial corrections, broken-link reports, and methodology questions are welcome.

---

PinkTaxWatch is independent, non-commercial, and not affiliated with any retailer, tax authority, or advocacy organization referenced in the dataset.
