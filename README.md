# Groupe E

[![VSE 1.0.0](https://img.shields.io/endpoint?url=https%3A%2F%2Fdata.strompreise-schweiz.ch%2Fgroupe-e%2Fbadges%2Fvse-1.0.0.json)](data/vse-conformance.json)
[![VSE 1.0.1](https://img.shields.io/endpoint?url=https%3A%2F%2Fdata.strompreise-schweiz.ch%2Fgroupe-e%2Fbadges%2Fvse-1.0.1.json)](data/vse-conformance.json)

The badges show whether the tariff file the utility publishes follows the
[OpenAPI definitions of the VSE](https://github.com/Strompreise-Schweiz/tariff-core/tree/main/schemas/vse). Details in [`data/vse-conformance.json`](data/vse-conformance.json).

Tariff data of Groupe E, published by the
[Strompreise Schweiz](https://github.com/Strompreise-Schweiz) initiative. All logic lives in
[`tariff-core`](https://github.com/Strompreise-Schweiz/tariff-core); this repo holds configuration,
corrections and data.

Everything is listed in `https://data.strompreise-schweiz.ch/groupe-e/index.json`.

## Static tariffs (constant, multilevel)

| What | Stable URL |
|---|---|
| Current year | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/current.json` |
| A given year | `https://data.strompreise-schweiz.ch/groupe-e/tariffs/<year>.json` |

The format is the VSE format (NNMV annex 10, OpenAPI) with additional fields: `tariffs[].id`,
`products` (which tariffs belong together) and `_meta` (source, repairs and corrections).
Prices exclude VAT.

## Structure

| Path | Content | Who changes it |
|---|---|---|
| `config/source.json` | Data sources | Person |
| `curation/<year>.json` | Corrections and product mapping, each with a reason | Person |
| `data/**` | Generated data | GitHub Actions only |

Format details: [`SCHEMA.md`](https://github.com/Strompreise-Schweiz/tariff-core/blob/main/SCHEMA.md).

## License

Not defined yet for this repo. See the [organization page](https://github.com/Strompreise-Schweiz).
