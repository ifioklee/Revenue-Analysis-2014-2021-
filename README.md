# Revenue Analysis (2014-2021)

# Project Overview
This reposistory contains details relating to the analysis of combination of datasets relating to the revenue of a ficticious company from the year 2014 through to the year 2021. I worked on this project using power query to transform the various dataset and Power BI to visulize various insight from the working on the dataset. Working on this project helped me learn how to use Power Query for various data transformation process and Power BI for visulization, I also got to apply my knowledge of DAX while working with Power BI to derive and visulize various insights.

## Project Goal

The goal of this project is to firstly to help me apply practically my knowledge of the use of Power Query for data transformation, Power BI for data visulization and the use of DAX in creating various logical measures within Power BI.By applying apply all these, this project end goal is to visualize the answers to the following question on a Power BI interactive dashboard.

1. Total Revenue. 
2. Total number of Products. 
3. Total number of Manufactures. 
4. % of Urban Revenue.
5. Number of countries 
6. Total number of cities. 
7. Revenue trend by year and month. 
8. Top 5 Manufacturers By Revenue.
9. Top 10 Products By Revenue. 
10. Total Revenue By category. 
11. Total Revenue By Country. 
12. Segment, Revenue, and a Sparkline of revenue by product (Table Visual).

# Features
- Interactive Power BI dashboard with year, month and product slicers
- File that includes all the DAX formula used in creating different measure in Power BI


# Data

# Project Structure

### Raw Dataset
The original dataset used for this analysis can be found here:  
[InternationalSales](https://github.com/ifioklee/Revenue-Analysis-2014-2021-/blob/main/InternationalSales.zip) and [USSales](https://github.com/ifioklee/Revenue-Analysis-2014-2021-/blob/main/USSales.zip)
### DAX Scrips Analysis
This file contains DAX formula for the analysis:  
[ View DAX Formula Script]

### Visualization
Interactive Power BI dashboard is available here:  
[View Power BI Dashboard]

### README.md Project verview and instructions
You can explore the complete project documentation here:  
[View README File](https://github.com/ifioklee/Sales-Data-Analysis-Using-Excel/blob/main/README.md)

## Technical Details

This project uses **Power Query** for data exploration and transformation and **Power BI**  for chart visualization, and interactive dashboard creation.

### Data Preparation and Exploration (Power Query)
- The Product, Manufacturer and Geo table is cointaind in the file name USASales as CSV files, they are imported into Power Query for tranformation
- The Sales table is conitained in the file named USSales as an Excel file, it is imported into Power Query for tranformation
- The InternationalSales folder is imported into Power Query as a folder for transformation

#### Product Table
- Change the data type both ProductID and MunufacturerID columns to text
- Create anew column named 'Segment' by splitting by delimiter the 'Product' column
- Replace rows with NULL entries using the fill Down function
- Create a new 'Price' column to have only the price datapoint as just figures with the USD symbol

 #### Geo Table
 - Remove the top two rows
 - Promote the first row as new header of the table
 - Change the 'Zip' column data type to text and remove rows with errors
 - Remove the redundacy in the data by spilitting the 'city' column by delimitter to have only information city stand alone and the part of the split cointaining state and country datapoint is deleted because we alredy have columns for each of them
 - Replace blank rows with NA in the City, State, Region, District and Country columns

#### Manufacturer Table
- Remove last 3 rows as they cointain null entries
- Transpose the table
- Promote first row the header of the table
- Change the data type of the ManufacturerID column to text

#### Sales Table 
- Change the data type of the ProductID, Zip and Revenue to text, text and fixed decimal respectively
- Replace all NULL entries in the country column with USA( this is done after the InternationalSales table has been appended to the Sales table)

#### InternationalSales Table
- Delete the column 'Source.name'
- Remove errors from 'Zip' column
- Change the data type of ProductID, Zip and Revenue columns to text, text and fixed decimals respectively
- Append to Sales Table
- Disable load after appending to the Sales Table

Now Apply and load to Power BI

### Power BI
- Create a new table called 'Calendar' using DAX Calendar = CALENDARAUTO()
- Change data type 'Date' column in the Calendar table
- Create new column called month in the Calendar table using DAX Month = FORMAT('Calendar'[Date].[Month],"MMMM")

### Data Modeling( Power BI)
- The product table to sales table by ProductID with one to many cardinality
- The Geo table to sales table by Zip with many to many cardinality
- The manufacturer table to product table by ManufacturerID with one to many cardinality
- The calendar table to the sales table by Date with one to many cardinality

### Visulization with Power BI
- Visualize to 10 Products by revenue using a stacked bar chart
- Visualize to 5 Manufacturer by revenue using a stacked bar chart
- Create two buttons with labels Manufacturers and Products to swich between the visuals created above
- Visualize the Total revenue using a Card and the DAX total revenue = SUM(Sales[Revenue])
- Visualize total number of products using a card and DAX Total Number of Products = DISTINCTCOUNT('Product'[Product])
-    


## Results and Insights
