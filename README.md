# Project-1-Air-Quality-Index

### Dashboard Link : https://app.powerbi.com/groups/me/reports/fc902282-5852-43c8-a2a8-695c4be5d4f0/ReportSection?experience=power-bi
## Problem Statement

The sales department of the company lacks clear insights into key performance metrics such as total revenue, quantity sold, top customers, and top-selling products across 
different markets. Without this data being effectively visualized, it becomes challenging to identify trends, areas of growth, and potential issues. The goal is to create 
an interactive Power BI dashboard that provides a comprehensive view of these sales metrics, allowing stakeholders to make data-driven decisions and enhance sales 
strategies. This dashboard should highlight overall sales performance, market-wise comparisons, and key contributors, such as top customers and top products.

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset from MySQL server.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & 2 empty values were present except column named "Zone" in markets table.Unchecked the blank option from the dropdown filter.
- Step 5 : In sales transaction table it was observed that there were negative and zero value in "sales_amount" column. Unchecked the same with dropdown filter as its considered as garbage values.
- Step 6: After reviewing the "transaction" table, a conditional column was created to standardize the currency from USD to INR across the dataset.
            
           = Table.AddColumn(#"Filtered Rows", "Std_sales_amt", each if [currency] = "USD" or [currency] = "USD#(cr)" then [sales_amount]*88 else [sales_amount])
- Step 7 : Open Data Modeling tab to establish relationship.
- Step 8 : Created new table using enter data from data table. Added measures for base values as total revenue.
- Step 9 : In the report view, under the view tab, theme was selected.
- Step 10: To display the base values for total revenue and total quantity sold, two cards were added to the report using the visualizations pane. This was done by
  selecting the card visual from the pane and assigning the respective measures for total revenue and total quantity sold to each card, allowing a clear and concise representation of these key metrics.
- Step 11 : Visual filters (Slicers) were added for two fields named "Year", "Months".
- Step 12: To visualize the revenue and quantity per market, two stacked bar charts were added. Using the visualizations pane, stacked bar charts were selected,
- and the data fields for revenue and quantity were assigned to each chart. This allowed for a comparative analysis of revenue and quantity sold across different markets.
- Step 13 : A pie chart was added to represent the top 5 customers, visualizing their contribution to the overall revenue. Similarly, a donut chart was included to display the top 5 products, showcasing their share in total sales. Both visuals were selected from the visualizations pane, and filters were applied to limit the data to the top 5 customers and products, ensuring a clear and focused representation of key contributors.
- Step 14 : Heading was added by text box.

    
- Step 15 : New measure was created to find total revenue and total quantity sold.

Following DAX expression was written for the same,
        
        Total Revenue = sum('sales transactions'[sales_amount])
        Total Quantity = sum('sales transactions'[sales_qty])
        


 - Step 18 : The report was then published to Power BI Service.
 
 
![Publishing to power bi](https://github.com/user-attachments/assets/c9c09d75-7f64-4ce0-8667-f1108ca03aea)

# Snapshot of Dashboard (Power BI Service)

![Screenshot 2024-10-17 154506](https://github.com/user-attachments/assets/711fe85d-ba4c-4b66-901f-953d9632e3b8)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Screenshot 2024-10-17 155222](https://github.com/user-attachments/assets/d8745236-c68e-4fe9-8b7c-2992508f519f)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Revenue = 984.81M

    Revenue by market
    1, Delhi NCR = 519.51M
    2, Mumbai = 150.08M
    3, Ahmedabad = 132.31M
    4, Bhopal = 58.61M
    5, Nagpur = 55.03M
    6, Kochi = 18.81M
    7, Chennai = 18.04M
    8, Kanpur = 13.58M
    9, Hyderabad = 7.44M
    10, Patna = 4.43M
    11, Lucknow = 3.09M
    12, Surat = 2.61M
    13, Bhubaneshwar = 0.89M
    14, Bengaluru = 0.37M
    
### [2] Total Quantity Sold = 2M 

    Quantity by market
    1, Delhi NCR = 988K
    2, Mumbai = 384K
    3, Nagpur = 262K
    4, Kochi = 255K
    5, Ahmedabad = 207K
    6, Bhopal = 113K
    7, Hyderabad = 78K
    8, Chennai = 50K
    9, Lucknow = 37K
    10, Surat = 17K
    11, Kanpur = 17K
    12, Bhubaneshwar = 15K
    13, Patna = 6K
    14, Bengaluru = 413

 ### [3] Top 5 Customers

    1, Electricalsara Stores = 413.33M
    2, Electricalslytical = 49.64M
    3, Excel Stores = 49.12M
    4, Premium Stores = 44.91M
    5, Nixon = 43.89

### [4] Top 5 Products

    1, Blank = 419K
    2, Prod065 = 64.07K
    3, Prod159 = 18.4K
    4, Prod040 = 16.11K
    5, Prod018 = 7.08K


An issue in the source data is causing some values to appear as "blank," which is why it is being displayed first in the list.

One line chart showing the revenue trend is available. 

Two Slicers are available to filter based on the year and month.
