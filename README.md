# PinkTaxWatch — Open Data Pipeline

Open, auditable data behind the **European Menstrual Affordability Index** at [pinktaxwatch.com](https://pinktaxwatch.com).

This repository contains the raw inputs, monthly snapshots, and methodology documentation that underpin every number shown on the public site. Anyone can download, audit, or cite this data.

## What's here

- `data/snapshots/` — monthly index snapshots (one JSON per month, 27 countries × full metrics)
- `data/sources.md` — list of upstream data sources with direct URLs
- `data/changelog.md` — version notes per release
- `docs/METHODOLOGY.md` — full methodology in long form
- `docs/CITATION.md` — recommended citation format
- `scripts/` *(coming soon)* — the automated fetchers and aggregators that produce each monthly snapshot

## Upstream sources

| Source | What we use | URL |
|---|---|---|
| Eurostat `earn_nt_net` | Female net median monthly income, 27 EU countries | https://ec.europa.eu/eurostat/databrowser/view/earn_nt_net |
| European Commission TEDB | Standard VAT rate per country, sanitary product VAT classification | https://taxation-customs.ec.europa.eu/taxation/vat/vat-rates-eu_en |
| ECB FX reference rates | Monthly currency-to-EUR conversion | https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/ |
| Local retail index (curated) | Mid-tier private-label menstrual product basket pricing | See `data/sources.md` for retailer list |

## Methodology in one sentence

**Affordability Index = (Monthly basket price × current VAT) ÷ Net monthly income × 100**

For the full breakdown, see [`docs/METHODOLOGY.md`](./docs/METHODOLOGY.md).

## Update cadence

- **Monthly:** Retail basket prices, ECB FX rates, monthly snapshot publication
- **Annual:** Eurostat earn_nt_net income data
- **Quarterly:** TEDB VAT rate audit
- **Continuous:** `VAT_History` log entry every time a member state changes a rate

## How to use this data

1. **Download a snapshot:** browse `data/snapshots/` and grab the JSON for the month you need
2. **Reproduce a number:** every value on [pinktaxwatch.com](https://pinktaxwatch.com) is computable from the published snapshot + the formula in `docs/METHODOLOGY.md`
3. **Cite us:** use the form below
4. **Found an error?** Open an Issue. We treat data corrections as critical fixes.

## License

- **Data** (everything in `data/`): [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/) — free to use with attribution
- **Code** (everything in `scripts/`): MIT

## Cite this dataset

> PinkTaxWatch (2026). *European Menstrual Affordability Index*, monthly dataset. https://github.com/PinkTaxWatch/pinktaxwatch-data

## Contact

- Project site: [pinktaxwatch.com](https://pinktaxwatch.com)
- Issues, corrections, or data contributions: open an Issue on this repo
- Editorial: info@pinktaxwatch.com
