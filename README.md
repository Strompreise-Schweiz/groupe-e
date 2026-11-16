# Groupe E

[![VSE 1.0.0](https://img.shields.io/endpoint?url=https%3A%2F%2Fdata.strompreise-schweiz.ch%2Fgroupe-e%2Fbadges%2Fvse-1.0.0.json)](data/checks.json)
[![VSE 1.0.1](https://img.shields.io/endpoint?url=https%3A%2F%2Fdata.strompreise-schweiz.ch%2Fgroupe-e%2Fbadges%2Fvse-1.0.1.json)](data/checks.json)

The badges show whether the yearly tariff file the utility publishes follows the
[OpenAPI definitions of the VSE](https://github.com/Strompreise-Schweiz/tariff-core/tree/main/schemas/vse). Details in [`data/checks.json`](data/checks.json).

Tariff data of Groupe E, published by the
[Strompreise Schweiz](https://github.com/Strompreise-Schweiz) initiative. All logic lives in
[`tariff-core`](https://github.com/Strompreise-Schweiz/tariff-core); this repo holds configuration,
corrections and data.

Everything is listed in `https://data.strompreise-schweiz.ch/groupe-e/index.json`.

## Where what is

| Folder | Holds | Changed by |
|---|---|---|
| [`config/source.json`](config/source.json) | where the data comes from | a person |
| `curation/<year>.json` | corrections and products, each with a reason | a person |
| `data/sources/` | the files of Groupe E, unchanged: the yearly file and in `days/` what the APIs sent | GitHub Actions |
| `data/tariffs/` | all tariffs, repaired to VSE 1.0.1 and corrected, with the day prices of the dynamic tariffs | GitHub Actions |
| `data/products/` | what a customer pays: every component and the total | GitHub Actions |
| [`data/checks.json`](data/checks.json) | what is wrong with all of the above | GitHub Actions |

## What a household pays

Start here. A product is what a customer pays: energy, grid, metering and fees together, excluding
VAT. `total.fixed` holds the prices per month, `total.windows` the prices per kWh by time of day.

No product yet: no yearly file is configured in `config/source.json`.

## Tariffs

| What | Stable URL |
|---|---|
| All tariffs of the current year | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/current.json` |
| All tariffs of a given year | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/<year>.json` |
| Day prices of a dynamic tariff, today and tomorrow | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/current/<tariff>.json` |
| Day prices of a dynamic tariff, one day | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/<year>/<tariff>/<date>.json` |

The yearly file is the VSE format (OpenAPI 1.0.1) with additional fields: `tariffs[].id`, `products`
and `_meta` (sources, repairs and corrections). For a dynamic tariff, `prices.dynamic.url` points to
its day prices. These are an addition to the yearly file: `tariffs/2026/<tariff>/` holds the days of
the tariff `<tariff>` in `tariffs/2026.json`.

The Vario API of Groupe E is configured but not enabled.

Timestamps are Swiss local time with an offset, for example `2026-11-02T00:00:00+01:00`.
Parse the offset and do not assume 96 intervals: a day has 92 in March and 100 in October.
Check `_meta.complete` before you use a day. The site serves the days of the current year; all years
are in git under `https://raw.githubusercontent.com/Strompreise-Schweiz/groupe-e/main/data/`.

Format details: [`SCHEMA.md`](https://github.com/Strompreise-Schweiz/tariff-core/blob/main/SCHEMA.md).

## License

Not defined yet for this repo. See the [organization page](https://github.com/Strompreise-Schweiz).
