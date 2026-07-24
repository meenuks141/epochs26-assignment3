# Used Cars Data Science & EDA Project (Epochs '26 - Assignment 3)

## Dataset Overview
This project performs an end-to-end Exploratory Data Analysis (EDA), data cleaning, and feature engineering workflow on a used car dataset (`used_cars.csv`). The dataset contains various attributes regarding car listings, including brand, model, model year, mileage, fuel type, engine specifications, transmission type, exterior/interior colors, accident history, title status, and pricing.

---

## Data Quality Issues Identified
During the initial inspection of the dataset, several data quality issues were uncovered:
1. **Incorrect Data Types:** The `price` and `milage` columns were stored as string objects containing currency symbols (`$`), commas, and units (`mi.`), preventing numerical analysis.
2. **Missing Values:** Missing values were found across categorical columns such as `fuel_type`, `accident`, and `clean_title`.
3. **Outliers:** Pricing data exhibited extreme right-skewness with severe outliers corresponding to ultra-luxury and exotic vehicles.

---

## Cleaning Techniques Applied
* **Type Conversion:** Stripped formatting characters (`$`, `,`, `" mi."`) from `price` and `milage` and converted them into proper `float64` numerical types.
* **Missing Value Imputation:** 
  * Imputed missing values in `fuel_type` using the dataset mode.
  * Filled missing values in `accident` and `clean_title` with standard default categories (`"None reported"` and `"Yes"`, respectively).
* **Duplicate Check:** Verified and confirmed zero duplicate rows in the dataset.

---

## Feature Engineering Performed
Five meaningful features were engineered to enhance future modeling and analysis:
1. **`car_age`:** Calculated the age of the car relative to the current year (`2026 - model_year`).
2. **`price_per_mile`:** Computed cost efficiency by dividing `price` by `milage` (with safety handling for zero division).
3. **`is_luxury`:** A binary flag (`1` or `0`) indicating whether the brand belongs to high-end luxury manufacturers (e.g., Porsche, BMW, Mercedes-Benz, Audi, Lexus).
4. **`milage_per_year`:** Estimated average annual mileage driven by dividing `milage` by `car_age`.
5. **`has_accident`:** Converted text-based accident history into a binary indicator (`1` for reported accidents, `0` for none).

---

## Five Key Insights Obtained
1. **Strong Recency Premium:** Newer vehicle models show a strong positive correlation with pricing—newer cars retain significantly higher resale value.
2. **Mileage Depreciation:** Higher cumulative mileage consistently drives down market price across all standard brands.
3. **Market Dominance of Gasoline:** Gasoline engines make up the overwhelming majority of car listings compared to hybrid, diesel, and flex-fuel alternatives.
4. **Right-Skewed Price Distribution:** The price distribution boxplot highlights extreme right-skewness, identifying a small, elite tier of luxury and sports cars priced multiple standard deviations above the market median.
5. **Impact of Damage History:** A notable portion of listings explicitly report prior accident damage, which directly influences market pricing and title status.

---

## Repository Contents
* `task-3.ipynb`: Jupyter Notebook containing the complete EDA, visualization, cleaning, and feature engineering steps.
* `cleaned_used_cars.csv`: The final processed and cleaned dataset ready for modeling.
* `README.md`: Project documentation and summary report.
