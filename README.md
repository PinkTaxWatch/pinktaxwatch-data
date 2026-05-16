# PinkTaxWatch — Open Data Pipeline

Open, auditable data behind the **European Menstrual Affordability Index** at [pinktaxwatch.com](https://pinktaxwatch.com).

This repository documents the methodology, upstream sources, and licensing terms for the public index. The goal is full transparency: every number visible on the project site is reproducible from publicly available data, using the formula and source mapping described below.

## What PinkTaxWatch measures

PinkTaxWatch publishes a monthly Affordability Index — a single comparable figure expressing how much a typical monthly basket of essential menstrual products costs relative to female net median income in each of the 27 EU member states.

Numbers are reported in three forms:

- **% of monthly salary** — the headline affordability metric
- **Hours of work / year** — annual time-cost equivalent at the country's typical working schedule
- **Lifetime cost (32-year cohort)** — cumulative real-terms cost across a standard reproductive span

## Methodology in one sentence

**Affordability Index = (Monthly basket price × current VAT) ÷ Net monthly income × 100**

The basket is standardised across all 27 countries: a fixed-composition selection of mid-tier private-label menstrual essentials, priced from publicly listed retail averages and converted to EUR at the ECB daily reference rate.

## Upstream sources

The index does not generate primary data. It aggregates, normalises, and presents data from four established public sources:

- **Eurostat** — female net median monthly income (dataset: `earn_nt_net`)
- **European Commission TEDB** — standard VAT rates and sanitary product classification
- **European Central Bank** — daily EUR reference exchange rates
- **Local retail averages** — mid-tier private-label menstrual product pricing, curated monthly

Every monthly snapshot is timestamped against the snapshot date used for each upstream source.

## Update cadence

- **Monthly:** retail basket pricing, ECB FX rates, snapshot publication
- **Annual:** Eurostat income data refresh
- **Quarterly:** TEDB VAT rate audit
- **Continuous:** VAT change log updated whenever a member state changes a rate

## License

- **Data** in this repository is published under [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/). You are free to use, share, and adapt the data for any purpose, including commercially, with attribution.
- **Code** (when published) is released under the MIT License.

## Citation

If you use PinkTaxWatch data in research, journalism, or analysis, please cite it as:

> PinkTaxWatch (2026). *European Menstrual Affordability Index*. https://github.com/PinkTaxWatch/pinktaxwatch-data

## Contact

- Project site: [pinktaxwatch.com](https://pinktaxwatch.com)
- Data corrections, source flags, or methodology questions: open an Issue on this repository
- Editorial inquiries: info@pinktaxwatch.com
