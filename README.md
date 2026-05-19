# PinkTaxWatch

Public-interest tracking of menstrual product affordability across European retail markets.

https://www.pinktaxwatch.com

**Current snapshot:** 2026-05 · **Markets:** 9 · **Retail observations:** 38 · **Methodology version:** v1.0

---

## About

PinkTaxWatch is an independent data project comparing menstrual product affordability across selected European countries using:

* recorded retail prices
* VAT rates
* Eurostat income data

The project focuses on one question:

> How much does a comparable monthly menstrual product basket cost relative to local wages, depending on where someone lives?

The current public release includes:

* 9 European markets (DE, AT, HU, CZ, UK, IE, DK, NL, BE)
* 38 recorded retail price observations
* affordability rankings
* VAT-adjusted comparisons
* country-level basket calculations

---

## Methodology

The current dataset uses a normalized monthly basket:

* 20 pads
* 20 tampons

This composition is designed to allow direct cross-category price comparisons across markets; it is not a prescriptive recommendation for individual consumption.

For each country:

1. Recorded retail products are converted into unit prices.
2. The lowest recorded own-brand unit price is selected per category.
3. The basket is reconstructed from those normalized prices.

Affordability is calculated as:

```txt
monthly basket cost ÷ average net monthly earnings
```

Income reference:

* Eurostat `earn_nt_net`
* **Family Case A1** (single full-time worker, no children, 100% of average wage)
* 2024 reference year

VAT rates are verified per country against primary government sources, with verification dates recorded in the dataset metadata.

The project prioritizes:

* transparency
* comparability
* reproducibility

over statistical representativeness.

---

## Data Sources

The dataset combines:

* publicly visible retail prices
* country VAT rates (primary government source per market)
* Eurostat income data

Retail observations are manually reviewed before publication. The current dataset is small by design — human verification catches substitution SKUs, sale prices, and pack-size variations that automated scraping would miss.

---

## Repository Structure

```txt
/public
  dataset-2026-05.csv
  country-summary-2026-05.json
  observations-2026-05.json
/src
  components/
  pages/
  locales/
  hooks/
```

---

## Tech Stack

* React
* TypeScript
* Tailwind
* Google Sheets (published-to-web CSV — primary data source consumed by the frontend)
* Lovable (build environment)
* [hosting / CDN — fill in: Vercel / Netlify / Cloudflare Pages / etc.]

AI-assisted workflows are used for:

* research support
* data collection assistance
* frontend iteration

All public calculations and published observations are manually reviewed before release.

---

## Scope Limitations

PinkTaxWatch is an observational public-interest dataset, not an official statistical index.

Current limitations include:

* limited retailer coverage
* selected European markets only
* recorded shelf prices rather than full household consumption
* no promotional pricing
* no loyalty-card discounts
* current-price lifetime calculations do not model future inflation
* income reference data lags retail price observations by approximately 18 months due to Eurostat publication cycles — this may slightly overstate affordability burden in markets with rapid recent wage growth

The dataset should be interpreted as:

> a comparable affordability baseline, not a definitive measure of national menstrual spending.

---

## Reproducibility

The published CSV and derived JSON files contain enough detail to reproduce:

* affordability rankings
* basket calculations
* VAT-adjusted comparisons
* lifetime baseline estimates

All derived values displayed on the public site are computed from the published dataset.

---

## How to Cite

If you reference this dataset, its derived rankings, or its visualizations in journalism, research, or policy work, please cite as:

> PinkTaxWatch (2026). *Menstrual product affordability across European retail markets, 2026-05 snapshot.* Available at https://www.pinktaxwatch.com. Dataset licensed CC BY 4.0.

When citing a specific data point, please include the snapshot date (`2026-05`) to support reproducibility across releases.

---

## Future Work

Planned future work may include:

* additional European markets
* longitudinal releases (multi-snapshot comparison)
* regional comparisons within markets
* expanded product categories (menstrual cups, period underwear, reusables)
* work-time affordability metrics
* perimenopause and postmenopause scope extension (lifetime cost models currently underestimate this phase)
* search behavior as a public-interest data layer (aggregated keyword volume, public forum signals) — exploratory v2.0 scope

The project is intentionally evolving slowly to preserve methodological consistency between releases.

---

## License

* **Dataset:** CC BY 4.0 — free to use with attribution.
* **Code:** MIT License.

---

## Disclaimer

PinkTaxWatch is an independent public-interest data project.

The dataset and content are published in good faith and without warranty. While calculations are manually reviewed, errors or inconsistencies may still occur.

This project does not represent:

* a government institution
* a statistical authority
* or a medical recommendation system

---

## Contact

* **Website:** https://www.pinktaxwatch.com
* **Issues, corrections, methodology questions:** use the GitHub Issues tab
* **Press, research, policy inquiries:** contact form on the website
