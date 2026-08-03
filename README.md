# 🏢 Executive Retail Margin & Inventory Analytics Pipeline
![Status: In Progress](https://img.shields.io/badge/Status-In_Progress-F5A623?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker_Studio-4285F4?style=for-the-badge&logo=google&logoColor=white)

> **Enterprise Business Case:** End-to-end Analytics Engineering pipeline to uncover profit margin leakage, evaluate promotional discount efficiency, and deliver data-driven recommendations to executive leadership.

---

## 📌 1. Executive Summary & Business Problem
In high-growth e-commerce operations, aggressive promotional discounting often leads to **margin shrinkage** without proportionally driving customer acquisition. 

The Chief Revenue & Marketing Officer (CRMO) commissioned this project to answer three core business questions:
1. **Where is our margin leaking?** Which product categories generate the highest dollar-value loss due to discounting?
2. **Are discounts misallocated?** Are we over-discounting premium, highly-rated SKUs that would sell organically at full retail price?
3. **What is the real inventory valuation?** What is our true warehouse capital exposure after promotional adjustments?

---

## 🛠️ 2. Architecture & Tech Stack

| Phase | Technology | Functional Description |
|:---|:---|:---|
| **Data Ingestion** | `Python (requests)` | Consumes live JSON payloads from REST endpoint (`products?limit=100`). |
| **Data Wrangling** | `Pandas` | Flattens nested metadata, cleanses string casing, handles missing attributes. |
| **Feature Engineering** | `Python / NumPy` | Computes `effective_price`, `total_inventory_value_usd`, and `discount_loss_usd`. |
| **Data Warehouse / SQL** | `SQL (ANSI/Postgres)` | Executes multi-table aggregations, ranking, and margin-leakage diagnostics. |
| **Business Intelligence** | `Looker Studio` | Interactive web-based dashboard for executive decision-making. |

---

## 🐍 3. Sample Cleaned Data Structure (Pandas Output)
*Below is a snapshot of the cleansed dataset generated via `df.head().to_markdown(index=False)`:*

| sku_id | product_title | category | retail_price | discount_pct | effective_price | stock | rating | discount_loss_usd |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| SKU-101 | Wireless Headphones | tech-audio | 120.00 | 15.00 | 102.00 | 45 | 4.8 | 810.00 |
| SKU-102 | Ergonomic Office Chair | furniture | 350.00 | 25.00 | 262.50 | 12 | 4.2 | 1050.00 |

---

## 🗄️ 4. Advanced SQL Diagnostic Query
To identify the top categories burning profit margins while maintaining high customer satisfaction, the following diagnostic query was executed:

```sql
-- Executive Diagnostic: Revenue Leakage vs. Organic Product Strength
SELECT 
    category,
    COUNT(*) AS total_skus_in_category,
    ROUND(AVG(rating), 2) AS avg_customer_rating,
    ROUND(SUM(discount_loss_usd), 2) AS total_margin_leakage_usd,
    ROUND(SUM(total_inventory_value_usd), 2) AS net_inventory_value_usd,
    ROUND(
        (SUM(discount_loss_usd) / SUM(SUM(discount_loss_usd)) OVER()) * 100, 
        2
    ) AS pct_share_of_total_leakage
FROM retail_inventory_fact
GROUP BY category
ORDER BY total_margin_leakage_usd DESC
LIMIT 5;
