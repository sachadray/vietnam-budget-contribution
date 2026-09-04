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
| `data/VNTAX_FY2025_ownership_sector.xlsx` | Nine-sheet workbook with live formulas: firm-level tables, ownership and sector cuts, group structure, tax composition, year-on-year. |

## Read the list years carefully

**CafeF labels each list by its publication year, not the year of the payments.** The lists published in 2026 measure amounts actually remitted in financial year 2025. A list labelled 2025 is FY2024 data.

This is easy to get wrong and it matters: the FY2024 and FY2025 pictures are materially different. The convention was confirmed by cross-checking PetroVietnam, which is ₫90,991bn in both the 2026 VNTAX 200 and the STATE 100.

## Headline findings, FY2025

Of the **₫989.3tn** remitted by the 200 largest contributors, state-owned enterprises paid **₫445.6tn — 45.0%** from 74 of the 200 firms. Domestic private firms paid ₫390.3tn (39.5%) and foreign-invested firms ₫153.4tn (15.5%).

Against total FY2025 budget revenue of ₫2,650.1tn, the whole list is **37.3%** of revenue and the 74 state firms alone are **16.8%**.

**The state share fell from 54.4% to 45.0% in one year.** State remittance rose in absolute terms; it simply grew far more slowly than the private side, which was up 57%. Almost the entire swing is one firm: Vingroup went from ₫56,163bn to ₫148,773bn, of which ₫93,813bn is land and land rent — a single year of land obligations worth 9.5% of the entire list. Read the shift as a land-revenue event, not a structural rebalancing of the tax base.

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
