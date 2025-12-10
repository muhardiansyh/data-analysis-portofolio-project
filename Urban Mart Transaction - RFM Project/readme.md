# Portofolio Project: Urban Mart Transaction RFM Performance Analysis Dashboard (Microsoft Excel)
## 1. Project Overview & Objective
This project is an advanced Customer Analytics case study focusing on transactional data from a retail business, "Urban Mart" (using the Superstore dataset structure). The primary goal is to demonstrate Advanced Spreadsheet Modeling and Business Intelligence (BI) Dashboarding capabilities using Microsoft Excel to drive strategic marketing and operational decisions.

The analysis workflow focuses on transitioning raw transactional data into actionable customer segments (RFM) and creating a highly interactive dashboard to track performance dynamically.

Key Objectives:
- RFM Feature Engineering: Calculate and model the three core customer metrics: Recency (R), Frequency (F), and Monetary (M) value for every unique customer ID.

- Customer Segmentation: Implement a robust scoring system (1-4 scale) and utilize a Segmentation Matrix (via VLOOKUP) to assign customers to distinct, actionable segments (e.g., Champions, At-Risk, New Customers).

- Dynamic Data Visualisation: Develop a professional and interactive performance dashboard where the displayed data can be controlled by end-users.

- Advanced Control Integration: Implement Scroll Bars and Spin Buttons linked with the INDIRECT function to enable dynamic data slicing, allowing users to scroll through and shift the visual range of the analyzed data on demand.

- Performance Analysis: Visualize the distribution of the customer base across the RFM segments to provide clear insight into customer health, allowing management to prioritize retention and marketing efforts.

Tools & Platform:
Microsoft Excel, Pivot Tables, Advanced Spreadsheet Formulae (VLOOKUP, IF, MAX, COUNTIF, SUMIF, DATEDIF/Date Functions, INDIRECT), Scroll Bar, Spin Button.

## 2. Data Source & Initial Setup
The analysis is based on the comprehensive Superstore Dataset, which contains four years of transactional records across various regions, product categories, and customer segments. This section confirms the origin and initial state of the data before any processing began.

Source: Kaggle Datasets

Dataset Link:
https://www.kaggle.com/datasets/xyzeys/urbanmart-transactions-dataset-2023-2024

Initial Setup Best Practice:
The raw data was imported directly into Microsoft Excel. A crucial data integrity best practice was applied: preserving the original, unmodified data in a dedicated RAW DATA sheet. All subsequent calculations, RFM feature engineering, and modeling steps were performed on a separate sheet named RFM_CALCULATION to maintain full data integrity and auditability.

Target Data Range:
The analysis primarily focused on creating the necessary dimensions and measures for RFM modeling, including:

- Customer ID: The unique identifier used as the primary key for all RFM aggregation.

- Order Date: Required to calculate the Recency (R) metric.

- Order ID: Required to calculate the Frequency (F) metric.

- Sales: Required to calculate the Monetary (M) metric.

## 3. Methodology & Problem Solving (Technical Deep Dive)
This phase highlights the critical data wrangling and spreadsheet modeling required to transform the raw transactional data into an analytic-ready RFM format (the RFM_DATA sheet). This section demonstrates the ability to execute complex customer segmentation logic and perform advanced custom aggregations using Excel functions.

### 3.1. RFM Feature Engineering and Scoring
The core of this project involved creating the three RFM metrics and converting them into actionable customer scores.

- Recency (R) Calculation: Calculated as the number of days between the current date and the Max(Order Date) for each unique customer. This required the use of MAX and date subtraction formulas to find the last transaction date.

- Frequency (F) Calculation: Calculated as the count of unique Order IDs associated with each customer ID. This was implemented using the COUNTIF function to aggregate transactional volume.

- Monetary (M) Calculation: Calculated as the Sum(Sales) contributed by each customer. This was implemented using the SUMIF function to aggregate the total value spent.

Scoring Logic: The raw R, F, and M values were converted into a 1-4 scale score (4 being the best) using a complex nested IF logic referencing custom Percentile/Quartile cut-off points. The Recency score logic was inverted (Low R value = High Score) to reflect its business meaning.

### 3.2. Customer Segmentation Modeling
After calculating the scores, the segmentation phase grouped customers into strategic business categories.

- RFM Code Aggregation: The three numerical scores (R, F, M) were concatenated into a single, three-digit text string (e.g., "444") to create a unique identifier for the customer's score pattern.

- VLOOKUP Segmentation: A dedicated Segmentation Matrix was established. The final customer segment (e.g., "Champions," "At Risk/Churning" "New Customers") was assigned using the VLOOKUP function, mapping the unique three-digit RFM code to the predefined business segment name. This proved the ability to efficiently scale segmentation logic without relying on complex array formulas.

### 3.3. Dynamic Dashboard Control Implementation
The project introduced advanced Excel controls to maximize dashboard interactivity and user experience, moving beyond standard slicers.

- Scroll Bar and Spin Button Integration: Both the Scroll Bar and Spin Button controls were integrated and mapped to specific cells to control a dynamic Start Index and Visible Data Count.

- Dynamic Data Slicing (INDIRECT Function): The visual data displayed in the dashboard charts (e.g., Top N Segments by Revenue) was driven by the INDIRECT function. By using INDIRECT combined with the values from the linked Scroll Bar/Spin Button cells, the chart's data range could be dynamically shifted and re-sized, allowing the user to seamlessly "scroll" through different data subsets without manually adjusting chart source data. This demonstrates a high-level command of advanced, non-visual Excel functions to enhance BI flexibility.

## 4. Dashboard Analysis & Key Findings
The final output is a clean, interactive dashboard in Microsoft Excel (located in the DASHBOARD ANALISIS sheet). The dashboard is designed to provide quick answers regarding customer health, loyalty distribution, and the performance of key customer segments.

### 4.1. Dashboard Structure & Interactivity
- Key Metrics (RFM Summary): The dashboard prominently features the main performance indicators: Total Unique Customers, Total Transactions, and Total Sales contributing to the RFM model.

- Core Visual: The centerpiece of the dashboard is a Pie/Donut Chart visualizing the distribution of customers across the 5-7 major RFM segments (e.g., Champions, Loyal, At-Risk).

- Dynamic Control Interactivity: The dashboard utilizes the advanced Scroll Bar and Spin Button controls (linked via INDIRECT). This allows the user to dynamically shift the visible data range of the secondary charts (e.g., Top N Segments by Average Order Value) without using standard slicers, demonstrating sophisticated control over data presentation.

Data Source Integrity: All charts and aggregations draw data from the cleaned and feature-engineered RFM_CALCULATION sheet, ensuring transparency and accuracy.

### 4.2. Key Analytical Insights
The analysis yielded the following critical business insights based on the RFM segmentation:

- Customer Health & Loyalty: The analysis clearly identifies the size and value of the "Champions" segment (e.g., 5% of customers) and the "Loyal Customer" segment, confirming the foundation of the business's recurring revenue.

- Churn Risk Identification: The size of the "At Risk" / "Cannot Lose Them" segments is immediately visible. The large volume of customers in this category (which have high F/M scores but low R scores) highlights an urgent business need to launch targeted retention campaigns (e.g., win-back discounts).

- New Customer Conversion Opportunity: The "New Customers" segment (High R, Low F/M) indicates the volume of recent acquisitions. This insight provides actionable data for the marketing team to focus on effective onboarding strategies to convert first-time buyers into Loyalists.

- Monetary Value Validation: By comparing the Total Sales metric across the segments, the analysis visually validates that the "Champions" segment is responsible for the majority (e.g., 40-60%) of total revenue, justifying concentrated efforts on these high-value groups.

4.3. Visual Portfolio
<img width="1496" height="596" alt="image" src="https://github.com/user-attachments/assets/fc2cd0f7-78e4-4d47-b6c6-09b4e7415c81" />
<img width="940" height="408" alt="image" src="https://github.com/user-attachments/assets/b86fe3dd-57da-49c6-a222-b568c516a6ad" />

## 5. Project Access & Verification
This section provides direct links to the final output file contained within this GitHub repository, allowing for full verification of the analysis methodology, results, and advanced control implementations.

### 5.1. Final Output File
The primary output is the interactive dashboard contained within the Microsoft Excel file. This file demonstrates the advanced use of Scroll Bars and Spin Buttons linked via the INDIRECT function, which requires verification directly in the Excel environment.

### 5.2. Repository Contents
The repository contains the necessary files to audit the entire project workflow, from the source data to the final analytical results:

readme.md (This file): Documentation of the project's objectives, methodology, technical challenges solved, and key business findings.

RFM_UrbanMart_Transaction.xlsx: The final working Microsoft Excel file, which includes the raw data, the RFM_CALCULATION sheet with all scoring logic (e.g., VLOOKUP segmentation), and the interactive DASHBOARD ANALISIS sheet with dynamic controls.

UrbanMart_Transactions.csv: The original, untouched source file used to ensure transparency and auditability of the data source.

