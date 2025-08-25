# Blinkit Power BI Dashboard

*Interactive Power BI dashboard for analyzing Blinkit sales, assortment, outlet performance and customer ratings.*

## Business objectives

- *Goal :* Boost revenue and customer satisfaction by identifying high-impact products, product attributes, and outlet segments.

- *Key questions*

    - Which SKUs/categories drive the most revenue?
    - How do product attributes (e.g., fat content) perform by outlet and location?
    - Which outlets are most efficient (sales, visibility, ratings)?
    - Are there time/cohort trends in outlet performance?
    - Where can visibility, assortment, or service changes raise revenue?

## Key Metrics & Definitions

  - Total Sales: Net revenue (Price × Quantity, net of refunds).
  - Avg Sales: Average revenue per transaction (or per sale unit depending on your data model).
  - No. of Items: Distinct SKUs present in the sales data.
  - Avg Rating: Mean customer rating for sold items (ratings should be linked to transactions).
  - Item Visibility: App/shelf visibility metric (e.g., impressions, featured count — define per  data source).
  - Outlet Size / Type / Location Tier: Business-defined outlet attributes used for segmentation.

## Recommended DAX Measures

    -- Total Sales
    Total Sales = SUM(Sales[Revenue])
    
    -- Transactions
    Transactions = DISTINCTCOUNT(Sales[TransactionID])
    
    -- Avg Sales per Transaction
    Avg Sales per Transaction = DIVIDE([Total Sales], [Transactions], 0)
    
    -- Distinct Items Sold
    Distinct Items Sold = DISTINCTCOUNT(Sales[ItemID])
    
    -- Average Rating (filtered to sold items)
    Average Rating = AVERAGE(Feedback[Rating])
    
    -- Sales Rolling 3 Months
    Sales Rolling 3M =
    CALCULATE([Total Sales], DATESINPERIOD(Calendar[Date], LASTDATE(Calendar[Date]), -3, MONTH))

## Typical Insights & Recommended Actions

  - Pareto SKU focus: If ~20% SKUs produce ~80% revenue → prioritize these SKUs for stock & promotions; rationalize the long tail.
  - Rating mismatch: High sales + low ratings → investigate product quality, packaging or fulfillment issues at the outlet level.
  - Visibility uplift: Low visibility + low sales → run placement/promotional tests and measure lift.
  - Outlet optimization: Normalize by outlet size (sales / outlet or sales / area) to identify high-efficiency outlets and re-evaluate cost-to-serve for low-performers.

## Example

Preview image of dashboard (<img width="1421" height="771" alt="Blinkit_Analysis" src="https://github.com/user-attachments/assets/faadf49f-dcbf-474a-8892-90b6281a6dc9" />)

## Conclusion 

This dashboard turns sales, assortment, outlet and rating data into clear, actionable insights — prioritize top SKUs, tailor assortments by outlet, and run visibility/quality experiments to drive revenue and satisfaction.




