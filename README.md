# Retail Assortment Optimization

## Project Overview
This project analyzes retail sales data (Oct 2018 – Oct 2019) from a non-food retail store.  
The goal is to identify **core** and **complementary** product assortments, uncover sales patterns, and generate actionable business recommendations.

- **Core assortment**: stable, high-value items (e.g., Home, Utility).  
- **Complementary assortment**: impulse-driven items (e.g., Gardening, Floristics, Other) suitable for checkout placement and cross-selling.  

## Key Steps
1. **Data Cleaning & Preparation**
   - Removed duplicates, missing values, anomalies (~19.28% of rows dropped)
   - Converted types and added `total_price` feature

2. **Data Enrichment**
   - Product categories added via web scraping + manual mapping

3. **Exploratory Data Analysis (EDA)**
   - Seasonality: peaks in May–July, high-value orders in Oct, Dec, Feb, Jun
   - Distribution analysis: most sales from affordable items
   - Category analysis: Gardening & Floristics dominate in volume; Home & Utility dominate in value

4. **Statistical Analysis**
   - Normality tests (D’Agostino)
   - Mann–Whitney test confirmed significant differences between core vs complementary assortments

5. **Machine Learning Extensions**
   - **Clustering**: segmented products by sales, price, and demand patterns
   - **Market Basket Analysis**: identified cross-selling opportunities (e.g., tools + gloves, pots + fertilizers)

6. **Business Insights**
   - Place complementary items at checkout
   - Bundle products for cross-selling
   - Adjust stock based on seasonality
  
This project demonstrates a **full-cycle analysis**: from raw data cleaning to business insights.

## Results
- Clean dataset: **5438 valid orders** (from 6737 raw, ~19.3% anomalies removed)
- Complementary items outsell core items in **volume (+866 units)**
- Recommendations for checkout, bundling, and seasonal promotions

## Repository Structure
```
retail-assortment/
├─ data/
│  ├─ raw.csv
│  └─ cleaned.csv
├─ notebooks/
│  └─ Retail_Assortment_Optimization.ipynb
├─ plots/
│  └─ *.png (exported charts)
├─ presentation/
│  └─ Retail_Assortment_Optimization_Presentation.pptx
├─ README.md
└─ requirements.txt
```

## Tools & Skills
- **Python**: pandas, numpy, matplotlib, seaborn, scikit-learn, scipy, mlxtend
- **SQL**: data querying (notebook examples not included here)
- **Web scraping**: category enrichment
- **Statistical testing**: Shapiro-Wilk, KS, Mann–Whitney, effect size
- **ML**: clustering, association rules (apriori)

## How to Run
```bash
pip install -r requirements.txt
jupyter notebook notebooks/Retail_Assortment_Optimization.ipynb
```

## Business Impact
- Improved checkout strategy → higher basket size  
- Bundling opportunities → estimated +3–5% seasonal uplift  
- Seasonal targeting → reduced stock-outs and dead stock  
