# Before the Fed, the Fed before WWII, and the Fed after WWII

An interactive comparison of US inflation, business-cycle contractions and bank failures from 1837 to 2026, split into three periods:

- **Before the Fed** — 1837–1913 (Free Banking and National Banking eras)
- **Fed before WWII** — 1914–1945 (early Fed and gold standard, Great Depression, deposit insurance from 1934, WWII)
- **Fed after WWII** — 1946–2026 (Bretton Woods, Great Inflation, Great Moderation, post-2008)

The site is a single static page (`index.html`) that reads the CSV files in `data/` and draws the charts with D3 (vendored in `vendor/`). Hover over any chart for exact values.

## Data

| File | Contents | Source |
|---|---|---|
| `data/cpi.csv` | Annual CPI (1967 = 100) and inflation, 1830–2026 | Federal Reserve Bank of Minneapolis, "Consumer Price Index, 1800–" (pre-1913 values are BLS reconstructions; 2026 is a Q3-to-Q3 estimate) |
| `data/contractions.csv` | Peak and trough dates of every contraction | NBER Business Cycle Dating Committee (1857–2020); Davis (2006, *Journal of Economic History*) annual dates for 1836–37 and 1839–40 |
| `data/output_annual.csv` | Annual industrial output index | NBER Macrohistory manufacturing production index, FRED A0107AUSA322NNBR (1863–1918); annual average of Fed industrial production, FRED INDPRO (1919–2025) |
| `data/bank_failures.csv` | Banks closed per year | *Historical Statistics of the United States*, series X-741, bank suspensions (1864–1933); FDIC failures of insured institutions, FRED BKFTTLA641N (1934–2026; 2021–22 entered as 0; 2026 year to date) |
| `data/panic_severity.csv` | Pre-Fed recessions with vs. without a major banking panic | Jalil (2015), *AEJ: Macroeconomics* |
| `data/regimes.csv`, `data/eras.csv` | Period and epoch definitions | Author's grouping by monetary regime |

## Method notes

- **Depth of a contraction** is the peak-to-trough fall in *annual* output: the higher of the peak year and the year before, compared with the lowest year from the peak through the trough year. Annual data are used on both sides of 1913 so the comparison is like-for-like; monthly data after 1919 would make later contractions look deeper simply by catching short dips (Romer's measurement critique). Annual data understate short contractions, and contractions before 1863 are not measured.
- **Contractions** are assigned to the period in which they began. Time in contraction runs through October 2026.
- **Bank counts** change definition in 1934 (suspensions before, FDIC failures after) and are not scaled by the number of banks.

## Updating

Edit the CSVs in `data/` and the page recomputes everything on load. To preview locally, run `python3 -m http.server` in this folder and open http://localhost:8000.
