# Who pays Vietnam's tax bill

An interactive breakdown of Vietnam's largest contributors to the state budget in **financial year 2025**, by ownership, sector and corporate group.

**Live page:** https://sachadray.github.io/vietnam-budget-contribution/

Pages serves from `main`, folder `/ (root)`. The repository must be **public** for Pages to serve on a free GitHub account.

## What's here

| File | What it is |
|---|---|
| `index.html` | The interactive page. Self-contained: all data embedded, no build step, no dependencies except Google Fonts. |
| `data/vntax200_fy2025.csv` / `.json` | All 200 firms in the VNTAX 200, with the ownership tag and the basis for it. |
| `data/state100_fy2025.csv` / `.json` | All 100 firms in the STATE 100, with corporate group, parent/subsidiary role, and whether the row counts toward the headline contribution. |
| `data/vntax200_fy2024.csv` | The prior year, for the year-on-year comparison. |
| `data/panel_fy2024_fy2025.csv` | Matched firm-level panel across the two list years: 231 enterprises, each tagged `common` / `entered` / `left`, with an `in_balanced_panel` flag. |

The page also carries the full VNTAX 200 for both list years as a searchable table (231 enterprises, English and Vietnamese names, dong and dollars), and the full STATE 100 for FY2025.
| `data/ownership_share_decomposition.csv` | The state-share change on three bases, plus the sequential attribution that sums to the published −9.31 points. |
| `data/VNTAX_FY2025_ownership_sector.xlsx` | Nine-sheet workbook with live formulas: firm-level tables, ownership and sector cuts, group structure, tax composition, year-on-year. |

## Read the list years carefully

**CafeF labels each list by its publication year, not the year of the payments.** The lists published in 2026 measure amounts actually remitted in financial year 2025. A list labelled 2025 is FY2024 data.

This is easy to get wrong and it matters: the FY2024 and FY2025 pictures are materially different. The convention was confirmed by cross-checking PetroVietnam, which is ₫90,991bn in both the 2026 VNTAX 200 and the STATE 100.

## Headline findings, FY2025

Of the **₫989.3tn** remitted by the 200 largest contributors, state-owned enterprises paid **₫445.6tn — 45.0%** from 74 of the 200 firms. Domestic private firms paid ₫390.3tn (39.5%) and foreign-invested firms ₫153.4tn (15.5%).

Against total FY2025 budget revenue of ₫2,650.1tn, the whole list is **37.3%** of revenue and the 74 state firms alone are **16.8%**.

**The state share fell from 54.4% to 45.0% in one year.** State remittance rose in absolute terms; it simply grew far more slowly than the private side, which was up 57%. Most of the swing is one firm and a re-cut list: Vingroup accounts for 5.5 of the 9.3 points and list turnover for 3.4, leaving 0.4 of a point across the 168 enterprises present in both years. Vingroup went from ₫56,163bn to ₫148,773bn, of which ₫93,813bn is land and land rent — a single year of land obligations worth 9.5% of the entire list. Read the shift as a land-revenue event, not a structural rebalancing of the tax base: on a balanced panel excluding Vingroup the state share is essentially flat, at 59.6% against 59.2%.

Real estate and construction is now the largest sector at 23.7% of the list and 91% private. Tobacco and the provincial lotteries remain entirely state-owned; coal and mining is 97% state; oil, gas and fuels is 85% state.

The STATE 100 gives an independent read on the state sector: **₫425.8tn, about 16% of national revenue**, close to the ₫445.6tn found here. The gap is mostly Vietsovpetro (₫21.5tn), which is state-controlled but which CafeF omits from the STATE 100.

## Sources

- [CafeF VNTAX 200, published 2026](https://cafef.vn/du-lieu/vntax200/2026/top-200-doanh-nghiep.chn)
- [CafeF STATE 100, published 3 September 2026](https://cafef.vn/du-lieu/state100/doanh-nghiep.chn)
- [CafeF PRIVATE 100, published 2026](https://cafef.vn/du-lieu/private100/2026/top-100-doanh-nghiep.chn)
- National budget outturn: General Statistics Office / Ministry of Finance, FY2025 revenue = ₫2,650.1tn

## Method notes

**The variable is remittance, not incidence.** "Nộp ngân sách" bundles VAT (domestic and import), corporate income tax, personal income tax withheld from staff, and land payments. VAT and withheld PIT are collected by the firm from customers and employees; the firm is the collection point, not the payer. Excise and natural-resource tax are not broken out and sit inside the totals for tobacco, brewing, fuel and mining.

**Ownership classification.** State-owned means the state holds control, central or provincial, including state-controlled joint ventures. Firms on neither the STATE 100 nor the PRIVATE 100 were classified by hand; every override is recorded in the `ownership_basis` column.

The load-bearing calls:

- **Vietsovpetro → state.** PetroVietnam holds 51%, Zarubezhneft 49%. CafeF omits it from the STATE 100.
- **Sabeco → foreign.** ThaiBev holds 53.6% via Vietnam Beverage; MOIT retains 36%.
- **Nghi Son Refinery → foreign.** Idemitsu and KPI hold 70.2% against PetroVietnam's 25.1%.
- **PVI, Binh Minh Plastics, VSIP Nghe An, Ciputra Hanoi, Long Son Petrochemicals → foreign** on foreign majority control.
- **VEAM, VEC, Resco, Hawaco, Saigon Construction, Liksin, VN Helicopter, SJC, Mobifone → state**, below the STATE 100 cut-off.

**STATE 100 deduplication.** The STATE 100 ranks parents and their larger subsidiaries in the same hundred slots, so the rows do not sum to the contribution. Thirty-one entries are subsidiaries of another entry:

```
Sum of all 100 ranked rows          518,060
Less 31 subsidiary entries          -92,225
STATE 100 contribution              425,835   (published: 425,800)
```

This reconstruction reproduces every figure the publisher states: 31 subsidiaries totalling ₫92,224bn, 71 firms above ₫1,000bn, 14 above ₫10,000bn, and the group composition (PetroVietnam 11 entries, EVN 8, Viettel 4, Vinacomin 4, Petrolimex 3).

One figure differs. The publisher books the Ho Chi Minh City lottery company under lotteries while also leaving it inside its parent HFIC, giving a lottery total of ₫59.7tn against ₫53.5tn on a consistent basis. Everything else reconciles exactly.

**Balanced panel and the decomposition.** The published lists are re-cut every year, so a change in the state share mixes two things: the firms changing and the list changing. Matching FY2024 to FY2025 on ticker gives 169 enterprises present in both years — the match is unambiguous, since ticker and trading name agree exactly, with no duplicates and no renames. No enterprise changed ownership classification between the two years.

```
Basis                          n     FY2024   FY2025   change
Published basis               200     54.4%    45.0%   -9.31 pts
Balanced panel                169     55.3%    49.4%   -5.94 pts
Balanced panel, ex-Vingroup   168     59.6%    59.2%   -0.44 pts

Sequential attribution of the published -9.31 points
  list turnover (31 in, 31 out)      -3.37
  Vingroup                           -5.50
  like-for-like growth               -0.44
                                     -----
                                     -9.31
```

The attribution is sequential, so the split between turnover and Vingroup depends on the order in which they are removed; the like-for-like residual does not. The 31 entrants are worth ₫91,838bn (9.3% of the FY2025 list) against ₫18,742bn leaving, and are 19 domestic private, 9 foreign-invested and 3 state-owned. The cut-off rose and what cleared it was almost entirely non-state.

**Only two list years are on a consistent panel.** CafeF publishes an earlier VNTAX 200 vintage; adding it would extend every series to three points without changing the method. It is not included here.

**Disclosure coverage.** The publisher reports a total for every enterprise but a named-tax breakdown for only some. Across the list, ₫460,951bn of ₫989,254bn — 46.6% — carries a named tax; 40 enterprises worth 29.5% of the list disclose no split at all. Coverage is very uneven by ownership: 36% of state-owned remittance is attributed, 75% of domestic private, and 6% of foreign-invested. This bounds the incidence caveat rather than resolving it: VAT plus withheld PIT is ₫201,329bn, or 44% of the *disclosed* components, but that ratio cannot be extrapolated to the whole list, and the share of the ₫989,254bn that is collected rather than borne is not determinable from this source.

**Land and land rent.** ₫111,837bn is separately disclosed as land and land rent, 11.3% of the list, across 21 enterprises. Vingroup is 83.9% of it. Stripping Vingroup's ₫93,813bn of land out of the denominator leaves ₫895,441bn, on which the state share is 49.8% rather than 45.0% — a sensitivity, not a restatement. The headline share on the published basis remains 45.0%.

**Years.** Every figure is financial year 2025 unless labelled FY2024. FY2025 comes from the lists CafeF published in 2026; FY2024 from the VNTAX 200 published in 2025. The page states this in the hero and repeats the year in every section kicker, axis and column header.

**Currency.** Dollar figures on the page convert at period-average rates of ₫24,900 per US$ for FY2024 and ₫26,050 for FY2025. **These are placeholders pending an official series** — they live in a single `fx` constant in the page payload and in nothing else, so replacing them updates every dollar figure at once. All shares, percentages and the decomposition are computed in dong and are unaffected by the rate.

**What this is not.** Not a census — both lists are cut-offs. Not audited accounts — publisher figures, reconciled to the publisher's own totals but not to Ministry of Finance returns. Not group accounts in the VNTAX 200 — each row there is the figure the publisher ranks on, so PetroVietnam's ₫90,991bn is the ranked entity, not the consolidated group.

## Publishing this

The page is static and self-contained. To put it on GitHub Pages:

The repository is already pushed to `github.com/sachadray/vietnam-budget-contribution`. To serve it:

1. **Settings → General → Danger Zone → Change visibility → Public.** GitHub Pages will not serve a private repository on a free account.
2. **Settings → Pages**, set **Source** to *Deploy from a branch*, branch `main`, folder `/ (root)`, and save.

The page goes live at https://sachadray.github.io/vietnam-budget-contribution/ within a minute or two.

The `.nojekyll` file stops GitHub Pages running the content through Jekyll, which is unnecessary here.

## Licence

The analysis, code and page are yours to reuse. The underlying figures belong to CafeF (VCCorp) and the General Statistics Office; check their terms before republishing the raw data commercially.
