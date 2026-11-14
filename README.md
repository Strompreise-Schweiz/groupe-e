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

| Question | Place | Changed by |
|---|---|---|
| Where does the data come from? | [`config/source.json`](config/source.json) | a person |
| What does a person change? | `curation/<year>.json`, each change with a reason | a person |
| What is wrong with it? | [`data/checks.json`](data/checks.json) | GitHub Actions |
| What is published? | `data/`: `sources/` as the utility sent it, the rest built from it | GitHub Actions |

## Yearly tariff file

| What | Stable URL |
|---|---|
| Current year | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/current.json` |
| A given year | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/<year>.json` |

The VSE format (OpenAPI 1.0.1) with additional fields: `tariffs[].id`, `products` (which tariffs
belong together) and `_meta` (sources, repairs and corrections). It holds all three tariff forms:
`constant`, `multilevel` and `dynamic`. For a dynamic tariff, `prices.dynamic.url` points to the day
prices below. Prices exclude VAT.

## Day prices

One file per Swiss calendar day in the format of HDN 2025, chapter 7.4, always in quarter hours.
`latest.json` holds today and, once published, tomorrow. These URLs never change.

**Price sources**: what one API of the utility sends, with the corrections of `curation/`.

| Source | Valid | Stable URL |
|---|---|---|
| Groupe E Vario | open, not enabled | `https://data.strompreise-schweiz.ch/groupe-e/prices/vario/latest.json` |

Timestamps are Swiss local time with an offset, for example `2026-11-02T00:00:00+01:00`.
Parse the offset and do not assume 96 intervals: a day has 92 in March and 100 in October.
Check `_meta.complete` before you use a day.

A past day: `https://data.strompreise-schweiz.ch/groupe-e/<prices|products>/<id>/<year>/<date>.json` for the current year. All years are in git:
`https://raw.githubusercontent.com/Strompreise-Schweiz/groupe-e/main/data/<prices|products>/<id>/<year>/<date>.json`.

Format details: [`SCHEMA.md`](https://github.com/Strompreise-Schweiz/tariff-core/blob/main/SCHEMA.md).

## License

Not defined yet for this repo. See the [organization page](https://github.com/Strompreise-Schweiz).
