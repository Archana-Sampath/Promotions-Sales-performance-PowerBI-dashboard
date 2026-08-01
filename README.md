**AtliQ Mart--Promotion Effectiveness & Revenue Analysis**

**Domain**: FMCG **Function:** Sales & Promotions

An interactive PowerBI dashboard analysing Promotional campaigns, Sales and Revenue from the dataset. This dashboard provides key insights on how different promo types (percentage discounts, flat cashback, and BOGOF) actually impact revenue and sales. helping the business make informed decisions for their next promotional period.

**Project Overview:**

AtliQ Mart is a retail giant with over 50 supermarkets in the southern region of India. All their 50 stores ran a massive promotion during the Diwali 2023 and Sankranti 2024 (festive time in India) on their AtliQ branded products. Now the sales director wants to understand which promotions did well and which did not so that they can make informed decisions for their next promotional period.

**Objectives:**

The business ran five promo types - 25% OFF, 33% OFF, 50% OFF, 500 Cashback, and BOGOF (Buy One Get One Free) - across multiple product categories and campaigns, and needed to know

- Store Performance Analysis- How stores performed across the promotional period.
- Promotions Analysis- measure the effectiveness of promo types in terms of Incremental revenue(IR) and Incremental units sold(ISU)
- Product & category analysis- Which product categories and individual products responded well to the promotions

**Tools Used:**

| Microsoft Power BI | Dashboard development & visualization |
| ------------------ | ------------------------------------- |
| Power Query        | Data cleaning & Transformation        |
| DAX                | Business KPI's                        |
| CSV                | Source Dataset                        |
| MySQL              | SQL based report generation           |

**Dataset:**

The dataset contains 4 CSV files:

| **File**          | **Description**                                                                                                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **fact_events**   | **1,500 transaction-level rows -Base price,** **promo_type,** **quantity_sold(before_promo),** **quantity_sold(after_promo) including foreign keys for campaigns, products and stores** |
| **dim_campaigns** | **Campaign details - campaign_id,campaign_name (e.g., Diwali, Sankranti),Start date ,End date.**                                                                                        |
| **dim_products**  | **Product-level attributes - product_name, category,product_code**                                                                                                                      |
| **dim_stores**    | **Store-level details - store ID, city**                                                                                                                                                |

**Data Transformation**

- Promoted headers
- Converted date fields into Date format
- Created discounted_price custom column
- Converted discounted_price and Revenue into Decimal format
- Assigned proper numeric data types
- Created custom columns for enhanced reporting

**Data Modeling:**

The data model follows a star schema, with **fact_events** as the central fact table connected to three dimension tables:

- **dim_products** (dimension) - **product_code**
- **dim_campaigns** (dimension) - **campaign_id**
- **dim_stores** (dimension) - store_id
- **fact_events** (fact table) - transaction-level records, joined to each dimension table via foreign keys (**product_code, campaign_id, store_id)**

**Key Calculations:**

Discounted price (Power Query)

Each promo type requires a different logic -a flat % cut(25%,33%,50%), a cashback(500 cashback) and BOGOF(Buy one get one free).

For BOGOF, considered quantity_sold(after_promo) as total units shipped including paid+free, so revenue for BOGOF is calculated by rounding the quantity up and dividing by 2 ,to get the actual number of paid units. For example, the quantity sold(after_promo) is 79, dividing by 2 gives 39.5, which rounds up to 40 - meaning 40 units were paid for and 39 were given free.

**Measures:**

- **Revenue(before_promo)**
- **Revenue(after_promo)**
- **Quantity sold(before_promo)**
- **Quantity sold(after_promo)**
- **Incremental Revenue(IR)**
- **Incremental units sold(ISU)**

**Dashboard preview- Store Analysis**
### Store Analysis
![Store Analysis Dashboard](assets/store_analysis_dashboard.png)

### Promotion Analysis
![Promotion Analysis Dashboard](assets/promotion_analysis_dashboard.png)

### Product & Category Analysis
![Product & Category Analysis Dashboard](assets/product_category_dashboard.png)

### Business Insights & Impact
### Store Performance Analysis -

- **Store "STMYS-1" in Mysuru performed exceptionally well during promotional period  achieving  an Incremental Revenue of "3.64M" ,followed by STCHE-4 in Chennai  with an Incremental Revenue  of  "3.54M"**.
- **Store "STMLR-0" in Mangalore underperformed during the promotional period, selling only  1952 items .This is  followed by stores STVSK-3 & STVSK- 4  in Visakhapatnam  which also  recorded low sales**.
- **Bengaluru , Chennai & Hyderabad recorded highest promotional revenue among all cities, generating  26.76M , 21.18M & 15.25M respectively**.
- **Mangalore, Vijayawada & Trivandrum recorded lowest promotional revenue among all cities, generating  3.37M , 2.86M & 2.35M respectively**.

Insights: 
- **Top performing cities have higher number of operational stores compared to  underperforming cities, which could a factor for their strong promotional performance**.

### Promotion Type Analysis -

- **The Diwali Campaign performed exceptionally well ,generating 106.32M revenue during promotional period**.
- **The Top two Promotions by revenue are 500 cashback, which generated  " 91.05M" followed by BOGOF with "21.77M" in revenue**.
- **The Bottom two promotions by units sold  during promotional period were"50% off" , with  6,931 units sold , and "25% off" which recorded  negative value of 5,717 units , indicating the number of units sold during promotions are lower than the number of units sold before promotion**.

Insights: 
 - **The Discount based promotions (25% off ,33% off ,50% off ) generated a negative net revenue of "-5.46M" , while BOGOF are 500 cashback promotions delivered stronger results , with revenue nearly doubled**.


### Product & Category Analysis -

 - **Combo1 saw the most significant lift in sales during promotional period making an revenue of '$157.95M" with an incremental revenue of  "$91.05M" followed by Home appliances generating a incremental revenue of "$7.87M". Personal care category is losing its revenue with IR of "-0.85M" marking it as underperforming category during promotional period**.
 - **Based on the correlation matrix , its hard to determine which promotion  performed well across the product categories because  the promotional offers are not evenly distributed . For example, top performing promotions "500 cashback" and "BOGOF" were never offered for  "Personal care" category. Similarly  "Combo1" category was promoted with the "500 cashback" offer and was not given any discount based promotions(25% off,33% off or 50% off).As a result , the uneven distribution of  promotional offers across product categories limits the ability to compare promotion effectiveness by product category**.

### Recommendations for Next promotional Period-

 - **Prioritize "500 cashback" and "BOGOF" as they delivered highest incremental value and strong sales performance**.
 - **The promotions based on discounts(25% off, 33% off, & 50% off) should be redesigned with new strategy  and tested across various range of products to evaluate their effectiveness. If the performance is not improved,  replace with loyalty reward program where points earned are redeemed later for discounts or free products**.
 - **Before finalizing the future promotional strategies , each promotion type should be evenly distributed to broader range of products and tested for the  effectiveness. The uneven distribution of promotions in the current campaign caused the limitation to determine whether the performance were driven by the promotion or the categories to which it is applied**.

**Dashboard Features:**

- **KPI Cards**
- **Interactive Slicers and Filters**
- **Revenue Analysis**
- **Product and Category Analysis**
- **Promotion Analysis**
- **Product Category and Promotion Analysis**
- **Performance of stores by City**
- **Dynamic charts**
- **Recommended Insights**
