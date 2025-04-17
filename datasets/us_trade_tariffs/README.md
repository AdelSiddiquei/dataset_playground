# US Tariffs & Trade

## Challenge 1: Trade Overview Basics (15 mins)  
This challenge tests your ability to parse and summarize a tabular dataset using basic pandas operations.

### 💡 Problem  
**Data:** https://www.kaggle.com/datasets/danielcalvoglez/us-tariffs-2025/data  
You're given a dataset with detailed information about trade between the US and other countries, including exports, imports, and trade deficit/surplus values. One version of the dataset also includes population figures.

Your task is to:
1. Load the dataset and display the first 5 rows.
2. Clean column names to follow snake_case using `str.lower()` and `str.replace()`.
3. Convert monetary values (`us_2024_deficit`, `us_2024_exports`, `us_2024_imports_(customs_basis)`) to numeric, removing `$` signs and commas.
4. Identify the 5 countries with the highest `us_2024_exports`.
5. Calculate the total US trade balance across all countries by summing `us_2024_exports - us_2024_imports_(customs_basis)`.

---

## Challenge 2: Tariff-Based Trade Summary (20 mins)  
This challenge focuses on using `.groupby()` and `.agg()` for summarization, as well as multi-index sorting.

### 💡 Problem  
Some countries may share similar trade characteristics. Grouping by tariff-related fields can reveal patterns.

Your task is to:
1. Group the data by `trump_tariffs_alleged`.
2. Use `.agg()` to compute:
   - Total `us_2024_exports`  
   - Total `us_2024_imports_customs_basis`  
   - Mean `us_2024_deficit`  
   - Count of countries in each group
3. Sort the result by total exports (descending), then by total imports (ascending).

---

## Challenge 3: Trade Balance Classification (25 mins)  
This challenge tests your ability to create new columns using conditional logic with `numpy.where()`.

### 💡 Problem  
You're now asked to classify each country's trade balance status.

Your task is to:
1. Create a new column `trade_balance_flag` using `np.where()`:
   - `"Surplus"` if `us_2024_exports` > `us_2024_imports_customs_basis`  
   - `"Deficit"` if `us_2024_imports_customs_basis` > `us_2024_exports`  
   - `"Balanced"` otherwise
2. Count the number of countries in each trade balance category.
3. Plot a bar chart showing the number of countries per `trade_balance_flag`.

---

## Challenge 4: Population-Adjusted Trade (30 mins)  
This challenge explores calculated fields, null-handling, and per capita analysis.

> ⚠️ This task uses the version of the dataset with the `population` column.

### 💡 Problem  
You want to compare trade values on a per-person basis, but some rows have missing population data.

Your task is to:
1. Filter out rows where `population` is null or zero.
2. Create two new columns:
   - `exports_per_capita` = `us_2024_exports` / `population`  
   - `imports_per_capita` = `us_2024_imports_customs_basis` / `population`
3. Sort the data using a multi-index:
   - First by `exports_per_capita` (descending)  
   - Then by `imports_per_capita` (ascending)
4. Identify the top 5 countries by `exports_per_capita`.
5. Create a scatter plot of `exports_per_capita` vs. `imports_per_capita`, color-coded by `trade_balance_flag`.

---

## Challenge 5: Visualizing Trade Dynamics (Optional, 15–20 mins)  
This bonus challenge checks your ability to create effective visuals using matplotlib.

### 💡 Problem  
You’ve been asked to summarize US trade insights in visual format.

Your task is to:
1. Create a pie chart showing the share of total US exports accounted for by the top 5 countries.
2. Create a horizontal bar chart comparing `us_2024_exports` and `us_2024_imports_customs_basis` for the top 10 countries by total trade volume.
3. Customize your plots with titles, axis labels, and legends to make them presentation-ready.
