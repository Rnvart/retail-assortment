# Retail Assortment Optimization & Cross-Selling Analysis

## Project Overview
This project analyzes non-food retail sales data to perform a commercial assortment audit. The primary business goal is to segment products into **Core** and **Complementary** assortments to optimize cross-selling strategies, maximize basket sizes, and design checkout-zone product placements.

* **Core Assortment:** High-value, planned, and structural items (e.g., Home & Utility, Kitchenware, Plumbing) that stabilize the foundational revenue.
* **Complementary Assortment:** Fast-moving, impulse-driven, low-cost, or seasonal items (e.g., Gardening, Floristry) ideal for related-item cross-selling and checkout-zone placement.

## Repository Structure
```text
retail-assortment/
├─ data/
│  ├─ vkr_project_retail.csv   # Raw, unedited dataset (6,737 records)
│  └─ cleaned.csv              # Processed retail dataset (6,485 records)
├─ notebooks/
│  └─ Retail_Assortment_Optimization.ipynb
├─ README.md
└─ requirements.txt
```

## Key Analytical Steps & Deliverables

### 1. Advanced Data Cleaning & Pipeline
* Standardized raw multi-format headers to `snake_case`.
* Implemented custom string parsing to convert complex integer formats (`YYYYMMDDHH`) into operational datetimes.
* Executed **Two-Factor Statistical Filtering (99th Percentile)** to isolate and remove extreme wholesale anomalies and system noise (e.g., single-order quantities of 1,000 units), successfully retaining **97.98% of authentic retail transactions** (6,485 valid rows).

### 2. Exploratory Data Analysis (EDA)
* **Seasonality Trends:** Line charts proved a powerful traffic acceleration during late spring and early summer (May–June), driven by Gardening volume peaks. In contrast, sharp isolated revenue milestones occurred in October, December, and February, driven by low-volume but premium holiday decor and gifting.
* **Basket Metrics:** Distribution analysis revealed a right-skewed order value profile. The store operates on high-volume accessible shopping, with a **Median Check Size of 698.00 RUB** and an **Average Check Size of 1,265.07 RUB**.

### 3. Category Enrichment via Web Scraping
* Utilized programmatic web scraping techniques to extract standard retail category trees from external industry sources.
* Implemented automated keyword parsing to enrich the dataset into 5 clean categories (*Gardening, Floristry, For the Home, Plumbing, Other*), dynamically mapping them into Core vs. Complementary groups.

### 4. Statistical Hypothesis Testing
* Conducted a **D’Agostino-Pearson diagnostic**, formally rejecting data normality ($p = 0.0$), steering the methodology away from error-prone T-tests.
* Applied a non-parametric **Mann-Whitney U Test** to evaluate assortment values ($p = 0.0$, Reject $H_0$). This mathematically validated that Core items (Median: 750 RUB) and Complementary items (Median: 120 RUB) represent fundamentally different consumer spending behaviors.

### 5. Recommendation Engine (ML Extension)
* Built a scalable cross-selling model using a binary transaction market-basket matrix and optimized **Pearson correlation analysis**.
* Successfully verified the engine using the store's top item (*Zucchini Seedlings*), exposing high-confidence co-occurrence patterns (correlations up to $0.61$) among related crop variations.

## Core Business Value & Impact
* **Cross-Merchandising:** Grouping matching seedling varieties or lower-cost accessories directly next to primary structural displays can drive a projected 2-3x increase in secondary items per basket.
* **Checkout Optimization:** Utilizing the high baseline velocity of Complementary items (Median: 120 RUB) by positioning them as impulse grabs at checkout registers directly addresses the low 698 RUB median basket size.
