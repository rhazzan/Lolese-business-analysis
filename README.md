# Lolese-business-analysis
This project applies data analysis techniques to uncover business insights, optimize operations, and support data-driven decision-making aimed at improving sales performance.
## Overview
Olawale Rabiu is the owner of a medium-sized enterprise that provides rental services for chairs, canopies, drums, and related items. Like many business owners, he aims to maximize profit and optimize operations. The challenge, however, was that he had no clear understanding of how his business had performed in previous years and needed clarity to make informed decisions.

Recognizing the risks of operating without proper insight, I offered to conduct a comprehensive analysis for him to give him a full understanding of his business performance. I collected his hard-copy record book, converted it into a digital format to enable efficient analysis, and cleaned the data to prepare it for detailed evaluation. I then performed a full analysis to help him understand the true state and trends of his business.

After reviewing the dashboard and report I created, he was able to make informed decisions that improved his operational performance and increased sales by 10% within a month. He also mentioned that the decision he had been planning to make before receiving the dashboard and report could have severely harmed his business, but he was grateful that he chose to act on the insights provided.
## Tools Used
- Data Preparation:
  - Excel VBA - Data Inputing
  - Microsoft Excel - Data Storage
  - Power Query - Data Cleaning
- Data Modeling & Visualization:
  - DAX - Data Analysis
  - Power BI - Data Modelling and Visualisation
## Data Cleaning and Preparation
- Converted hard-copy records to digital format (Excel).
- Standardized date formats (dd/mm/yyyy).
- Removed duplicates using Excel and Power Query.
- Corrected inconsistent item names (e.g., “Chairr”, “Chair”, “Chairs” → “Chair”).
- Filled missing values where possible or tagged them as Null.
- Created new calculated fields (e.g., revenue, transaction category).
- Applied data validation rules to prevent future errors.
- Cleaned whitespace and formatting issues.
! [Data Ccleaning Process]("C:\Users\PC\Pictures\Screenshots\Screenshot-2025-12-11-103659.png")
<!-- <img width="492" height="147" alt="Image" src="https://github.com/user-attachments/assets/fbda187f-34c0-48ca-a028-c1c12cdeb764" /> -->
<p align="center">
  <img  width="1800" height="147" alt="Image" src="https://github.com/user-attachments/assets/fbda187f-34c0-48ca-a028-c1c12cdeb764">
  <img width="1862" height="714" alt="Image" src="https://github.com/user-attachments/assets/1c1f3ea9-5f1b-46cd-ac64-fec3ead664fe" />
  <img width="1808" height="969" alt="Image" src="https://github.com/user-attachments/assets/91c1bd9b-9fe4-4786-8f37-f0db57fae68c" />
</p>
## Exploratory Data Analysis

```python
Total Sales = SUMX(DISTINCT('Order Data'[OrderID]),CALCULATE(MAX('Order Data'[Deposit])))
Total Quantity = CALCULATE(SUM('Order Data'[Quantity]))
Total Charity= CALCULATE(DISTINCTCOUNT('Order Data'[OrderID]),FILTER('Order Data','Order Data'[Amount] = 0 && 'Order Data'[Deposit] = 0))
Total Orders = DISTINCTCOUNT('Order Data'[OrderID])
```
```python
Top Customers = 
VAR _Ranked =
            IF(ISINSCOPE('Order Data'[Name]),RANKX(ALL('Order Data'[Name]),[Total Sales],,DESC))
RETURN IF(_Ranked <= 5,[Total Sales])
```
```python
Average Order Value = DIVIDE([Total Sales],[Number of Orders])
```
```python
Parameter Dax = SWITCH(SELECTEDVALUE(Parameter[Parameter]),
                        "Total Sales",SUMX(DISTINCT('Order Data'[OrderID]),CALCULATE(MAX('Order Data'[Deposit]))),
                        "Number of Orders",DISTINCTCOUNT('Order Data'[OrderID]),0)
```

## Insights and Recommendations
1.Orders Overview
- From January to 10th August 2025, total revenue amounted to ₦4.35 million across 133 orders, with an average order value of ₦32.7k. Some supplies were given out for charity, which reduced total collected revenue.
2. Customer & Category Insights
- Rental-to-Rental orders made up 18% of orders but only 11% of revenue, meaning volume is high but revenue contribution is low. Profit cannot be fully evaluated yet due to missing cost data, but these orders might have higher margins because they usually require no transport or labour.
- The Oreagba family contributed 14% of revenue, making them a key customer worth retaining.
-	Most customers are one-time customers; the most frequent customer only returned four times.
3. Seasonal & Monthly Trends
-	February recorded the highest number of orders, many booked in advance for June (Eid-ul-Adha), showing strong advance-payment behaviour which could support cash flow.
-	Revenue peaked in February (by order date) and again in June (by usage date).
-	Orders declined after February, rose in June, and declined again afterward.
4. Product Performance
-	Chairs dominated, generating ₦3M+ and 103 orders.
-	Next best:
    -	Royal Festival items
    -	Plastic Tables with Covers
- Larger tents (300–600 guest sizes) had the lowest demand.
5. Monthly Customer Breakdown
-	February major customers: Sunday, Mum Nurse, Tele (G.R.A), Oil Osinubi, Oreagba.
-	June major customers: Uncle Sarafa Sule, Igbo Wife Osinubi, Progressive Rental, Oreagba, Bonojo Gen.

Recommendations
1. Strengthen key customer relationships
-	Offer loyalty benefits or small discounts to top customers like the Oreagba family to maintain long-term patronage.
2. Re-evaluate pricing for Rental-to-Rental
-	Since this category brings many orders but low revenue, consider:
-	minimum charges, service fees, or a different price structure after reviewing full cost and profit data.
3. Use advance bookings better
-	Encourage early payments and deposits since many customers book several months ahead. This can support cash flow and inventory planning.
4. Focus on high-demand products
-	Chairs and Royal Festival items consistently perform well. Stock more of them and use targeted promotions.
5. Adjust inventory for low-demand tents
-	Consider reducing investment in large tents or switching to renting instead of owning them.
6. Improve customer retention
-	Most customers don’t return, so introduce referral bonuses, follow-ups, or seasonal reminders through WhatsApp or SMS.

7. Collect more data
-	Add cost, labour and transport data to help identify the most profitable products—not only those with the highest revenue.
