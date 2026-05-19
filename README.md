# PinkTaxWatch

Public-interest tracking of menstrual product affordability across European retail markets.

https://www.pinktaxwatch.com

---

## About

PinkTaxWatch is an independent data project comparing menstrual product affordability across selected European countries using:

* recorded retail prices
* VAT rates
* Eurostat income data

The project focuses on one question:

> How much does a comparable monthly menstrual product basket cost relative to local wages depending on where someone lives?

The current public release includes:

* 9 European markets
* 38 recorded retail price observations
* affordability rankings
* VAT-adjusted comparisons
* country-level basket calculations

---

## Methodology

The current dataset uses a normalized monthly basket:

* 20 pads
* 20 tampons

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
* single full-time worker
* no children
* 100% of average wage
* 2024 reference year

The project prioritizes:

* transparency
* comparability
* reproducibility

over statistical representativeness.

---

## Data Sources

The dataset combines:

* publicly visible retail prices
* country VAT rates
* Eurostat income data

Retail observations are manually reviewed before publication.

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
* Airtable
* Lovable
* Cloudflare / Vercel

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

## Future Work

Planned future work may include:

* additional European markets
* longitudinal releases
* regional comparisons
* expanded product categories
* work-time affordability metrics

The project is intentionally evolving slowly to preserve methodological consistency.

---

## License

Dataset:
CC BY 4.0

Code:
MIT License

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

Website:
https://www.pinktaxwatch.com

Issues and corrections:
Use the GitHub Issues tab for dataset corrections, methodology questions, or feedback.
