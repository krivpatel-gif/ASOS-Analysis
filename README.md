# ASOS-Analysis
This Python analysis evaluates 13k+ ASOS products to identify "phantom revenue", sales lost to stockouts. Using Pandas, I built a custom function to calculate stockout rates across sizes and mapped brand variations for accuracy. By visualizing price vs. demand, I pinpointed "Winner" brands where inventory expansion would drive the highest growth.
This analysis utilizes **Python (Pandas, Matplotlib, and Seaborn)** to evaluate inventory health and revenue loss for products sold on ASOS. By cleaning the dataset and applying custom functions, the code identifies "phantom revenue"—the potential sales lost due to out-of-stock items.

Here is a breakdown of the technical process and the insights generated:

### 1. Data Cleaning and Brand Identification
The analysis begins by loading a dataset of **13,002 rows**. 
* **Brand Extraction:** Since the "Brand" column was initially messy, a custom function was written to parse the `description` column, extracting brand names based on specific text patterns (e.g., searching for keywords after "by").
* **Normalization:** A mapping dictionary was used to consolidate brand variations (e.g., mapping "Topshop" and "Topshop Curve" into one category) to ensure the analysis accurately reflects market share.

### 2. The "Phantom Revenue" Logic
The core of the analysis is a custom function, `calculate_phantom_revenue`, which quantifies missed opportunities:
* **Stockout Count:** The code parses the `size` string for each product to count how many specific sizes are listed as **"Out of Stock."**
* **Stockout Rate:** It calculates the ratio of unavailable sizes to the total number of sizes offered for that item.
* **Lost Revenue Calculation:** By multiplying the number of out-of-stock sizes by the product's price, the code estimates **"Lost Revenue."** This highlights high-demand items that are currently under-stocked.

### 3. Brand Strategy Analysis
The code aggregates this data at the brand level to categorize market performance:
* **Aggregation:** It calculates the **average price**, **median stockout rate**, and **total lost revenue** for every brand with more than 10 products.
* **Visualization:** A scatter plot is generated (using Seaborn) to visualize the relationship between **Average Price** (x-axis) and **Stockout Rate** (y-axis). 
* **Identifying "Winners":** The code specifically filters for "Winners"—brands that maintain a high stockout rate (above 40%) despite having higher price points (above 60). These brands represent the highest demand and the greatest opportunity for inventory expansion.

### Summary of Results
The final output provides a strategic leaderboard. For example, brands like **Barbour** and **ASOS DESIGN** appear at the top of the "Lost Revenue" list. This tells stakeholders that these specific items have high "phantom revenue," meaning the company could significantly increase its actual sales simply by resolving supply chain or inventory issues for those high-performing products.
