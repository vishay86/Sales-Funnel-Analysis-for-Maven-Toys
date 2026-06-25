# Sales Funnel Analysis for Maven Toys

### Project Background

Maven Toys is an e-commerce store around 3 years old (2012-2015). The company sells plush toys globally via their website.

The company has significant amounts of data on its sales, marketing efforts, orders and returns that have been previously underutilized. This project thoroughly analyzes and synthizes this data to uncover critical insights that will improve Maven Toy’s commercial success.

Insights and recommendations are provided in the following key areas:

- **Sales Trend Analysis**: Evaluation of historical sales patterns, focusing on quarterly sales and Average Order Value (AOV)

- **Marketing Channel Analysis**: An in-depth analysis of which marketing channels are driving the most orders and to establish a competitive Customer Acquisition Cost (CAC)


### Data Structure & Intial Steps
Maven Toys database structure as seen below consists of six tables: orders, order_items, order_items_refunds, products, website_sessions, website_pageviews. A total of over 1.1 million rows

<img width="835" height="458" alt="image" src="https://github.com/user-attachments/assets/f9157103-e5ab-4c5b-b8d6-055a2514ec23" />



Prior to beginning the analysis, a variety of checks were conducted for quality control and familiarization with the datasets.


### Executive Summary
Sales since the company's inception have exploded every quarter over the past three years. We have seen an increase in orders from 60 in Q1 2012 to 5420 orders in Q1 2015 (⬆️8,900%)

###
###
###


## My Analysis

  
### Step 1: Identify what the current sales funnel looks like

I used SQL CTE's to create the sales funnel. I used the webpage_url in a CASE statement to get a list that would reiterate thru the whole webpage_pageviews table and give me a COUNT for each pageview_url

SQL Code can be found here

| stage1_home | stage2_products | stage3_cart | stage4_shipping | stage5_billing | stage6_thank_you_order |
| --- | --- | --- | ---| ---| ---|
| 472,871 | 261,231 | 94,953 | 64,484 | 52,058 | 32,313 |

### Step 2: Get the conversion rates

I decided to convert the total website_sessions for each stage into conversion rates (%) to better understand how our customers were flowing thru the funnel and where the drop-off's were.

SQL Code can be found here

|home_to_products_conv_rate | products_to_cart_conv_rate | cart_to_shipping_conv_rate | shipping_to_billing_conv_rate | billing_to_order_conv_rate | overall_conv_rate|
| --- | --- | --- | ---| ---| ---|
| 55.24 | 36.35 | 67.91 | 80.73 | 62.07 | 6.83 |

### 🔍 Findings: 
There seems to be a massive 64% drop off from customers viewing the products page to adding anything to their cart. This drop off indicates that they possibly could be having a hard time finding what they are looking for, so they are abandoning the website and looking elsewhere. 

### 🗒️ Recommendations: 
Our main priority at the moment should be to look into bettering the website experience. Possibly better product listings and banner placements could improve the customer's search experience and lead to more products being added to the cart.
