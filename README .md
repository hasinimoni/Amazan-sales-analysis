# Amazon India Sales — Performance Dashboard

An end-to-end sales performance analysis of an online apparel seller's order log, covering geographic spread, category mix, and fulfilment channel. Built with Excel PivotTables/PivotCharts, Power BI, and packaged as a lightweight interactive web dashboard.

**[View the live dashboard →](./index.html)**

![Status](https://img.shields.io/badge/status-complete-brightgreen) ![Made with](https://img.shields.io/badge/made%20with-Excel%20%7C%20Power%20BI%20%7C%20HTML%2FJS-blue)

---

## Overview

This project analyzes 128,969 orders (Mar–Jun snapshot) from an Amazon India apparel sales log. The dashboard opens with a four-panel **at-a-glance snapshot** — total sales by category, top 10 performing states by sale, monthly sales trend, and order status — mirroring the source Power BI report's own layout, then goes deeper into:

1. **Geography, in full** — the state view above, plus a city-level leaderboard.
2. **Fulfilment network** — Amazon-managed vs. merchant-fulfilled logistics.
3. **Salesperson &amp; product mix** — a separate electronics dataset by rep and city.

## Key results

| Metric | Value |
|---|---|
| Sales value | ₹78,592,678.30 (~₹7.86 Cr) |
| Orders count | 128,969 |
| Quantity | 117K units |
| Delivery rate | 22.33% |
| Cancellation rate | 14.21% |
| Amazon-fulfilled orders | 69.55% |
| Top state | Maharashtra (₹1.33 Cr) |
| Top city | Bengaluru (₹72.6 L) |
| Top category | Set (₹3.92 Cr, ~50% of category revenue) |
| Peak month | April (₹2.88 Cr), easing ~19% by June |

**Highlights**
- Maharashtra, Karnataka, Telangana and Tamil Nadu together outsell every other state combined — the business is heavily south/west-India weighted.
- Two categories, **Set** and **Kurta**, generate more revenue than the remaining seven categories combined.
- Sales peaked in April (₹2.88 Cr) and have declined each month since, down roughly 19% by June. March is a partial month at just ₹1.02L.
- Only 22.33% of orders are marked delivered at snapshot time; 14.21% were cancelled — worth watching alongside the 69.55% Amazon-fulfilled share.

## Tools & method

| Stage | Tool |
|---|---|
| Data cleaning & aggregation | Excel (PivotTables) |
| State / city / category rollups | Excel PivotCharts |
| Cross-filtering & fulfilment breakdown | Power BI |
| Final presentation layer | Static HTML/CSS + Chart.js |

The raw transaction log was summarized into PivotTables by `ship-state`, `ship-city`, and `Category`, cross-checked against a Power BI report for the order-count and fulfilment split. Those summarized figures feed the dashboard in `index.html` — no external data calls or backend, so it opens directly in any browser.

## Source screenshots

These are the original Excel/Power BI screenshots this dashboard was built from.

**Category & state/city PivotTables (Excel)**

![Total sales by category — PivotTable & chart](./screenshots/01-category-pivotchart.png)
![Category chart, selected view](./screenshots/02-category-chart-selected.png)
![Category totals + monthly sales trend PivotTable](./screenshots/03-category-and-monthly-trend-pivot.png)
![Top 10 states & cities by sale — PivotTables & charts](./screenshots/04-state-city-pivotcharts.png)

**Power BI views**

![Salesperson & product-type report](./screenshots/05-salesperson-productmix-powerbi.png)
![Order count by fulfilment (Amazon vs Merchant)](./screenshots/06-fulfilment-orderid-powerbi.png)
![Final Amazon Sales Dashboard — KPI cards, category, state, monthly trend, order status](./screenshots/07-amazon-sales-dashboard-final.png)

## Repository contents

```
.
├── index.html      # Self-contained interactive dashboard (Chart.js via CDN)
├── README.md        # This file
└── screenshots/      # Source PivotTable / Power BI screenshots (embedded above)
```

## Running it locally

No build step required — it's a single static file.

```bash
git clone <this-repo-url>
cd <repo-folder>
open index.html      # or double-click the file / drag into a browser
```

## Notes on the data

- Figures are drawn from Excel PivotTable/PivotChart and Power BI summaries of the source order log (not the raw row-level file).
- City and state totals reflect the **top 10 performers by revenue**, not the full geographic list.
- Currency is presented in Indian numbering (Lakh/Crore) to match the source market.
- The ₹78,592,678.30 revenue figure is confirmed by two independent PivotTables (category rollup and monthly trend), both landing on the same Grand Total — used here in place of the Power BI card's rounded ₹76M.
- Section 05 (salesperson/product mix) comes from a **separate Power BI report** covering electronics unit sales (Desktop/Laptop/Mobile/Tablet) by rep and city — it is not part of the apparel dataset and its totals are kept independent. The "Quantity by salesperson" figures are visual estimates read off a bar chart with limited axis labels and should be treated as directional.

## License

For portfolio / demonstration purposes.
