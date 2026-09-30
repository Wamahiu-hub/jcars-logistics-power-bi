# jcars-logistics-power-bi
Data cleanup assignment
# JCars Logistics — Power BI Business Intelligence Project

## Status: Partial Submission
Due to time constraints, this submission covers data cleaning and a minimal 
executive dashboard. Full detailed report pages, complete DAX measure set, 
interactivity features (drill-through, tooltips), and the Dev.to article 
were not completed by the deadline.

## Project Objective
Transform JCars Logistics' raw vehicle sales dataset into a reliable Power BI 
solution for management reporting on sales, profitability, and operations.

## Dataset
276 rows, one row = one vehicle sales order line item.

## Data Quality Issues Identified and Handled
1. Order ID — inconsistent formats across prefixes (LC/LCL/ORD/CAR); 19 rows 
   missing entirely; 3 IDs reused across different transactions. Standardized 
   to a numeric Order Key; original IDs retained; reused/missing IDs flagged, 
   not deleted.
2. Order Date / Delivery Date — 4+ mixed date formats, Excel serial numbers, 
   and one impossible date (month 13). Parsed into consistent Date type.
3. Delivery Before Order Flag — 16 of 276 rows show delivery date earlier 
   than order date (physically impossible). Flagged for investigation, not 
   deleted, since underlying revenue may still be valid.
4. Region, County, Customer Type, Payment Method, Payment Status, Delivery 
   Status, Fuel Type, Transmission, Lead Source, Vehicle Type — all had 
   case inconsistencies, abbreviations, and spelling variants, standardized 
   via mapping tables (e.g. "PMS" → Petrol, "NRB" → Nairobi).
5. Car Make / Car Model — typos and casing variants standardized 
   (e.g. "Toyta" → Toyota); distinct similar-sounding models kept separate 
   where they are genuinely different vehicles (e.g. Axela vs Axio).
6. Sales Rep / Customer Name — corrupted text with digits substituted for 
   letters (e.g. "Dan1El" → "Daniel"), corrected and case-normalized.
7. Customer Age, Vehicle Year, Units Sold, Discount, Customer Rating — mixed 
   text/numeric representations (e.g. "thirty", "two", "4.5 out of 5") 
   parsed into consistent numeric types.
8. Monetary fields — mixed currencies (KSh, KES, USD, an unlabeled symbol 
   treated as USD) and formats (abbreviated millions, error strings). 
   Standardized to KES.

## Currency Standardization
All monetary values converted to KES. Unlabeled values assumed KES per 
assessment instructions. Exchange rate used: **1 USD = 130 KES** (documented 
assumption; source: approximate market rate at time of analysis).

## Data Model
Single cleaned fact table (`Sales`) derived from raw staging table 
(`Sales_Raw`), retained for traceability. [Add model screenshot]

## Key Measures
- Total Revenue
- Total Units Sold  
- Gross Profit

## Executive Dashboard
One-page overview: KPI cards (Revenue, Units Sold, Gross Profit), 
revenue by region, revenue by payment status, revenue by car make.

## Not Completed (time constraints)
- Detailed multi-page report
- Drill-through, tooltips, full interactivity
- Full DAX measure set (time-based, ranking, ratio calculations)
- Analyst-defined business questions
- Written insights and recommendations
- Dev.to technical article
