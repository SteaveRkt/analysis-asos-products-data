# ASOS Products Data Analysis & Stock Optimization

This repository contains a data science project focused on analyzing an ASOS product dataset containing **30,845 items** across 9 key features (`url`, `name`, `size`, `category`, `price`, `color`, `sku`, `description`, `images`). 

The main objective of this analysis is to identify market demand dynamics, evaluate **stockout rates**, calculate **phantom (lost) revenue**, and define actionable inventory and pricing strategies using quadrant-based data segmentation.

## Business Insights Summary
The core of this project relies on a scatterplot matrix that segments fashion brands into four distinct categories based on their **Average Price** and **Stockout Rate**, revealing significant revenue-generation opportunities:

*   **Top-Right (The Winners):** Brands like *AllSaints* and *Mango* exhibit high prices and high demand but suffer from high stockout rates. Optimizing and expanding their inventory is our top priority to avoid leaving money on the table.
*   **Top-Left (Volume Drivers):** Lower prices but higher demand. We should double the stock for these products and aggressively adjust their prices upward to capitalize on market traction.
*   **Bottom-Right (Dead Stock):** High prices but low demand. These items tie up working capital; they should be liquidated immediately through targeted promotions.
*   **Bottom-Left (Underperformers):** Low price and low demand. These products bring minimal value and require no further investment.

---

## Tech Stack & Library Requirements
The analysis is built entirely in Python using Jupyter/Google Colab notebooks. The required libraries to run the script are:

*   **Data Manipulation:** `pandas`, `numpy`
*   **Data Visualization:** `matplotlib`, `seaborn`
*   **File Path Management:** `pathlib`

To install the dependencies, run:
```bash
pip install pandas numpy matplotlib seaborn
```

---

##  Project Workflow & Features

### 1. Data Cleaning & Feature Engineering
*   Dynamic dataset discovery and file loading using `.rglob()` to handle local execution paths safely.
*   Data type conversion, explicitly formatting `price` columns to numerical values while handling `NaN` and missing price nodes.
*   Extracted the core `brand` attribute from raw `category` strings.
*   Mapped corrupted or generic brand labels into unified names (e.g., mapping "New" to "New Look" or "TopshopWelcome" to "Topshop").

### 2. Stockout & Phantom Revenue Computation
A customized analytical algorithm was designed to parse the raw string data inside the `size` objects, counting total available sizes versus sizes explicitly flagged as **"Out of Stock"**.
*   **Stockout Rate Formula:** `Total Out of Stock Sizes / Total Unique Sizes`
*   **Lost Revenue Formula:** `Product Base Price * Stockout Count`

### 3. Strategy Visualization
Using a customized `seaborn.scatterplot`, the dataset was aggregated by brand to calculate the median price threshold and isolate the top "Winners" leaking the most revenue (such as *Barbour*, *AllSaints*, and *Topshop* premium leather lines).

---

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/SteaveRkt/analysis-asos-products-data.git
   ```
2. Place your raw dataset named `products_asos.csv` inside your project directory tree.
3. Open the Jupyter Notebook / Google Colab file and run all cells sequentially.

---

