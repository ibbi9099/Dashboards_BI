# Power BI Dashboards

A collection of Business Intelligence dashboards built in Power BI Desktop, covering short-term rental listings, a sales data warehouse, and shipment logistics.

| # | Project | Domain | Files |
|---|---------|--------|-------|
| 1 | [Airbnb Listings Analysis](#1-airbnb-listings-analysis) | Hospitality / pricing | `BI_Project.pbix`, report PDF |
| 2 | [Sales Data Warehouse Dashboard](#2-sales-data-warehouse-dashboard) | Retail sales | `Ibrahim_Khalil_27003_DWH_sales.pbix` |
| 3 | [Shipment & Delivery Analysis](#3-shipment--delivery-analysis) | Supply chain | `PowerBI - V2 16th Nov.pdf` |

> **Tip:** Open the `.pbix` files with [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows).

---

## 1. Airbnb Listings Analysis

A two-page interactive dashboard exploring Airbnb listings: pricing, room types, availability, reviews and cancellation policies.

**Dataset:** Airbnb listings, 102,599 rows × 13 columns (price, service fee, minimum nights, number of reviews, review rate, availability, neighbourhood group, room type, cancellation policy, construction year, host verification, etc.)

**Data preparation (Jupyter Notebook / Python):**
- Dropped rows with missing neighbourhood group / neighbourhood
- Imputed missing `price` and `service fee` with the mean
- Dropped rows missing `number of reviews`, `review rate number` or `availability 365`
- Standardised text fields
- Output loaded into Power BI as `Cleaned_Airbnb_Data`

**Dashboard pages**

| Page | Visuals |
|------|---------|
| **Analysis Across Neighborhood Groups** | Room-type donut chart, average reviews & price by room type (combo chart), room-type availability by neighbourhood group (ribbon chart), KPI cards (average price, availability, rating, service fee), slicers for neighbourhood group and review rating |
| **Property Type Analysis** | Decomposition tree (cancellation policy → neighbourhood group → room type → minimum nights), price by construction year (area chart), same KPI cards, slicers for cancellation policy and review rating |

**Key insights**
- Most listings are in Manhattan and Brooklyn, mostly *Entire home/apt* or *Private room*.
- Manhattan skews towards higher prices; Brooklyn looks more affordable.
- Average rating is about 3.28, which leaves room for hosts to improve guest experience.
- Review counts are heavily skewed (most listings have fewer than 50 reviews) and many listings aren't available year-round.
- No strong correlation between price, minimum nights and number of reviews.

**Team:** Ahmad Murtaza (dashboard design & storytelling) · Ibrahim Khalil Ahmad (EDA & data cleaning)

---

## 2. Sales Data Warehouse Dashboard

A sales overview dashboard built on a **star-schema data warehouse**.

**Data model**

```
DIM_CUSTOMER ─┐
DIM_DATE ─────┤
DIM_PRODUCT ──┼── FACT_ORDER_ITEM
DIM_SHIPPER ──┤
DIM_ORDER_STATUS ┘
```

**Visuals**
- KPI cards: number of orders, total sales (extended price), total quantity sold, customer count
- Number of orders by month (line chart, with a date hierarchy for drill-down)
- Top 5 product categories by orders (bar chart)

---

## 3. Shipment & Delivery Analysis

A logistics dashboard comparing shipment modes (Air, Air Charter, Ocean, Truck) on delivery delay, freight cost, weight and sales. It includes a written chart-by-chart analysis.

**Visuals**
- Trend of average delivery delay over time
- Deliveries by shipment mode
- Total sales vs. average delay, by brand
- Top 5 average delivery delays by country and shipment mode
- Freight cost vs. shipment weight
- Weight and delay by shipment mode
- Sales distribution by shipment mode
- Filters: delivery date range, brand, shipment mode

**Key insights**
- Air Charter handles the heaviest shipments with the least delay and the highest sales.
- Ocean offers a balance between cost and weight capacity.
- Truck suits light, local deliveries with minimal delays.
- Air shipments show the highest delays despite lighter weights.
- Congo (DRC) and South Sudan have the longest delivery delays.
- Average delivery delay improved noticeably from 2011 onwards.

---

## Tools

- Power BI Desktop (DAX, data modelling)
- Python / Jupyter Notebook (data cleaning & EDA)

## Author

**Ibrahim Khalil Ahmad**
