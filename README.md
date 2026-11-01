<div align="center">

# 🚗 Tata Motors Sales & Profitability Analytics

### An interactive Power BI project for exploring vehicle sales, delivery performance, revenue, and profitability.

<p>
  <img src="https://img.shields.io/badge/Power%20BI-PBIP-F2C811?style=for-the-badge&logo=powerbi&logoColor=111111" alt="Power BI">
  <img src="https://img.shields.io/badge/Data%20Model-TMDL-5A6ACF?style=for-the-badge" alt="TMDL">
  <img src="https://img.shields.io/badge/Power%20Query-M-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white" alt="Power Query">
  <img src="https://img.shields.io/badge/Status-Portfolio%20Project-2EA44F?style=for-the-badge" alt="Portfolio project">
</p>

**Turning vehicle-level sales records into actionable business insights.**

</div>

---

## ✨ Project at a glance

This project explores a Tata Motors vehicle-sales dataset using **Power BI Desktop**. It combines Power Query transformations, a semantic model written in TMDL, and interactive report pages to help answer questions such as:

- How many vehicles have been sold, delivered, or are still in the pipeline?
- What are the revenue, cost, estimated profit, and profit margin?
- Which vehicle models contribute most to sales and profitability?
- How do delivery status and city category affect the sales picture?
- How does the EV segment compare with non-EV models?

> **Dataset note:** The included workbook contains 65 worksheet rows in `Data_Sheet`; the Power Query model filters to 50 non-empty product records whose IDs begin with `TATA`. The headline figures below describe those 50 modelled records.

## 📊 Snapshot of the included data

| KPI | Value |
|---|---:|
| Modelled vehicle records | **50** |
| Vehicle models | **11** |
| City categories | **3** |
| On-road revenue | **₹6.71 Cr** |
| Final cost | **₹5.92 Cr** |
| Estimated profit | **₹79.28 L** |
| Estimated profit margin | **11.8%** |
| Delivered | **35** |
| Pending | **8** |
| In transit | **7** |

<sub>Calculated from the included workbook after applying the same TATA product-ID filter as the Power Query model. Values are descriptive of this supplied dataset, not official company results.</sub>

## 🧭 Report pages

| Page | What it helps explore |
|---|---|
| **Overview** | High-level sales KPIs, delivery mix, revenue and model-level performance |
| **Profitability** | Cost, estimated profit, realised profit and margin comparisons |
| **Details** | Vehicle-level records and supporting breakdowns |

The report is delivered as a **Power BI Project** (`.pbip`) with a PBIR report definition and a TMDL semantic model, rather than only a single packaged `.pbix` file.

## 🛠️ Built with

- **Power BI Desktop** — report authoring and interactive visualisations
- **Power Query (M)** — importing, filtering, cleaning, typing and deriving fields
- **DAX** — reusable business measures and KPI calculations
- **TMDL / PBIR** — source-controlled semantic model and report definitions
- **Microsoft Excel** — source workbook

## 🧮 Data preparation & business logic

The `Sales` query performs the following steps:

1. Reads the `Data_Sheet` worksheet from the Excel workbook.
2. Promotes the first row to column headers.
3. Keeps the fields required for the analysis.
4. Filters to records with a non-empty `Product_ID` beginning with `TATA`.
5. Renames source columns and applies data types.
6. Derives `Fuel Type` from the model name (`EV` suffix → EV; otherwise Non-EV).
7. Calculates `Profit` as `On Road Price - Final Cost`.

### Core DAX measures

| Measure | Definition |
|---|---|
| `Total Units` | Count of rows in the Sales table |
| `Delivered Units` | Units with `Delivery Status = Delivered` |
| `Pending Units` | Units with `Delivery Status = Pending` |
| `In Transit Units` | Units with `Delivery Status = In Transit` |
| `Delivery Rate` | Delivered units divided by all units, ignoring delivery-status filters |
| `Total On Road Value` | Sum of on-road price, displayed in millions |
| `Delivered Revenue` | On-road value for delivered units, displayed in millions |
| `Pipeline Value` | Total on-road value less delivered revenue |
| `Total Cost` | Sum of final cost, displayed in millions |
| `Estimated Profit` | Sum of profit, displayed in millions |
| `Realised Profit` | Profit for delivered units, displayed in millions |
| `Profit Margin %` | Estimated profit divided by total on-road value |
| `Avg On Road Price` | Average on-road price per record |

## 🚀 Open the project locally

### Requirements

- Windows
- Power BI Desktop with support for **Power BI Project (`.pbip`)**, **TMDL**, and **PBIR** enabled where required
- Microsoft Excel workbook included in this repository

### Steps

1. Clone or download this repository.
   ```bash
   git clone https://github.com/<your-username>/Tata-Motors-Sales-Analytics.git
   cd Tata-Motors-Sales-Analytics
   ```
2. Open `CarSales.pbip` in Power BI Desktop.
3. If prompted, enable the relevant Power BI Project, TMDL and PBIR preview features in **File → Options and settings → Options → Preview features**, then restart Power BI Desktop.
4. In the semantic model parameter **`ExcelFilePath`**, set the full local path to:
   `car_sale_final-4_1_.xlsx`
5. Select **Home → Refresh** (or refresh from Power BI Desktop) to load the workbook.
6. Explore the Overview, Profitability and Details pages.

### Data source parameter

The model uses a Power Query parameter named `ExcelFilePath`. It currently contains a placeholder Windows path. Update it to the location of the workbook on your machine before refreshing.

## 📁 Repository structure

```text
Tata-Motors-Sales-Analytics/
├── CarSales.pbip
├── car_sale_final-4_1_.xlsx
├── CarSales.Report/
│   └── definition/
│       ├── report.json
│       └── pages/
│           ├── overview.../
│           ├── profit.../
│           └── details.../
├── CarSales.SemanticModel/
│   └── definition/
│       ├── model.tmdl
│       ├── expressions.tmdl
│       └── tables/
│           └── Sales.tmdl
├── docs/
│   └── data-dictionary.md
├── .gitignore
└── README.md
```

## 🔍 Possible next improvements

- Add date fields and a proper calendar table for time-intelligence analysis.
- Add drill-through pages for model and city-category deep dives.
- Introduce explicit validation for missing, duplicate or unexpected product records.
- Add EV vs. non-EV profitability comparisons and delivery-rate segmentation.
- Capture report screenshots and add them to a `screenshots/` folder.

## ⚠️ Limitations & interpretation

- This is a portfolio analytics project based on the workbook included here.
- The source workbook does not provide a transaction date in the modelled fields, so time-series trends are not currently available.
- `Estimated Profit` includes all modelled records; `Realised Profit` includes only delivered records.
- The Power Query logic infers EV status from the model-name suffix. Confirm this convention if the source data changes.
- The dataset is small (50 modelled records), so findings should not be treated as statistically representative of the wider automotive market.

## 👤 Author

**Your Name**  
Add your LinkedIn and portfolio links here.

---

<div align="center">

If this project was useful, consider giving the repository a ⭐

**Built with Power BI · Power Query · DAX · TMDL**

</div>
