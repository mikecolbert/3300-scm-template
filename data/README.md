# Data

## Overview

This folder contains sample sales transaction data used to demonstrate a simple JavaScript CSV-loading application. The data is fictional and was generated for educational purposes to illustrate how a web application can fetch, parse, and display structured data from a CSV file.

## Source

The data in `sales.csv` was synthetically generated — it does not represent real transactions, real products, or a real company. It is intended solely as a teaching dataset for demonstrating front-end JavaScript concepts such as `fetch()`, CSV parsing, and dynamic HTML table construction.

## Files

| File | Description |
|------|-------------|
| `sales.csv` | Ten sample sales order records across three product categories |

## Data Dictionary

The following table describes each column in `sales.csv`.

| Column | Data Type | Description | Example |
|--------|-----------|-------------|---------|
| `Order ID` | Integer | A unique identifier for each sales transaction | `1001` |
| `Product` | String | The name of the product sold | `Laptop Pro 15` |
| `Category` | String | The product category. One of: `Electronics`, `Accessories`, or `Furniture` | `Electronics` |
| `Quantity` | Integer | The number of units sold in the transaction | `2` |
| `Unit Price` | Decimal (USD) | The price of a single unit at the time of sale | `1299.99` |
| `Total` | Decimal (USD) | The total sale amount, calculated as `Quantity × Unit Price` | `2599.98` |
| `Date` | Date (YYYY-MM-DD) | The date the transaction was recorded | `2024-01-05` |

## Notes

- All monetary values are in US dollars (USD).
- Dates follow the ISO 8601 format: `YYYY-MM-DD`.
- The dataset contains 10 records spanning January–February 2024.
