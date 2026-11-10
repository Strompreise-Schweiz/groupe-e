# Groupe E

Tariff data of Groupe E, published by the
[Strompreise Schweiz](https://github.com/Strompreise-Schweiz) initiative. All logic lives in
[`tariff-core`](https://github.com/Strompreise-Schweiz/tariff-core); this repo holds configuration,
corrections and data.

Everything is listed in `https://raw.githubusercontent.com/Strompreise-Schweiz/groupe-e/main/data/index.json`.

## Static tariffs (constant, multilevel)

| What | Stable URL |
|---|---|
| Current year | `https://raw.githubusercontent.com/Strompreise-Schweiz/groupe-e/main/data/tariffs/current.json` |
| A given year | `https://raw.githubusercontent.com/Strompreise-Schweiz/groupe-e/main/data/tariffs/<year>.json` |

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
