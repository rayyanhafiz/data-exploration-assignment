# Retail Product Data Exploration (Excel)

![Microsoft Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

A structured exploratory data analysis (EDA) project conducted in Microsoft Excel on a retail product dataset. This repository demonstrates core spreadsheet modeling skills, including summary statistics, logical threshold classification, conditional aggregation, and string parsing.

---

## Project Overview

The objective of this project is to clean, transform, and analyze product inventory data across various categories (Electronics, Fashion, Kitchen, etc.). The analysis extracts key financial benchmarks, parses compound identifier strings into structured time and location attributes, and categorizes products based on pricing tiers.

---

## Dataset Schema

The primary worksheet (`Dataset`) contains 34 product records across 6 attributes:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Product ID` | String | Unique compound alphanumeric code (e.g., `28-JAN-US`) |
| `Product Name` | String | Commercial item name (Laptop, Sneakers, Coffee Maker, etc.) |
| `Brand Name` | String | Manufacturer / brand |
| `Price ($)` | Numeric | Unit price in USD |
| `Quantity` | Integer | Units currently in stock |
| `Category` | String | Product department classification |

---

## Tasks & Analytical Methodology

### 1. Summary Statistics
* **Total Inventory Value:** Sum of all unit prices across the catalog.
  * Formula: `=SUM(Price_Range)`
* **Product Catalog Size:** Total count of active SKUs.
  * Formula: `=COUNT(Price_Range)`
* **Average Unit Price:** Mean listing price across all departments.
  * Formula: `=AVERAGE(Price_Range)`
* **Price Extremes:** Maximum and minimum product pricing.
  * Formulas: `=MAX(Price_Range)`, `=MIN(Price_Range)`

### 2. Segment Classification (`IF`)
* Classified products into tier bands based on a $500 threshold:
  * **High Price:** Price $\ge$ $500
  * **Standard Price:** Price $<$ $500
  * Formula: `=IF(D2>=500, "High Price", "Standard Price")`

### 3. Conditional Aggregation (`SUMIF`, `COUNTIF`)
* **Departmental Revenue Contribution:** Calculated cumulative price for the **Electronics** category.
  * Formula: `=SUMIF(Category_Range, "Electronics", Price_Range)`
* **Budget Volume Count:** Identified the number of entry-level products priced under $100.
  * Formula: `=COUNTIF(Price_Range, "<100")`

### 4. Text Parsing & Feature Extraction (`LEFT`, `MID`, `RIGHT`)
Extracted temporal and geographic attributes from the structured `Product ID` (e.g., `DD-MMM-CC`):
* **Day (First 2 characters):** `=LEFT(A2, 2)`
* **Month (Characters 4 to 6):** `=MID(A2, 4, 3)`
* **Country Code (Last 2 characters):** `=RIGHT(A2, 2)`

---

## Key Results & Findings

| Metric | Result |
| :--- | :--- |
| **Total Product Value** | $10,100.00 |
| **Catalog Count** | 34 Products |
| **Average Product Price** | $297.06 |
| **Minimum Price** | $30.00 |
| **Maximum Price** | $1,000.00 |
| **Total Electronics Value** | $8,050.00 (~79.7% of total value) |
| **Products Under $100** | 11 Products (~32.4% of catalog) |

---

## Repository Structure

```text
├── Excel Assignment 1 - Data Exploration.xlsx   # Workbook with raw data and formulas
├── README.md                                    # Project documentation
└── .gitignore                                   # Excel temporary and lock file exclusions
