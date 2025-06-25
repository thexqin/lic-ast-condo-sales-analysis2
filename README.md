# Long Island City & Astoria Condo Sales Analysis Part 2: Deep Dive into Skyline Tower Resales 🏙️📈

Welcome to `lic ast condo salesanalysis2`, the continuation of our in-depth exploration into the Long Island City (LIC) and Astoria condominium market. While our [original repository](https://github.com/thexqin/lic-ast-condo-sales-analysis) provided a broad overview and initial insights into residential condo sales, with a primary focus on **Skyline Tower (23-15 44th Drive)**, this second installment takes a granular look at the fascinating world of **resales** within this iconic building.

In this repository, we move beyond initial sales to meticulously analyze how units in Skyline Tower perform on the secondary market. By examining publicly available real estate transaction data, enriching it with additional property details, and focusing specifically on units that have been sold multiple times, we uncover critical insights into:

  * **Price appreciation and depreciation trends** for individual units.
  * **Holding period impacts** on resale values.
  * **The characteristics of units** that are frequently resold versus those that are held long-term.
  * **The dynamic interplay of owner changes** and sale dates.

Whether you're a real estate investor keen on understanding market liquidity and profitability, a data scientist interested in time-series analysis of property values, or simply curious about the investment potential within prime NYC real estate, this repository offers a robust analytical pipeline and compelling findings.

## 🌟 Project Overview

This project builds upon the foundational data loaded in Part 1, `23-15.csv`, which contains comprehensive sales records for Skyline Tower. The core objective of this part is to identify and analyze resales to understand the secondary market dynamics.

### Key Features:

  * **Data Loading and Initial Inspection**: Efficiently loads and displays key information about the `23-15sub.csv` dataset, confirming data types and non-null counts and focusing on duplicated apartment numbers to isolate resale events.
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
  * **Quantitative Resale Metrics**: Calculates `changeM` (holding period in months), `change$` (dollar value change), and `change%` (percentage change) for each resale to provide clear quantitative insights into unit performance.

## 📊 Expanded Key Findings: Resale Dynamics in Skyline Tower

The analysis within the notebook, specifically the resale section, reveals several intriguing patterns and provides concrete examples of property value changes and ownership shifts:

  * **Varied Resale Performance**: We observe a mix of outcomes in the secondary market. Some units demonstrate **price appreciation** over time, reflecting potential capital gains for sellers. Conversely, other units may show a decrease in sale price or relatively stable values, indicating market fluctuations or specific unit characteristics.
      * *Example of Appreciation:* Unit with aptno **1611** shows a sale from **$1,862,500 (2021-03-24)** to **$2,240,000 (2024-11-01)**, indicating a notable increase in value over approximately 43.9 months.
      * *Example of Price Fluctuation/Stability:* Unit with aptno **805** shows a sale price of **$1,218,970 (2021-06-02)** and **$1,180,000 (2024-07-30)**, indicating a slight depreciation of **-$38,970** over approximately 38.5 months.
  * **Holding Periods Vary**: The data illustrates a range of holding periods before resale, from a minimum of around **13.2 months** to a maximum of approximately **47.2 months**, with an average holding period of around **33.2 months**. This suggests a mix of short-term and medium-term investment strategies among owners.
  * **Influence of Corporate Ownership**: The frequent appearance of entities like **BGY CITYVIEW LLC**, **RISLAND NEW YORK LLC**, and **HOLDING 12 SUB LLC** as owners, particularly in earlier years (e.g., 2023, 2024 listings), suggests that a significant number of units were initially acquired by **corporate entities or developers**. These entities likely served as intermediaries, gradually selling units to individual owners.
      * This pattern is evident in cases like the unit currently owned by "ZENG, ZHILIN," where "BGY CITYVIEW LLC" and "HOLDING 12 SUB LLC" are listed as prior owners. This multi-step ownership transfer from corporate to individual buyers is a recurring theme.
  * **Dynamic Ownership Changes**: The `check(aptno)` function effectively traces the **ownership history** for each unit across different years (e.g., 2023, 2024, 2025, 2026). This provides a clear chain of title and helps in distinguishing between professional investors/developers and individual homeowners. The varying sale dates for duplicated apartment numbers directly confirm these ownership transfers.

### In-depth Look at Price Appreciation vs. Depreciation:

A closer examination of the 16 identified resale transactions reveals that **price appreciation is significantly more prevalent than depreciation** within these specific examples from Skyline Tower.

**Overall Performance Metrics:**

  * The **mean percentage change (`change%`) is approximately 1.05**, indicating an average price increase of about **5.27%** per resale transaction.
  * The **median percentage change is 1.052**, further supporting a positive central tendency in price changes.
  * The **average dollar value change (`change$`) is approximately $46,582**, reflecting a net gain across the resales.

**Appreciation vs. Depreciation Count:**

  * Out of 16 resale transactions, **12 units (75%) demonstrated appreciation** (where `change% > 1`).
  * Only **4 units (25%) exhibited depreciation** (where `change% < 1`).

### Detailed Examples:

**Units Demonstrating Notable Appreciation:**

  * **Aptno 1611 (RUSSI, LUCEDY):** Experienced a significant increase of **$377,500**, with a **20.27%** gain over approximately 43.9 months.
  * **Aptno 2202 (ZKC SKYLINE LLC):** Saw its value rise by **$308,301**, a **21.24%** increase over approximately 47.2 months.
  * **Aptno 3609 (LEE, CHEONG WAI):** Gained **$192,074**, representing an **19.30%** appreciation over approximately 43.9 months.
  * **Aptno 907 (WONG, ADAM GAH JUIN):** Increased by **$170,745**, a **18.37%** gain over approximately 34.4 months.

**Units Exhibiting Depreciation:**

  * **Aptno 4311 (ZHANG, FUYIN):** Showed the most significant depreciation, a loss of **-$795,630**, equating to a **-34.33%** change over a relatively short period of 13.2 months. This substantial drop warrants further scrutiny, as it could indicate a non-market transaction or specific distressed sale conditions rather than a typical market decline.
  * **Aptno 4412 (ZANG, MENG):** Experienced a depreciation of **-$125,285**, or **-7.22%**, over approximately 19.3 months.
  * **Aptno 805 (HC805 INC.):** Saw a slight depreciation of **-$38,970**, a **-3.20%** change over approximately 38.5 months.
  * **Aptno 2909 (CHUNG, YOUNG):** Showed a negligible depreciation of **-$96**, representing a **-0.01%** change over approximately 28.4 months, essentially remaining flat.

In conclusion, the Skyline Tower resale market, based on this dataset, demonstrates a clear trend of **appreciation for the majority of units**. While individual cases of depreciation exist, some are minimal, and the most significant depreciation could be an outlier requiring further context. The positive average percentage change and the higher number of appreciating units suggest a healthy secondary market for condominiums in this building.

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
