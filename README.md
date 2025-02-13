# Sales-by-region-Dashboard
Using Power Bi, created a dashboard. 
•	Business requirement of this dashboard - 
As the measures we are getting sales, profit and quantity under the 2021 to 2024.
So in this dashboard key metrics are, sales, profit and quantity.
https://drive.google.com/drive/folders/1jhZJHXkZ4HBSNDs7UzAJe4c_s8OwDiPY


•	KPI requirements of this – 

Central Region:
Display Sales, Profit, and Quantity as per the selected year filter.
Allow dynamic selection between Sales, Profit, and Quantity.
Show Sales for the previous year based on the selected year.
Create a bar sparkline for monthly data, including an average line for better trend analysis.

East Region:
Display Sales, Profit, and Quantity as per the selected year filter.
Allow dynamic selection between Sales, Profit, and Quantity.
Show Sales for the previous year based on the selected year.
Create a bar sparkline for monthly data, including an average line for better trend analysis.

South Region:
Display Sales, Profit, and Quantity as per the selected year filter.
Allow dynamic selection between Sales, Profit, and Quantity.
Show Sales for the previous year based on the selected year.
Create a bar sparkline for monthly data, including an average line for better trend analysis.

West Region:
Display Sales, Profit, and Quantity as per the selected year filter.
Allow dynamic selection between Sales, Profit, and Quantity.
Show Sales for the previous year based on the selected year.
Create a bar sparkline for monthly data, including an average line for better trend analysis.


•	Chart’s requirements - 
In this dashboard, we can see these relationships. 
For an example, sale under 2021, 
First chart – how the sales have distributed during the year in four states. (East, west, central and south)
Another chart – how the sales have distributed in cities relevant states. And also we can see rank of that cities sales. And also this bubble map shows big bubbles shows big sales like wise. 
Another chart - metrics of previous year and current year sales in 2020 and 2021 in four states. 

•	Sales by State:

Bubble Map: Display a bubble map to visualize sales distribution across different states. The size of each bubble should correspond to the sales volume, allowing users to quickly identify states with high or low sales.

Bar Chart: Place a bar chart alongside the bubble map to provide a detailed breakdown of sales by state. This chart should allow for easy comparison between states, with bars sorted either in ascending or descending order of sales.

Create a table/grid to display key metrics for both current and previous years. The table should include the following columns:

CY Sales: Current Year Sales
PY Sales: Previous Year Sales
YoY Sales: Year-over-Year Sales growth or decline
CY Profit: Current Year Profit
PY Profit: Previous Year Profit
YoY Profit: Year-over-Year Profit growth or decline
CY Qty: Current Year Quantity
PY Qty: Previous Year Quantity
YoY Qty: Year-over-Year Quantity growth or decline

 
We create a table name as calendar table because we have to create a table in dashboard add CY sales, PY sales like that. 
Then using model view connect those two table in 1 to many relationship. 
Set canvas background image and reduce transparency. Then set image middle. 
Modeling tool – new parameters- fields – select metric and add those total sales, total profit, total quantity.

Going to create KPI-
Next add card. That icon has 123. Then drag and drop to that select metrics. (we have already created from data )
Next now visualize that slicer. That included total sales, total profit and total quantity. To that, click particular slicer, then go to format of your visuals tab near to build visuals. Then slicer setting convert to tile. Values convert to seouige bold.
If then want to change name of ‘total sales’ into ‘sales’ then click the select metrics then we can see autmaticall created DAX functions. From there, we can change names. 

Next when adding regions as central, east like wise. First add text box and type central. Then do that center and when clicking that under effects tab turn off background. 

Next turn on the filters near to the visualization. Then drag and drop field to that ‘region’ and then select central first. Then add slicer and create 4 tiles of 2021, 2024from drag and drop year column from calendar table. 

Create new measure as dynamic title = max of select metrics (total sales, quantity and profit). Then created a card, drag and drop that new measure dynamic title into that card. 
Ex -  changing the title of sales, profit, qty like wise. 

To calculate previous year sales, to get that we can to first create PY KPI new measurement. Then select new measure and rename It as PY KPI Sales. Then first select a year from calendar table year. Then to get the previous year, we have to minus one from selected year. Then return that value. 

Then get a card and drag that PY KPI sales into that. Then we can see, according to sales, when selecting 2022, we can see sales of 2021 from that card. But when selecting 2021, there is blank. So, at that time we have to again edit that calculation we have done before. We have to add if condition to that return. 
Like this, 
PY KPI Sales = 
    VAR SelectedYear = SELECTEDVALUE('Calendar Table'[Year])
    VAR PreviousYearSales = CALCULATE([Total Sales], 'Calendar Table'[Year] = SelectedYear -1)
    VAR FormatPYSales = FORMAT(PreviousYearSales/1000, "0.00")
    RETURN
        IF(ISBLANK(PreviousYearSales), "PY Sales: No Data", "PY Sales:" & FormatPYSales & "k")

There are three variables, SelectedYear, PreviousYearSales, FormatPYSales. 
According to if condition, first add the expression, then add if it is correct what we want show and another one is if it is false which we want to show. 

Next when we want visualize the sales or profit or quantity distribution over the year. That means over the 12 months, then add column bar chart. To the x-axis add months, and to the y-axis add select metrics (we already created that sales, profit and quantity).
When creating that we can see, there is no order of that months. So we have to sort that when clicking that three dots. But it is not getting rigt order. So we have to add a new column in calendar table, as Month Number. 
Month Number = MONTH('Calendar Table'[Date]) then getting the number of that related month. 
But when typing like this, 
Month = FORMAT('Calendar Table'[Date],"mmm") then it shows the first three letters of that relevant month. As an example, ‘Jan’ etc. 

https://drive.google.com/drive/folders/1jhZJHXkZ4HBSNDs7UzAJe4c_s8OwDiPY

