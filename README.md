# 🎬 The Global Streaming Wars - Power BI Analysis ![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) ![Power Query](https://img.shields.io/badge/Power%20Query-FFD580?style=for-the-badge&logo=powerbi&logoColor=black)

## 📊 Project Overview
This interactive Power BI dashboard provides a deep dive into the content strategies of the world's leading streaming platforms: **Netflix, Amazon Prime, and Disney+**.

The goal was to visualize the growth of content libraries over time, compare the volume of Movies vs. TV Shows, and analyze the geographical distribution of content production.


<img width="2081" height="1169" alt="All" src="https://github.com/user-attachments/assets/a33fff91-e2ea-4e6f-bbb0-7d41f9446d08" />
---<img width="2081" height="1171" alt="Amazon" src="https://github.com/user-attachments/assets/d1d79355-8424-4658-8bf5-7d5d3f9f28d9" />
<img width="2081" height="1171" alt="Disney" src="https://github.com/user-attachments/assets/20f9759d-9d58-48e8-8b06-82f2bf16c3ad" />
<img width="2080" height="1170" alt="Netflix" src="https://github.com/user-attachments/assets/ae0113e3-5368-425a-b936-f03502dc32cd" />
*(Note: Please download the PNG or PBIX file to view the high-resolution report)*

## 🛠️ Work Process

### 1. Data Extraction & Ingestion
* Sourced **three separate CSV datasets** from external sources, representing distinct content libraries.
* Imported raw data into **Power BI** via Power Query Editor.

### 2. ETL & Data Cleaning (Power Query)
* **Merging Disparate Sources:** Appended the three separate tables (Netflix, Amazon, Disney+) into one master table (`All_Movies`).
* **Data Standardization:** Aligned column names and data types across different source files to ensure consistency.
* **Error Handling:** Cleaned "Release Year" and "Date Added" columns, removing errors and handling missing values to prevent data loss.
* **Text Trimming:** Applied text transformation to remove whitespace and standardize categorical data (Platform names, Ratings).

### 3. Data Engineering (Solving the ID Collision)
* **The Challenge:** Since the three datasets came from different sources, they used identical ID schemas (e.g., `s1`, `s2`...). When merged, Power BI could not distinguish between *Netflix's "s1"* and *Amazon's "s1"*, leading to severe data inaccuracies (duplicate removal).
* **The Solution:** I engineered a **Composite Primary Key** using DAX/Power Query. I concatenated the `Platform` name with the original `show_id` (e.g., transforming `s1` into `Netflix-s1`).
* **The Result:** This guaranteed unique identification for every title, correcting the metrics and revealing the true total of **19,000+ unique titles**.

### 4. Visualization & Reporting
* **Dynamic Filtering:** Created custom slicers/buttons to toggle views between specific platforms.
* **KPI Cards:** Implemented `DISTINCTCOUNT` measures to accurately calculate Total Titles, Movies, and TV Shows.
* **Timeline Analysis:** Visualized content growth over decades using Area Charts.
* **Geospatial Analysis:** Mapped content production by country.

## 📈 Key Insights 
* **Amazon Prime Dominance:** Amazon holds the largest volume of content among the three platforms (as seen in the Total Titles KPI), largely due to its extensive library of older licensed movies.
* **Netflix's "Originals" Boom:** The Production Timeline reveals a massive exponential spike in content added by Netflix in the last decade, highlighting their pivot to mass production of original content.
* **Library Size Comparison:** Disney+ has the smallest content library by volume compared to Amazon and Netflix, indicating a more selective content catalog strategy.

---
