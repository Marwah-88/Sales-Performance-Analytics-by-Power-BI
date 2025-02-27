# Sales-Performance-Project

### Power BI Dynamic Dashboard Link : https://app.powerbi.com/view?r=eyJrIjoiNGI3ZTcyNGYtYjI3Yy00MGQxLWIzNzUtMDlmOTgzMzAyNjcyIiwidCI6IjM0Y2JmYWYxLTY3YTYtNDc4MS1hOWNhLTUxNGViMjU1MGI2NiIsImMiOjN9

## Project Description:

This Power BI Sales Performance Dashboard provides a comprehensive analysis of sales performance, enabling businesses to track, evaluate, and optimize sales operations. It visualizes key metrics, including:

#### -Total Transactions – Number of completed sales.
#### -Total Quantity Sold – Total volume of products sold.
#### -Total Revenue – Overall sales revenue generated.

The dashboard includes interactive filters, allowing managers and supervisors to drill down into specific teams, analyze revenue contributions, and identify top and bottom performers.

## Key Features
- Revenue Breakdown: Analyzes revenue distribution by weekdays vs. weekends, sales channels, and managers to identify trends and sales patterns.

- Dynamic Sales Ranking: Highlights the top and lowest-performing sales representatives based on revenue and quantity sold.

- Dynamic Ranking: Enables users to filter and rank top/bottom performers by product name, product group, or salesperson for deeper performance analysis.

- Revenue vs. Budget Comparison: Visualizes revenue trends over time and evaluates performance against the allocated budget to assess goal achievement.

- Interactive Filters: Allows users to filter data by supervisors, managers, product categories, and sales channels for customized insights.

- Full Salesperson Transactional Details: Provides a granular breakdown of transactions, quantity sold, and revenue per salesperson for deeper performance insights.

## Use Cases
- Identify high-performing salespersons and recognize top contributors.

- Track total revenue trends and evaluate budget performance.

- Analyze sales distribution by product and region to optimize sales strategies.

- Compare weekday vs. weekend sales to adjust pricing and promotions.

- Enable managers to make data-driven decisions to improve sales efficiency.

## Insights
- Total revenue is 3.72% higher than the budget (rounded to 4%), indicating that the company exceeded its sales target, reflecting strong financial performance.

- Revenue consistently exceeded budget in most months, but some months show underperformance.

#### Sales Channel Performance
- Retail Channel leads with $9M (48.56%), making it the largest revenue contributor, indicating strong sales performance in physical locations.

- Distributor Channel follows, generating $6M (34.05%), showing a significant reliance on partnerships.

-Online Channel contributes $3M (17.39%), indicating room for growth in e-commerce.

#### Sales Team Performance
- Diego Araujo and Diogo Carvalho’s teams lead in revenue, contributing 35.26% and 34.05%, respectively.

- Carla Ferreira (Diego Araujo’s team) is the top performer, generating $4.7M in revenue and selling 1.64M units followed by Julio Lima (Diogo Carvalho’s team) with $3.3M in revenue and 1.16M units sold.

 - Gustavo Gomes (under Diogo Carvalho), despite generating $2.4M, has a high percentage of total quantity sold (12.43%) but lower total revenue compared to top performers. This suggests he might be selling at 

- Julieta Gomes and Isabella Sousa (under Emily Rocha) show minimal contributions to total revenue and units sold, indicating underperformance.

## Recommendations:
- Recognize and learn from top performers (Carla Ferreira, Julio Lima).

- Review pricing strategies for salespersons with high sales volume but low revenue.

- Provide training or support for underperforming team members to improve sales.

- Apply best practices from Diego Araujo and Diogo Carvalho’s teams across other teams.

- Analyze trends for underperforming months and adjust sales strategies accordingly (e.g., promotions, product focus).


  #### Optimize sales channels:
  - Retail Channel: Consider expanding operations or maintaining current strategies to sustain performance.
  
- Distributor Channel: Optimize partnership agreements and supply chain efficiency to maintain profitability.
  
- Online Channel: Invest in digital marketing, online promotions, or an improved e-commerce strategy to boost growth.

## Technical Details
- Data Source: Excel CSV files (Sales, Product, Budget, Photos)

- Tools Used: Power BI

- Data Processing: DAX for dynamic calculations and actionable insights

## Final Dashboard (snapshot)

This dashboard is a powerful tool for sales performance tracking and revenue optimization, offering actionable insights to drive business growth.

![Image](https://github.com/user-attachments/assets/d6665667-c68b-4f2e-8f2f-bc79197dc792)

![Image](https://github.com/user-attachments/assets/1d653603-a6ad-46e5-8a0a-f677ab6b25e0) 




## Step-by-Step Data Analysis & Visualization Process in Power BI
1. ### Data Cleaning & Preparation
- Imported CSV files into Power BI and verified data integrity by checking for missing values, anomalies, and consistency in data types and formats.
- Removed unnecessary top rows and promoted the first row as headers.

![Image](https://github.com/user-attachments/assets/c21eda1a-630a-4ef9-8f3a-d23b6910ef9b)




2. ### Data Transformation & Normalization
- Normalized the Sales Fact Table by separating salesperson details into an independent dimension (Dim_SalesPerson) for better relational modeling.

![Image](https://github.com/user-attachments/assets/1973327e-d0a6-4cf2-b1b1-09b1fccdca2c)
	
- Unpivoted the budget table’s month columns to create a normalized, date-based structure that integrates with the fact table, enabling better time-based analysis and reporting.


#### Table Before Unpivoting (Snapshot)

![Image](https://github.com/user-attachments/assets/cef69e3d-497a-4e67-a628-dd4075924dd5)



#### Table After Unpivoting (Snapshot)

![Image](https://github.com/user-attachments/assets/97bb69e0-b60e-4a6a-a8e5-333d24276f6d)

	
-  Merged Queries to denormalize tables by merging salesperson photos from the photo table into Dim_SalesPerson and product images into the product dimension table through a common key column, ensuring accurate record linking and data consistency.

![Image](https://github.com/user-attachments/assets/0e2c3652-ee53-4a04-888d-26d5087c915d)



3. ### Date Table & Model Relationships
- Created a Calendar Table to structure date values into Year, Quarter, Month, Week, and Day, supporting hierarchies and time intelligence functions (e.g., YTD, MTD, QTD).

             Calendar = ADDCOLUMNS(
             CALENDARAUTO(),
             "Year", YEAR([Date]),
             "Month",FORMAT([Date],"mmm"),
             "MonthNum",MONTH([Date]),
             "Weekday",FORMAT([Date],"ddd"),
             "WeekNum",WEEKDAY([Date]),
             "Qtr",FORMAT([Date],"\QQ"))

Additionally, a Weekend/Weekday column was added to classify each date based on the day of the week.
DAX Code for Weekend/Weekday Column:

       Weekend/Weekday = 
       IF('Calendar'[WeekNum] IN {1,7}, 
       "Weekend",
       "Weekday"
       )


#### The final output table displays the structured Calendar Table, including the newly added Weekend/Weekday classification.

![Image](https://github.com/user-attachments/assets/d080eeb6-75d2-44f1-89cd-ecf00403af6e)


- Managed and optimized relationships between all tables in Model View to ensure seamless filtering and accurate reporting.

![Image](https://github.com/user-attachments/assets/f8310e25-b7c6-409b-b659-633fe2242a8d)



4. ### Analyzing Data & Creating visuals
### To track key sales performance metrics, the following DAX measures were created:

- #### Total Transactions: Counts the number of sales transactions.

      #Transaction = COUNTROWS('Fact Table') 

- #### Total Quantity Sold: Sums up the total quantity of products sold

      Total Qty Sold = SUM('Fact Table'[Quantity])

- #### Total Revenue: Calculates revenue by multiplying unit price by quantity for each transaction.

      Total Revenue = SUMX('Fact Table','Fact Table'[UnitPrice] * 'Fact Table'[Quantity])

These measures provide insights into overall sales performance, allowing better tracking of revenue, transaction volume, and product sales trends.

#### To visually represent these key metrics, a card visual was used, as shown below:

![Image](https://github.com/user-attachments/assets/9fa3e646-94c8-4f9f-a675-a4f73138fc59)



- ### Created a Dynamic Filter & Slicer Based on Revenue combined with Dynamic Subtitle
#### To enable dynamic ranking based on revenue, the following steps were performed:
1.	Created a Numeric Range Parameter: Named Choose Rank to allow users to select ranking values.
2.	Created a Field Parameter: Named SelectToRank to allow dynamic ranking by Product, Product Group, or Salesperson.
3.	Inserted Data & Created a Supporting Table: Added two columns (Select, Sort) and named it Choose Ranking Type.

#### To make these three filters and slicers dynamic, the following Ranking DAX was implemented:

![Image](https://github.com/user-attachments/assets/6342af1d-24ac-405f-ae98-9b571f61b9ac)


#### To enhance these filters and slicer, a dynamic subtitle was created using the following DAX measure. This ensures that users can instantly read the selected ranking type, rank value, and category (Product Name, Product Group, or Salesperson) in the report.

![Image](https://github.com/user-attachments/assets/50c56b1d-61d8-4da0-9986-1263bd6c72c1)


This dynamic subtitle improves user experience by making the ranking selections more clear and interactive in Power BI visuals.


#### The final output, shown below, allows users to interactively filter rankings by Top/Bottom values across Product Name, Product Groups, or Salespersons:

![Image](https://github.com/user-attachments/assets/1d2e2921-f2e4-4a7b-815b-24d5ece2aa34)


#### Additionally, product tooltips were created to display detailed sales insights based on  Top/Bottom values across Product Name , Product Groups, or Salespersons:
- Total revenue breakdown by weekend vs. weekday sales.
- Percentage contribution of sales by time period.
- Product images for better visual representation.

#### Product Tooltip (snapshot)

![Image](https://github.com/user-attachments/assets/eaa6e1ee-818f-4a4c-a441-616344c5cc72)

- ### Salesperson Tooltip Ranking & Total Revenue by Channel Visualization

- #### Donut Chart used to filter revenue data by sales channel (Retail, Distributor, Online).

#### (Snapshot)

![Image](https://github.com/user-attachments/assets/bd66706c-e4ee-4cb8-ba01-a634402aa8c6)


#### Sales Person Tooltip to provide additional insights, a tooltip was implemented to display the top 3 salespersons by revenue for each channel.
To implement this tooltip:
- A multi-card visual was used to display the salesperson's name and total revenue.
- An image visual was added to show the salesperson's photo.

      The following DAX measure was applied as a visual-level     filter to dynamically rank salespersons based on revenue

#### Sales person tootip (snapshot)

![Image](https://github.com/user-attachments/assets/b66e1d15-b66d-41f6-8367-1c399faac92d)

This setup creates an interactive ranking visualization, providing a clear and dynamic view of the top-performing salespersons per channel.




- ### Total Revenue vs. Budget Tooltip & Visualization

![Image](https://github.com/user-attachments/assets/47ff4753-2364-42d1-982c-8efd938ccbec)

A line and stacked column chart was used to compare total revenue vs. total budget over time.
Color indicators:
- Blue bars show revenue above budget.
- Red bars show revenue below budget.
- The line represents the total budget for reference.

#### To enhance visualization, conditional formatting DAX was applied:


         Conditional Formatting 1 = 
         VAR _Revenue=[Total Revenue]
         VAR _Budget=[Total Budget]
         VAR _Result=
         SWITCH(
         TRUE(),
        _Revenue<_Budget,
        "#F12B30",
        "#033773"
        )

        RETURN
       _Result






- ### Revenue vs. Budget Tooltip
To provide additional insights, a tooltip was implemented to display:
- A visual card showing Total Transactions, Total Revenue, Total Budget, and Revenue from Budget.
- A gauge visual to indicate the performance status of each month.

#### Total vs Budget tooltip

![Image](https://github.com/user-attachments/assets/b5f88ed6-61ca-407f-928f-4cf290ec210d)


This setup allows users to quickly identify whether the business is performing above or below budget targets each month.





- ### Matrix Visualization


![Image](https://github.com/user-attachments/assets/78baa123-ce64-4452-92dd-c3074311fb7c)

This matrix visual presents a hierarchical breakdown of total revenue and total quantity sold, grouped by supervisors and their sales teams. It allows for an easy comparison of sales performance across different levels.

#### Conditional Formatting:
- Blue bars represent higher performance, showing strong contributions in revenue and sales volume.
- Red-shaded values indicate lower performance, helping to quickly identify underperforming salespersons who may need attention.
#### Total Row:

The Total row summarizes revenue and sales quantity across all supervisors and salespersons, showing that the company has achieved $17.9M in total revenue and 6.38M in total quantity sold in selected year



- ### Table Visualization 

![Image](https://github.com/user-attachments/assets/d7cca406-1153-4107-8e50-51516c07793d)

This visual presents salesperson details along with their profile pictures for better identification. It provides key sales performance metrics, including:
- Total Transactions – Number of completed sales per salesperson.
- Total Quantity Sold – Total units sold by each salesperson.
- Total Revenue – Total revenue generated per salesperson.

To enhance readability, Conditional Formatting is used to apply color intensity, making it easier to identify high-performing and low-performing salespersons at a glance.

Additionally, this visual includes Interactive Filters for Managers and Supervisors, allowing users to filter and analyze performance under different leadership structures.

This interactive and visually enhanced report enables businesses to evaluate individual sales performance, identify top performers, and assess areas needing improvement efficiently.





