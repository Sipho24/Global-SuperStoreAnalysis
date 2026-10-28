# Global-SuperStoreAnalysis
The task was to analyse dataset for Global SuperStore to look at was it happening and what is not happening with the date.
First step was to clean the data, it had no duplicates but postal codes had null values and the column was not important into the data so it was deleted.
Date columns were changed from text to Data, and on PowerBI Using Locale to standardize the dates.
Ensuring the other columns were correct, cost columns to currency and profit to also currency but as a percentage.
The below DAX Measures were added: Total Sales = SUM(Sales), Total Profit = SUM(Profit), Total Orders = DISTINCTCOUNT(Order ID), Profit Margin = DIVIDE([Total Sales], [Total Orders], 0), Total Quantity = SUM(Quantity).
New columns for dates were also added: Order Year as YEAR([Order Date]), 
Order Year-Month as FORMAT([Order Date], "YYYY-MM"),
Profit Flag as IF([Profit] < 0, "Loss", "Profit"),
