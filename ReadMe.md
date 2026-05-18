# Financial Forecasting Tool

An Excel-based financial forecasting tool that projects 5-year income statements for publicly traded companies across three scenario types — Base, Strong, and Weak — using historical financial data and dynamic assumptions.

---

## Overview

The tool is built around a single Excel workbook that pulls historical income statement data for a set of ticker symbols and generates forward-looking projections based on scenario-specific growth rates and margin assumptions. The dashboard updates dynamically when the user selects a different company or scenario via dropdown menus.

![Dashboard](dashboard.png)
*5-year income statement projections with dynamic ticker and scenario selection.*

![Assumptions](assumptions.png)
*Year 4–5 growth rates and margin assumptions by scenario (Base / Strong / Weak).*

---

## Features

- Dynamic ticker selection — switch between companies without editing formulas
- Three forecast scenarios: Base (historical CAGR), Strong (+25% adjustment), Weak (-25% adjustment)
- 5-year income statement projections covering revenue, cost of revenue, gross profit, SG&A, operating income, and key margins
- Scenario-specific assumptions sheet for Year 4–5 growth rates and margins
- Extensible data sheet — add new tickers by appending rows to the Data sheet

---

## Getting Started

**Requirements:** Microsoft Excel 2016 or later (uses `UNIQUE()` and named ranges)

1. Clone the repository:
   ```
   git clone https://github.com/abdalrhman-abas-0/financial-forecasting.git
   ```

2. Open `financial_forecast_tool.xlsx` in Excel.

3. Select a company — go to cell **B2** (`selected_symbol`) and choose a ticker from the dropdown (NAVI, PYPL, QRVO, WRK).

4. Select a scenario — go to cell **B13** (`selected_scenario`) and choose Base, Strong, or Weak.

5. The Dashboard sheet updates automatically with projected financials.

---

## File Structure

```
financial_forecast_tool.xlsx
    ├── Dashboard       ← 5-year projections and margin summary (main view)
    ├── Assumptions     ← Scenario growth rates and margin inputs for Year 4–5
    └── Data            ← Historical income statement data by ticker
```

---

## Adding New Tickers

Append rows to the `Data` sheet with the following fields populated:

`ticker_symbol`, `years`, `period_ending`, `total_revenue`, `cost_of_revenue`, `sales_general_and_admin`, `other_operating_items`, `growth_profits`, `operating_profits`, `growth_margin`, `operating_margin`

The `UNIQUE()` formula in the ticker dropdown will pick up the new symbol automatically.

---

## Methodology

Revenue and margin projections are built in two phases:

- **Years 1–3** are anchored to historical actuals from the Data sheet.
- **Years 4–5** apply scenario-specific growth rate and margin adjustments defined in the Assumptions sheet.

The Base case preserves the historical CAGR. Strong and Weak cases adjust that rate by ±25%, with corresponding margin shifts applied to gross profit and operating income lines.
