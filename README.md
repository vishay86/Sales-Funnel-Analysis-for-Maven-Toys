# Sales Funnel Analysis for Maven Toys

### Project Background

Maven Toys is an e-commerce store around 3 years old (2012-2015). The company sells plush toys globally via their website.

The company has significant amounts of data on its sales, marketing efforts, orders and returns that have been previously underutilized. This project thoroughly analyzes and synthizes this data to uncover critical insights that will improve Maven Toy’s commercial success.

Insights and recommendations are provided in the following key areas:

- **Sales Trend Analysis**: Evaluation of historical sales patterns, focusing on quarterly sales and Average Order Value (AOV)

- **Marketing Channel Analysis**: An in-depth analysis of which marketing channels are driving the most orders and to establish a competitive Customer Acquisition Cost (CAC)


## Executive Summary
This analysis of the toys e-commerce store reveals two key areas of focus: website conversion performance and marketing channel effectiveness. While the business has successfully grown its order volume across all marketing channels from 2012 to 2015, the website's sales funnel exposes a critical bottleneck — only 36% of customers who visit the products page proceed to add items to their cart, resulting in a modest overall conversion rate of just 6.83%. Addressing this drop-off represents the single highest-leverage opportunity to increase revenue without requiring additional marketing spend.

### Key Issues

The products-to-cart stage has the steepest drop-off in the entire funnel at 64%, suggesting friction in the product discovery and browsing experience that is causing customers to look elsewhere.
Despite strong traffic driven primarily by gsearch_nonbrand_orders, the business remains heavily reliant on a single paid channel, creating risk if Google search costs rise or campaign performance shifts.


### Recommendations

Prioritize a UX audit of the products page, focusing on improving product listings, search functionality, filtering options, and banner placements to reduce cart abandonment and improve the products-to-cart conversion rate.
Invest in scaling bsearch_nonbrand (Bing), organic search, and direct channels to further reduce paid traffic dependency — a trend already moving in the right direction, with the paid-to-free order ratio improving from 6:1 to 2:1 between 2012 and 2015.
Conduct a cost-per-acquisition analysis across all channels to ensure marketing budget is being allocated where it generates the highest return, particularly ahead of Q4 when order volumes peak across the board.




###
###
###


## My Analysis

### Data Structure & Intial Steps
Maven Toys database structure as seen below consists of six tables: orders, order_items, order_items_refunds, products, website_sessions, website_pageviews. A total of over 1.1 million rows

<img width="835" height="458" alt="image" src="https://github.com/user-attachments/assets/f9157103-e5ab-4c5b-b8d6-055a2514ec23" />



*Prior to beginning the analysis, a variety of checks were conducted for quality control and familiarization with the datasets.


  
### Step 1: Identify what the current sales funnel looks like

I used SQL CTE's to create the sales funnel. I used the webpage_url in a CASE statement to get a list that would reiterate thru the whole webpage_pageviews table and give me a COUNT for each pageview_url

SQL Code can be found here: https://github.com/vishay86/Sales-Funnel-Analysis-for-Maven-Toys/blob/main/SQL%20Analysis

| stage1_home | stage2_products | stage3_cart | stage4_shipping | stage5_billing | stage6_thank_you_order |
| --- | --- | --- | ---| ---| ---|
| 472,871 | 261,231 | 94,953 | 64,484 | 52,058 | 32,313 |

### Step 2: Get the conversion rates

I decided to convert the total website_sessions for each stage into conversion rates (%) to better understand how our customers were flowing thru the funnel and where the drop-off's were.

SQL Code can be found here: https://github.com/vishay86/Sales-Funnel-Analysis-for-Maven-Toys/blob/main/SQL%20Analysis

|home_to_products_conv_rate | products_to_cart_conv_rate | cart_to_shipping_conv_rate | shipping_to_billing_conv_rate | billing_to_order_conv_rate | overall_conv_rate|
| --- | --- | --- | ---| ---| ---|
| 55.24 | 36.35 | 67.91 | 80.73 | 62.07 | 6.83 |

### 🔍 Findings: 
There seems to be a massive 64% drop off from customers viewing the products page to adding anything to their cart. This drop off indicates that they possibly could be having a hard time finding what they are looking for, so they are abandoning the website and looking elsewhere. 

### 🗒️ Recommendations: 
Our main priority at the moment should be to look into bettering the website experience. Possibly better product listings and banner placements could improve the customer's search experience and lead to more products being added to the cart.

### Step 3: Identify number of orders for each marketing channel
In order to better under understand what is currently working in terms of customer acquisition and to better inform budget allocation, I decided to deep dive into our orders data to understand what marketing channels were bringing in the most number of orders.

SQL Code can be found here: https://github.com/vishay86/Sales-Funnel-Analysis-for-Maven-Toys/blob/main/SQL%20Analysis

| Year | Quarter | gsearch_nonbrand_orders | bsearch_nonbrand_orders | brand_search_orders | organic_search_orders | direct_type_in_orders |
|------|---------|------------------------|------------------------|--------------------|-----------------------|----------------------|
| 2012 | Q1 | 60 | 0 | 0 | 0 | 0 |
| 2012 | Q2 | 291 | 0 | 20 | 15 | 21 |
| 2012 | Q3 | 482 | 82 | 48 | 40 | 32 |
| 2012 | Q4 | 913 | 311 | 88 | 94 | 89 |
| 2013 | Q1 | 766 | 183 | 108 | 125 | 91 |
| 2013 | Q2 | 1,114 | 237 | 113 | 134 | 119 |
| 2013 | Q3 | 1,132 | 245 | 154 | 167 | 143 |
| 2013 | Q4 | 1,657 | 291 | 248 | 223 | 197 |
| 2014 | Q1 | 1,667 | 344 | 354 | 338 | 311 |
| 2014 | Q2 | 2,208 | 427 | 410 | 436 | 367 |
| 2014 | Q3 | 2,259 | 434 | 432 | 445 | 402 |
| 2014 | Q4 | 3,248 | 683 | 615 | 605 | 532 |
| 2015 | Q1 | 3,025 | 581 | 622 | 640 | 552 |

### 🔍 Findings: 
Brand search picking up significantly from 0 to 600+ orders in three years means our brand is top of mind for the consumer on their product search journey. 
Seeing similar growth for our organic search and direct type in orders, also helps signify that our brand recognition is growing. 

The orders generated from these three channels have grown from an approximate ratio of  6 to 1 (paid vs free channels) to now being around 2 to 1 by the beginning of 2015. This is an indication that the business has become much less dependent on paid traffic and that our previous marketing spend has lead to an increase in significant brand value.


### 🗒️ Recommendations: 
Given gsearch nonbrand's outsized contribution to orders, the business should prioritize continued investment in Google Search campaigns — particularly in Q4, where order volumes spike across all channels likely due to holiday toy demand. Diversification efforts should focus on scaling bsearch_nonbrand_orders (Bing) and organic_search_orders, as both show promising upward trends and could reduce over-reliance on a single channel. Additionally, a deeper dive into conversion rates and customer acquisition costs per channel would help determine where incremental budget increases would yield the highest return on investment.
