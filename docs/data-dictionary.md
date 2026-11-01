# Data dictionary

The Power BI model exposes a single table named `Sales`. The source is the `Data_Sheet` worksheet in `car_sale_final-4_1_.xlsx`.

| Field | Description | Origin |
|---|---|---|
| `SL No` | Source row/serial number | Renamed from `SL No.` |
| `Product ID` | Product identifier; model keeps IDs beginning with `TATA` | Renamed from `Product_ID` |
| `City Category` | City classification | Renamed from `City_Category` |
| `Batch` | Source batch identifier | Source |
| `Model Name` | Vehicle model name | Source |
| `Delivery Status` | Delivered, Pending or In Transit | Source |
| `Product Cost` | Base product cost | Source |
| `Tax and Delivery Cost` | Taxation and delivery cost | Renamed from `Taxation & Delivery Cost` |
| `Final Cost` | Product cost plus related costs as represented in source | Source |
| `On Road Price` | On-road selling price | Source |
| `Fuel Type` | `EV` when model name ends in ` EV`; otherwise `Non-EV` | Derived in Power Query |
| `Profit` | `On Road Price - Final Cost` | Derived in Power Query |

## Model filters

Rows are retained only when `Product_ID` is not null and its text value starts with `TATA`. The supplied workbook has 65 worksheet rows and the modelled filter returns 50 product records.

## Measure interpretation

- **Delivery Rate** = Delivered Units / Total Units, with the delivery-status filter removed from the denominator.
- **Pipeline Value** = Total On Road Value − Delivered Revenue.
- **Estimated Profit** = sum of `Profit` across all modelled rows.
- **Realised Profit** = sum of `Profit` for rows marked `Delivered`.
- **Profit Margin %** = Estimated Profit / Total On Road Value.

Currency values are sourced as numeric values in the workbook; the report formats the value measures in millions. The README's rupee-formatted snapshot assumes the workbook's monetary values are INR.
