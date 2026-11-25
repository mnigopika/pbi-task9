# 🏡 King County House Sales --- Power BI Data Cleaning & Transformation

## 📌 Project Overview

This project focuses on cleaning, transforming, and preparing the **King
County House Sales dataset** using **Microsoft Power BI and Power
Query**. The prepared data can be used to explore house prices, property
features, and sales trends.

## 🎯 Project Objectives

-   Import and understand the raw housing dataset.
-   Inspect data types, missing values, and duplicate records.
-   Clean and transform columns using Power Query.
-   Prepare the dataset for analysis and visualization.
-   Build meaningful insights through a Power BI report.

## 📂 Dataset Details

  Description                                                  Details
  ------------------------------ -------------------------------------
  Dataset                          `kc_house_data - kc_house_data.csv`
  Total records                                                 21,613
  Total columns                                                     21
  Missing cells in source file                                       0
  Exact duplicate rows                                               0
  Records with a repeated `id`                                     353
  Sale date range                           02 May 2014 -- 27 May 2015

## 🧹 Data Cleaning & Transformation

The following are the key cleaning and transformation activities to
review and apply in Power Query:

1.  **Data Import** -- Load the CSV file into Power BI using Get Data.
2.  **Column Headers** -- Confirm that the first row is used as the
    column headers.
3.  **Data Types** -- Assign suitable data types to date, price, area,
    numeric, and categorical columns.
4.  **Missing Values** -- Check columns for null or blank values and
    decide how to handle them.
5.  **Duplicate Check** -- Identify exact duplicate rows and investigate
    repeated property IDs before removing anything.
6.  **Date Transformation** -- Convert the `date` column into a proper
    Date data type.
7.  **Column Review** -- Check column names and remove only unnecessary
    columns.
8.  **Value Validation** -- Review zero values and unusual values in
    property-related columns.
9.  **Apply Changes** -- Use Close & Apply to load the prepared data
    into the Power BI model.
   

<img width="1342" height="711" alt="Screenshot 2026-11-25 173511" src="https://github.com/user-attachments/assets/e1b66f94-1506-4f10-bd01-7d439735c083" />



## 🔄 Power Query Date Transformation

The source date values use a format similar to `20141013T000000`. The
following Power Query M expression can convert this text into a Date
value:

``` powerquery
Date.FromText(
    Text.Start([date], 4) & "-" &
    Text.Range([date], 4, 2) & "-" &
    Text.Range([date], 6, 2)
)
```

After conversion, set the new column's data type to **Date**.

## 📊 Important Data Quality Notes

-   The source CSV contains **0 missing cells**.
-   The source CSV contains **0 completely duplicated rows**.
-   **353 records** have an `id` value that appears more than once.
    Repeated IDs are not necessarily duplicate records; verify their
    meaning before deleting them.
-   `yr_renovated = 0` appears in **20,699 records**. This may represent
    properties that have not been renovated, so do not automatically
    treat it as missing data.

## 📈 Suggested Power BI Analysis

The cleaned dataset can be used to create:

-   KPI cards for average price, median price, and total sales records.
-   Charts showing house prices by bedroom count, grade, and condition.
-   A trend chart showing sales over time.
-   A scatter chart comparing living area and sale price.
-   A map showing property locations using latitude and longitude.
-   Slicers for date, zipcode, bedrooms, and waterfront.

## 🧮 Sample DAX Measures

``` dax
Average Sale Price = AVERAGE('kc_house_data'[price])

Median Sale Price = MEDIAN('kc_house_data'[price])

Total Properties = COUNTROWS('kc_house_data')
```

Replace `'kc_house_data'` with the actual table name in your Power BI
model if it is different.

## 🛠️ Tools & Technologies

-   **Microsoft Power BI Desktop** -- Data modelling and visualization
-   **Power Query** -- Data cleaning and transformation
-   **DAX** -- Calculated measures and analysis
-   **CSV** -- Source dataset

## 📁 Project Files

-   `kc_house_data - kc_house_data.csv` -- Original dataset
-   `housedata.pbix` -- Power BI report file
-   `README.md` -- Project documentation

## 👤 Conclusion

This project demonstrates the data preparation process for a real-world
housing dataset. Cleaning and validating the data helps create a more
reliable foundation for analysis and reporting in Power BI.

------------------------------------------------------------------------

**Project:** King County House Sales Analysis\
**Tool:** Microsoft Power BI
