# Jamaat's quiet advantage: the women's vote

An interactive data-journalism analysis of how men and women voted differently in Bangladesh's
national election — with a focus on how **Jamaat-e-Islami consistently outperformed among women**.

**[▶ Open the presentation](index.html)** · **[▶ Open the map](map.html)**
(serve the folder over any static HTTP server — see below.)

## The finding

Bangladesh runs many polling stations segregated by sex. By matching each men's centre to the
women's centre **in the same building** — 2,453 such pairs — we can compare how men and women at
the identical spot voted, holding geography constant.

- **Jamaat is the only major party that gained among women: +1.6 points** (31.2% → 32.8%),
  while the BNP was flat and every other party slipped.
- The effect is **concentrated, not universal** — the median seat shows ~0 gap. The lift comes
  from the south-west (the Jessore–Satkhira–Jhenaidah belt), where women push Jamaat past 50%.
- **Women mattered most exactly where Jamaat won:** in its won seats the female advantage was
  +3.7 points, turning a 49% male plurality into a 53% female majority.

## Methodology

Every gender figure is computed from **same-station pairs** — a male centre matched to the female
centre in the same building (exact + fuzzy name match) within a constituency — so no comparison
confounds sex with location. Per-constituency charts use seats with ≥4 pairs (210 seats); district
charts use ≥6 pairs. Single-sex centres are ~26% of all 42,382 centres (25% of the electorate);
the rest are mixed and can't be split by sex. Seat winners and national vote shares come from the
full official results, not the pairs.

Party symbols: ধানের শীষ = BNP · দাঁড়িপাল্লা = Jamaat-e-Islami · হাতপাখা = Islami Andolan · শাপলা কলি = NCP.

## Run it locally

```bash
# from this folder
python3 -m http.server 8000
# then open http://localhost:8000/index.html
```

Any static server works; the map fetches `constituencies_story.geojson` and the charts fetch the
`*.json` data files from this folder, so it must be served over HTTP (not opened as a `file://`).

## Contents

| File | What it is |
|------|------------|
| `index.html` | The scrollable presentation (11 charts, inline SVG, light/dark) |
| `map.html` | Interactive constituency choropleth (Leaflet) — 4 views |
| `chart_data.json` | Aggregate gender metrics (same-station pairs) |
| `winner_data.json` | Seat outcomes + gender-split "parliaments" |
| `won_femadv.json` | Female advantage grouped by who won the seat |
| `const_map_data.json` | Per-constituency values for the map |
| `overview_data.json` | Election / coverage / methodology headline numbers |
| `constituencies_story.geojson` | Simplified constituency boundaries |

All data files are aggregate and contain no personal information.
