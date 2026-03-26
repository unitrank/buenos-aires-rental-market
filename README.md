# Buenos Aires Rental Market Data

Monthly snapshots of the Buenos Aires rental market. Aggregated, anonymized statistics from [Unitrank](https://unitrank.com).

## What's included

| File | Description |
|------|-------------|
| `summary.csv` | City-wide medians by bedroom count and rental type (Airbnb, temp furnished, long-term furnished, long-term unfurnished) |
| `by-barrio.csv` | Per-neighborhood breakdown: medians, inventory counts, Airbnb vs direct price gap |
| `cost-breakdown.csv` | All-in cost decomposition: base rent, expensas (building fees), utilities, broker fee, caucion (guarantee) |
| `inventory.csv` | Listing counts by source and bedroom count |
| `snapshot.json` | All of the above in a single JSON file |
| `metadata.json` | Generation date, methodology version, data definitions |

## Key numbers (latest)

Updated monthly. See the latest `data/YYYY-MM/summary.csv` for current figures.

## Methodology

**Sources:** Airbnb and Argenprop listings in Buenos Aires (CABA + Zona Norte + GBA, 74 neighborhoods).

**All-in monthly cost includes:**
- Base rent
- Expensas (building/condo fees)
- Estimated utilities ($40 + $4/sqm + $25/AC unit, based on 2026 Buenos Aires tariffs)
- Broker fee (amortized over contract duration; included when charged, regardless of legal status)
- Seguro de caucion / guarantee (amortized; zero for temporary rentals)

**Price trimming:** Bottom 10% and top 20% of prices excluded per category (PERCENT_RANK >= 0.10 AND <= 0.80). Minimum $200/month filter removes placeholder listings.

**Furnished detection:** Based on bed presence in listing photos (LLM-extracted `total_bed_capacity > 0`).

**Currency:** All prices in USD. Argentine peso prices converted at blue/MEP rate at time of scraping.

**What's NOT included:** Individual listing data, listing URLs, photos, descriptions, agent data, or any personally identifiable information. Only aggregated statistics.

## Data structure

```
data/
  2026-03/
    summary.csv
    by-barrio.csv
    cost-breakdown.csv
    inventory.csv
    snapshot.json
    metadata.json
  2026-04/
    ...
```

## License

[CC BY 4.0](LICENSE) — use freely, attribute Unitrank with a link to [unitrank.com](https://unitrank.com).

## About Unitrank

Apartment search engine for Buenos Aires. Compares the true cost of living in each apartment, not just rent. Aggregates Airbnb, Argenprop, and direct rentals into one search.

[unitrank.com](https://unitrank.com) · [Eviction law guide](https://unitrank.com/en/ar/buenos-aires/guides/desalojo-expres) · [About](https://unitrank.com/about)
