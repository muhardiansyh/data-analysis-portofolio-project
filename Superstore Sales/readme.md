
# Portofolio Project: Superstore Sales Performance Analysis Dashboard (Google Sheet)

## 1. Project Overview & Objectives
This project is an end-to-end data analysis case study utilizing a comprehensive Superstore dataset spanning four years of sales performance. The core objective is to demonstrate robust Spreadsheet Modeling and Advanced Problem-Solving capabilities required to convert raw, complex data into accurate, actionable Business Intelligence (BI) insights using Google Sheets.

The analysis workflow focuses on creating custom analytical dimensions, validating data consistency, and designing an interactive, professional dashboard.

Key Objectives:

- Data Validation & Parsing: Resolve data type conflicts within the Order Date column by implementing custom logic to validate numbers versus text strings and parse dates accurately using REGEX.

- Feature Engineering: Create essential business metrics, specifically Cost of Goods Sold (COGS), to enable a comprehensive profitability analysis.

- Time-Series Modeling: Develop custom solutions to group data by Fiscal Quarter and accurately aggregate profit using advanced functions like SUMIF and ROUNDUP, overcoming inherent platform limitations.

- Performance Ranking: Implement dynamic ranking with the RANK() function to identify the Top 10 Products based on sales contribution.

- Interactive Reporting: Design a functional, high-impact dashboard using Pivot Tables and Slicers to visualize quarterly trends and product performance.

Tools & Platform: Google Sheets, Pivot Tables, Slicer, Advanced Spreadsheet Formulae (IF, ISNUMBER, CONCATENATE, REGEXEXTRACT, RANK, SUMIF).

## 2. Data Source & Initial Setup
The analysis is based on the comprehensive Superstore Dataset, which contains four years of transactional records across various regions, product categories, and customer segments. This section confirms the origin and initial state of the data before any processing began.

Source: Kaggle Datasets

Dataset Link: https://www.kaggle.com/datasets/vivek468/superstore-dataset-final

Initial Step: The raw data was imported directly into Google Sheets. A crucial best practice was applied: preserving the original, unmodified data in a dedicated RAW DATA sheet. All subsequent cleaning, validation, and calculation steps were performed on a separate CLEANED & CALCULATION sheet to maintain full data integrity and auditability.

Target Data Range: The analysis focuses on key transactional and categorical columns, including Order Date, Sales, Profit, Sub-Category, and Region.

## 3. Methodology & Problem Solving (Technical Deep Dive)
This phase highlights the critical data wrangling, validation, and spreadsheet modeling required to transform the raw data into an analytic-ready format (CLEANED & CALCULATION sheet). This section demonstrates the ability to solve complex data quality issues and perform advanced custom aggregations.

### 3.1. Advanced Date Validation and Parsing
The most challenging step was ensuring the consistency of the Order Date column, which is essential for accurate time-series analysis.

- Problem: The original Order Date column contained a mixture of recognized date numbers and ambiguous text strings, preventing standard date functions from working universally.

- Solution (Order Date Parsing): A new, clean column (order_date) was engineered in the CLEANED & CALCULATION sheet. This column implements an IF condition to validate the data type, using a powerful REGEXEXTRACT solution to parse complex text dates:

      =IF(ISNUMBER(C2), C2, CONCATENATE(REGEXEXTRACT(C2,"\/(\d+\/)"),REGEXEXTRACT(C2,"\d+\/"),RIGHT(C2,4)))

This formula ensures that every entry in the new order_date column is a valid, calculable date value, regardless of its original format.

### 3.2. Custom Time-Series Modeling (Quarterly Aggregation)Analyzing trends requires grouping by quarter. 
Since Google Sheets Pivot Tables lack a robust, built-in feature for quarterly grouping, a custom dimension was developed.

- Custom Quarter Dimension: The final quarter series dimension was created using a concatenation of the quarter number and the year. This column (YYYY-Quarter) served as the primary aggregation driver for the Line Chart:

      =CONCATENATE("Q",ROUNDUP(MONTH(H43)/3),"-",TEXT(H43,"YYYY"))

- Final Aggregation (SUMIF Validation): The accuracy of the quarterly profit calculation was validated by creating a dynamic aggregation helper block in the Pivot Table 1 sheet, using UNIQUE to identify all quarter series and SUMIF to calculate the total profit for each quarter:

      =SUMIF($J$43:$J$1279, K43, $I$43:$I$1279)

This step confirms the reliability of the derived time-series data.

### 3.3. Feature Engineering: COGS and Top 10 Ranking
Two essential analytical dimensions were created to drive deeper business insights:

- Cost of Goods Sold (COGS): The COGS metric was calculated on the cleaned_data sheet (Sales - Profit) to provide context for profitability and gross margin analysis.

- Top 10 Product Ranking: To identify the best-performing products, the RANK() function was applied to the Total Sales column. This ranking column was then used to filter the dataset, enabling the creation of the dynamic Top 10 Product Sales bar chart. This method bypasses the basic Top-N filtering limitations of Google Sheets Pivot Tables.

## 4. Dashboard Analysis & Key Findings
The final output is a clean, interactive dashboard in Google Sheets (located in the DASHBOARD ANALISIS sheet). The dashboard is designed to provide quick answers regarding sales performance, profitability, and product contribution.

### 4.1. Dashboard Structure & Interactivity

- Key Metrics: The dashboard prominently features the main performance indicators: Total Orders (9994), Total Sales ($2.29M), and the Total Calculated COGS ($2.01M).

- Interactivity: The dashboard utilizes Slicers (Filter Controls) linked to key categorical fields (e.g., Region, Product Category) allowing users to dynamically filter all associated charts and Pivot Tables.

- Data Source Integrity: All charts and aggregations draw data from the cleaned and feature-engineered CLEANED & CALCULATION sheet, ensuring transparency and accuracy.

### 4.2. Key Analytical Insights
The analysis yielded the following critical business insights:

- Quarterly Trend (Profitability): The Line Chart displaying Total Profit vs. Custom Quarter Series highlights clear seasonal trends, with sales and profit peaking significantly in Q4 of every year. This trend validates the custom quarterly grouping methodology.

- Regional Dominance: The Pie Chart analysis shows that the West region is the primary contributor to overall sales and profit, accounting for approximately 31.4% of Total Sales.

- Product Performance: The Bar Chart displaying the Top 10 Products by Sales provides actionable data for inventory and marketing departments, highlighting which products deserve higher stock levels and promotional focus.

- Profit Margin Analysis (COGS Context): By comparing the calculated COGS against Sales and Profit, the analysis confirms the gross profitability of key product segments, setting a baseline for further investigation into operating expenses.

### 4.3. Visual Portfolio
<img width="1322" height="704" alt="image" src="https://github.com/user-attachments/assets/4cbedb64-8f52-4068-a05d-b69c3db82dbd" />

## 5. Project Access & Verification
This section provides direct links to the live, interactive spreadsheet and the raw files contained within this GitHub repository, allowing for full verification of the analysis methodology and results.

### 5.1. Live Dashboard Access
The primary output is the interactive Google Sheets dashboard. It is set to "view-only" access to maintain the integrity of the data while allowing stakeholders to utilize the Slicers and examine the final visualizations.

Link to Live Dashboard (Google Sheets):

https://docs.google.com/spreadsheets/d/1NCV1Yw_hyWOSjVl6tLTw6J8X40u14hgzkdqsPBvCOVM/edit?gid=90379397#gid=90379397

### 5.2. Repository Contents
The repository contains the necessary files to audit the entire project workflow:

- readme.md (This file): Documentation of the methodology and technical challenges solved.

- superstore_dataset_analysis.xlsx: The final working spreadsheet file, downloaded as .xlsx to preserve formulas, Pivot Tables, and formatting for offline verification.

- RAW DATA/Sample - Superstore.csv: The original, untouched source file used for the analysis.
