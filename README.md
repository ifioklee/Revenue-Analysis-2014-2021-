# Revenue Analysis (2014–2021)

## Project Overview
This repository contains details relating to the analysis of combined datasets on the revenue of a fictitious company from 2014 to 2021.  

The project was carried out using **Power Query** for data transformation and **Power BI** for visualizing insights.  
Working on this analysis strengthened my skills in:

- Power Query for data transformation  
- Power BI for dashboard creation  
- DAX for calculations and logical measures  

---

## Project Goal
The primary goal of this project is to practically apply Power Query, Power BI, and DAX to transform, model, and visualize data.  
The final Power BI interactive dashboard answers the following questions:

1. Total Revenue  
2. Total Number of Products  
3. Total Number of Manufacturers  
4. Percentage of Urban Revenue  
5. Number of Countries  
6. Total Number of Cities  
7. Revenue Trend by Year and Month  
8. Top 5 Manufacturers by Revenue  
9. Top 10 Products by Revenue  
10. Total Revenue by Category  
11. Total Revenue by Country  
12. Revenue Performance Table (Segment, Revenue, Sparkline by Product)

---

## Features
- Interactive **Power BI dashboard** with slicers (Year, Month, Product)  
- Includes a file containing all **DAX formulas** used in the report  

---

## Data

### Raw Dataset
The original datasets used for this analysis can be downloaded here:

- **International Sales:**  
  [InternationalSales.zip](https://github.com/ifioklee/Revenue-Analysis-2014-2021-/blob/main/InternationalSales.zip)

- **US Sales:**  
  [USSales.zip](https://github.com/ifioklee/Revenue-Analysis-2014-2021-/blob/main/USSales.zip)

### DAX Scripts
This file contains the DAX formulas used throughout the analysis:  
[View DAX Formula Script](https://github.com/ifioklee/Revenue-Analysis-2014-2021-/blob/main/DAX.md)

### Visualization
Interactive Power BI dashboard:  
[View Power BI Dashboard](https://github.com/ifioklee/Revenue-Analysis-2014-2021-/blob/main/Revenue%20Analysis(2014-2021)%20Dashboard.pbix)

### README.md (Project Overview & Instructions)
Full project documentation:  
[View README File](https://github.com/ifioklee/Sales-Data-Analysis-Using-Excel/blob/main/README.md)

---

## Technical Details

### Tools Used
- **Power Query** — data transformation and preparation  
- **Power BI** — visualization, modeling, DAX, and dashboard creation  

---

## Data Preparation & Transformation (Power Query)

### Product Table
- Change data type of *ProductID* and *ManufacturerID* to **text**
- Create a new column **Segment** by splitting the *Product* column
- Replace NULL values using **Fill Down**
- Create a **Price** column containing numeric price values only

### Geo Table
- Remove the top two rows  
- Promote first row as header  
- Change *Zip* column to **text** and remove rows with errors  
- Split the *City* column to remove redundant data  
- Replace blanks with **NA**  

### Manufacturer Table
- Remove last 3 rows (null entries)  
- Transpose the table  
- Promote first row as header  
- Change *ManufacturerID* to **text**  

### Sales Table
- Change data type of *ProductID*, *Zip*, *Revenue* to **text**, **text**, and **fixed decimal**  
- Replace NULL values in the *Country* column with **USA** (after appending international sales)

### International Sales Table
- Delete *Source.name* column  
- Remove errors from *Zip*  
- Set *ProductID*, *Zip*, and *Revenue* to correct data types  
- Append to Sales Table  
- Disable load for this table  

After transformations, data was loaded into **Power BI**.

---

## Power BI Modeling & DAX

### Calendar Table
- Create using:  
  `Calendar = CALENDARAUTO()`
- Add Month column:  
  `Month = FORMAT('Calendar'[Date].[Month], "MMMM")`

### Data Modeling
- Product → Sales (ProductID): **One-to-Many**
- Geo → Sales (Zip): **Many-to-Many**
- Manufacturer → Product (ManufacturerID): **One-to-Many**
- Calendar → Sales (Date): **One-to-Many**

---

## Visualizations in Power BI
- **Top 10 Products by Revenue** – Stacked Bar Chart  
- **Top 5 Manufacturers by Revenue** – Stacked Bar Chart  
- **Toggle Buttons** to switch between Products and Manufacturers  
- **Total Revenue** – Card  
- **Total Number of Products** – Card  
- **Total Number of Manufacturers** – Card  
- **Total Number of Countries** – Card  
- **Total Number of Cities** – Card  
- **Urban Revenue (%)** – Card  
- **Revenue by Category** – Donut Chart  
- **Revenue by Country** – Stacked Column Chart  
- **Revenue Trend (Year & Month)** – Line Chart  
- **Slicers** – Year, Month, Product  
- **Matrix Table** – Revenue performance with sparklines (Countries, Segments, Products)

---

## Results & Insights

- **Total Revenue:** $2.91 billion (2014–2021)  
- **Products:** 2,172 product lines  
- **Manufacturers:** 14  
- **Countries:** 7  
- **Cities:** 21,598  
- **Urban Revenue:** 79.79% of total revenue  

### Top Products by Revenue
1. Maximus UM-80  
2. Maximus UM-01  
3. Natura UM-10  
4. Maximus UC-00  
5. Maximus UC-69  
6. Maximus UC-74  
7. Maximus UC-41  
8. Maximus UM-50  
9. Maximus UM-04  
10. Maximus UC-16  

### Top Manufacturers by Revenue
- VanArsdel, Ltd — **$1,281,418,188.10**  
- Fabrikam, Inc — **$594,258,648.76**  
- Tailwind Traders — **$347,432,115.22**  
- Wide World Importers — **$264,569,247.71**  
- Nod Publishers — **$212,485,555.77**  

### Revenue by Country
| Country  | Revenue |
|----------|----------------------|
| USA      | $1,697,110,399.53 |
| Australia | $761,681,611.27 |
| Japan     | $227,982,217.89 |
| Nigeria   | $85,003,218.08 |
| Germany   | $69,249,072.33 |
| Mexico    | $51,944,903.93 |
| Canada    | $18,253,884.50 |

