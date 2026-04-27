# Super Store Data Set

## Slide 1

![image1.png](<images/Super Store Data Set/image1.png>)

Superstore Sales Hypothesis Testing

Presented By:

Vishal Kumar  Nalluri

Date:04/02/2025  

![image1.png](<images/Super Store Data Set/image1.png>)

Task Completed and Deliverables

| Name | Completed  | Deliverables |
|----|----|----|
| Rakesh  |                   100% | Report for PMO by using PBI , Adobe  Xdm  and salesforce Presentation |
| Khader |                   100% | Hypothesis Testing , Netflix Dash Board  |
| Aravinth |                   100% | SQL ER  Diag  , DDL scripted  |
|  |  |  |

![image1.png](<images/Super Store Data Set/image1.png>)

Introduction & Objective

This analysis focuses on the  Superstore dataset  to identify  sales patterns, product profitability, customer behavior, and segment performance . Using  statistical analysis and hypothesis testing , we aim to uncover key insights that can help improve business decision-making and drive better strategies.

  Key Insights Addressed:

Which month has the highest number of sales?

Which product has the highest profit?

 Do high-value orders prefer faster shipping?

Which cities have high revenue but low profit margins?

Do different segments respond differently to discounts?

![image1.png](<images/Super Store Data Set/image1.png>)

Super   Store Raw Cleansed Data Set 

![image1.png](<images/Super Store Data Set/image1.png>)

Data Analysis & Hypothesis Testing

1.  Which month has the highest number of sales? Tool: Excel (Pivot Table) H₀: Sales are equal across all months. H₁: At least one month has significantly different sales. ANOVA Single factor: Analysis of Variance.

Total Sum Of Sales for each Month of 2024

![image1.png](<images/Super Store Data Set/image1.png>)

Data Analysis & Hypothesis Testing

2. Which product has the highest profit? Method:

- Grouped profits by Product Name
- ANOVA

![image1.png](<images/Super Store Data Set/image1.png>)

Data Analysis & Hypothesis Testing

3. Do high-value orders prefer faster shipping?

Method:

- Classified orders as High/Low based on median Sales
- Used Chi-Square Test in Python

![image1.png](<images/Super Store Data Set/image1.png>)

4. Which cities have high revenue but low profit margins?

Method:

- Identified top cities by revenue
- Calculated average profit margins
- Used ANOVA to test for significance

![image1.png](<images/Super Store Data Set/image1.png>)

5.Do different segments respond differently to discounts?

Method:

- Grouped discount data by segment
- ANOVA test

![image1.png](<images/Super Store Data Set/image1.png>)

1. Monthly Sales Trend

Sales significantly vary across months. November, December, and September showed peak performance (Confirmed by ANOVA test).

2. Product Profitability

Profitability differs by product.  Canon  imageCLASS  2200 Advanced Copier  is the most profitable product (ANOVA confirmed).

3. High-Value Orders & Shipping

Customers  do not prefer  faster shipping methods for high-value orders (Chi-Square Test, P-value \> 0.05).

4. City Revenue vs. Profit Margins

Cities like  Chicago  and  Houston  have high sales but negative profit margins, indicating inefficiency or high costs.

5. Segment-wise Discount Response

No statistically significant difference in discount response among Consumer, Corporate, and Home Office segments.

Conclusion:

![image1.png](<images/Super Store Data Set/image1.png>)

Questions?

![image1.png](<images/Super Store Data Set/image1.png>)

![image1.png](<images/Super Store Data Set/image1.png>)

| Groups    | Count | Sum      | Average  | Variance |
|-----------|-------|----------|----------|----------|
|  January  | 24    | 44259.21 | 1844.134 | 2762126  |
| February  | 20    | 20301.13 | 1015.057 | 760657.4 |
| March     | 28    | 60728.48 | 2168.874 | 8339318  |
| April     | 27    | 36779.04 | 1362.187 | 2513145  |
| May       | 27    | 45155.48 | 1672.425 | 2165215  |
| June      | 26    | 53056.08 | 2040.618 | 2357296  |
| July      | 29    | 45989.5  | 1585.845 | 2035487  |
| August    | 28    | 64129.76 | 2290.349 | 6982869  |
| September | 28    | 88064.53 | 3145.162 | 7300017  |
| October   | 28    | 83474.78 | 2981.242 | 13531442 |
| November  | 30    | 117910.1 | 3930.338 | 9662778  |
| December  | 29    | 85072.7  | 2933.541 | 6424776  |
| Groups    | Count | Sum      | Average  | Variance |

| Source of Variation | SS           | df  | MS       | F        | P-value  | F crit   |
|---------------------|--------------|-----|----------|----------|----------|----------|
| Between Groups      | 213787757\.8 | 11  | 19435251 | 3.461452 | 0.000143 | 1.819406 |
| Within Groups       | 1751807496   | 312 | 5614768  |          |          |          |
|                     |              |     |          |          |          |          |
| Total               | 1965595253   | 323 |          |          |          |          |

| SUMMARY |
|---------|

| ANOVA SINGLE FACTOR  |
|----------------------|

| P-Value = 0.00143 \< 0.05 →reject H₀ F-Statistic \<  F crit  →  3.461\> 1.819 |
|----|

Appendix:1
