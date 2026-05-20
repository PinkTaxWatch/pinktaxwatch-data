# PinkTaxWatch — Open Data Pipeline

🔗 **Live site:** [pinktaxwatch.com](https://pinktaxwatch.com)  
📊 **License:** Data CC-BY-4.0 · Code MIT  
🗓️ **Cadence:** Monthly snapshots

Open, auditable data behind the **European Menstrual Affordability Index** — a monthly cross-country measure of how much menstrual essentials cost relative to female net income across all 27 EU member states.

This repository documents the methodology, upstream sources, and licensing for the public index. Every figure on the live site is reproducible from publicly available data using the formula and source mapping below.

---

## What PinkTaxWatch measures

PinkTaxWatch publishes a monthly **Affordability Index** — a single comparable figure expressing the cost of a typical monthly basket of essential menstrual products as a share of female net median income in each EU member state.

Results are reported in three forms:

| Metric | What it shows |
|---|---|
| **% of monthly salary** | Headline affordability metric |
| **Hours of work per year** | Annual time-cost equivalent at typical working hours |
| **Lifetime cost (32-year cohort)** | Cumulative real-terms cost across a standard reproductive span |

---

## Methodology in one sentence

> **Affordability Index = (Monthly basket price × current VAT) ÷ Net monthly income × 100**

The basket is standardised across all 27 countries: a fixed-composition selection of mid-tier private-label menstrual essentials, priced from publicly listed retail averages and converted to EUR using ECB daily reference rates.

---

## Upstream sources

The index does not generate primary data. It aggregates, normalises, and presents data from four established public sources:

| Source | Used for | Dataset / reference |
|---|---|---|
| **Eurostat** | Female net median monthly income | `earn_nt_net` |
| **European Commission TEDB** | Standard VAT rates and sanitary product classification | TEDB live database |
| **European Central Bank** | Daily EUR reference exchange rates | ECB FX reference rates |
| **Local retail averages** | Mid-tier private-label menstrual product pricing | Curated monthly |

Every monthly snapshot is timestamped against the snapshot date of each upstream source.

---

## Update cadence

- **Monthly** — retail basket pricing, ECB FX rates, snapshot publication
- **Quarterly** — TEDB VAT rate audit
- **Annual** — Eurostat income data refresh
- **Continuous** — VAT change log updated whenever a member state changes a rate

---

## License

- **Data** — published under [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/). Free to use, share, and adapt for any purpose, including commercially, with attribution.
- **Code** (when published) — released under the [MIT License](https://opensource.org/licenses/MIT).

---

## Citation

If you use PinkTaxWatch data in research, journalism, or analysis, please cite as:

> PinkTaxWatch (2026). *European Menstrual Affordability Index*. https://github.com/PinkTaxWatch/pinktaxwatch-data

---

## Contact

- **Project site:** [pinktaxwatch.com](https://pinktaxwatch.com)
- **Data corrections, source flags, methodology questions:** [open an Issue](https://github.com/PinkTaxWatch/pinktaxwatch-data/issues)
- **Editorial inquiries:** [info@pinktaxwatch.com](mailto:info@pinktaxwatch.com)

---

*PinkTaxWatch is an independent, non-commercial public-interest project. Not affiliated with any retailer, tax authority, or advocacy organisation referenced in the dataset.*
