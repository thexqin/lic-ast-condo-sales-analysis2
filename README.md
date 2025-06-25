# Long Island City & Astoria Condo Sales Analysis Part 2: Deep Dive into Skyline Tower Resales 🏙️📈

Welcome to `lic_ast_condo_sales_analysis2`, the continuation of our in-depth exploration into the Long Island City (LIC) and Astoria condominium market. While our [original repository](https://github.com/thexqin/lic-ast-condo-sales-analysis) provided a broad overview and initial insights into residential condo sales, with a primary focus on **Skyline Tower (23-15 44th Drive)**, this second installment takes a granular look at the fascinating world of **resales** within this iconic building.

In this repository, we move beyond initial sales to meticulously analyze how units in Skyline Tower perform on the secondary market. By examining publicly available real estate transaction data, enriching it with additional property details, and focusing specifically on units that have been sold multiple times, we uncover critical insights into:

  * **Price appreciation and depreciation trends** for individual units.
  * **Holding period impacts** on resale values.
  * **The characteristics of units** that are frequently resold versus those that are held long-term.
  * **The dynamic interplay of owner changes** and sale dates.

Whether you're a real estate investor keen on understanding market liquidity and profitability, a data scientist interested in time-series analysis of property values, or simply curious about the investment potential within prime NYC real estate, this repository offers a robust analytical pipeline and compelling findings.

## 🌟 Project Overview

This project builds upon the foundational data loaded in Part 1, `23-15.csv`, which contains comprehensive sales records for Skyline Tower. The core objective of this part is to identify and analyze resales to understand the secondary market dynamics.

### Key Features:

  * **Data Loading and Initial Inspection**: Efficiently loads and displays key information about the `23-15.csv` dataset, confirming data types and non-null counts.
  * **Apartment Number Sorting**: Implements a custom sorting logic for apartment numbers, ensuring proper order, especially for penthouse (PH) units.
  * **Phenomenon of "Bulk Sales"**: Investigates multiple units sold for the exact same "SALE PRICE" on the same "SALE DATE," often indicating bulk purchases by corporate entities or investors. This analysis helps in isolating typical individual unit sales from larger portfolio transactions.
  * **Targeted Data Filtering**: Cleans the dataset by:
      * Filtering out initial large-scale bulk purchases that skew individual resale analysis.
      * Excluding penthouse (PH) units to focus on standard condominium apartments.
      * Applying a price per square foot (`$/sqft`) cap to remove outliers.
      * Removing duplicate entries to ensure each record represents a unique sale event.
  * **Resale Identification and Analysis**: Identifies units that have been sold multiple times by detecting duplicate apartment numbers across the dataset. For these resold units, the analysis highlights:
      * The chronological sequence of sales for each specific apartment.
      * The owners associated with each transaction year, providing a historical ownership trace.
      * Price changes and ownership changes over time, offering insights into individual unit performance.

## 📊 Key Findings: Resale Dynamics in Skyline Tower

The analysis (specifically the resale section) reveals several intriguing patterns and provides concrete examples of property value changes and ownership shifts:

  * **Mixed Resale Performance**: While some units show significant **price appreciation** over time (e.g., unit **404** sold for $492,000 in 2023 and $718,772 in 2023, though the close sale dates suggest a rapid turnover potentially indicating a flip or a unique circumstance), others demonstrate a **decrease in sale price**, or relatively stable values depending on the holding period. This highlights the varied investment outcomes even within the same building.
      * *Example of Appreciation:* Unit with aptno '161' shows a sale from $1,862,500 in 2021 to $2,240,000 in 2024, indicating a notable increase in value.
      * *Example of Slight Decline/Stable:* Unit with aptno '805' saw a sale price of $1,218,970 in 2021 and $1,180,000 in 2024. This could indicate a slight market adjustment or specific unit characteristics.
  * **Short-Term vs. Long-Term Holds**: The data shows instances of relatively **quick resales** (e.g., unit '404' sold twice within months in 2023). This suggests a segment of buyers engaging in shorter-term investment strategies. Other units show longer holding periods before a subsequent sale.
  * **Corporate Ownership and Resales**: The presence of entities like "BGY CITYVIEW LLC," "RISLAND NEW YORK LLC," and "HOLDING 12 SUB LLC" frequently appearing as owners, especially in the early years (2023, 2024), suggests that some units were likely initially acquired by **corporate entities or developers** and then gradually sold off to individual owners.
      * This is evident in cases like `aptno` 'JIN, SHIYIFANG' where BGY CITYVIEW LLC and RISLAND NEW YORK LLC are listed as owners in 2023/2024, before JIN, SHIYIFANG.
      * Similarly, `aptno` 'DTC ESTATE LLC' shows BGY CITYVIEW LLC and HOLDING 12 SUB LLC as prior owners before DTC ESTATE LLC. This pattern of **corporate intermediary ownership** before the final individual buyer is a notable finding.
  * **Dynamic Ownership Changes**: The `check(aptno)` function effectively traces the **ownership history** for each unit, allowing us to see who owned the unit in specific years (e.g., 2023, 2024, 2025, 2026). This is crucial for understanding the chain of title and identifying professional vs. individual owners. The varying sale dates for duplicated `aptno` further confirm these ownership transfers.
  * **Consistency in Property Identifiers**: The consistency of `ZIP CODE`, `YEAR BUILT`, `housenum`, and `streetname` across multiple sales of the same `aptno` validates the accuracy of the resale identification.

## 🚀 Getting Started

To run this analysis, you'll need Python and a few common libraries.

### Prerequisites

  * Python 3.x
  * Jupyter Notebook or JupyterLab (for interactive analysis)
  * Pandas
  * Requests (for interacting with the NYC Open Data API, though pre-loaded data is primarily used)
  * `APP_TOKEN` for the NYC Open Data API (optional, if you wish to extend the `check` function beyond the pre-loaded data)

### Installation

1.  Clone this repository:
    ```bash
    git clone https://github.com/thexqin/lic-ast-condo-sales-analysis2.git
    cd lic-ast-condo-sales-analysis2
    ```
2.  Ensure you have the required CSV data file (`23-15.csv` and `23-15sub.csv`) in the root directory. These files are typically generated or refined from the data acquisition process in `lic_ast_condo_sales_analysis` (Part 1).
3.  Install the necessary Python libraries:
    ```bash
    pip install pandas requests ipython
    ```
4.  If you plan to use the `check` function with the NYC Open Data API, you'll need to set up your `APP_TOKEN`. Replace `{APP_TOKEN}` in the notebook with your actual token or set it as an environment variable.

### Usage

1.  Open the Jupyter Notebook:
    ```bash
    jupyter notebook
    ```
2.  Navigate to and open the notebook for Part 2.
3.  Run the cells sequentially to execute the analysis.

## 📂 Repository Structure

```
.
├── 23-15.csv               # Comprehensive sales data for Skyline Tower (from Part 1)
├── 23-15sub.csv            # Subset of data used for resale analysis (focused on potential resales)
├── skyline_tower_resale_analysis.ipynb # Jupyter Notebook for Part 2 analysis
└── README.md               # This README file
```

## 🤝 Contributing

We welcome contributions to enhance this analysis\! If you have suggestions for new features, improved methodologies, or bug fixes, please feel free to:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'feat: Add new analysis of...'`).
5.  Push to the branch (`git push origin feature/your-feature`).
6.  Open a Pull Request.

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.
