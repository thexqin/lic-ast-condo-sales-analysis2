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

  * **Varied Resale Performance**: We observe a mix of outcomes in the secondary market. Some units demonstrate **price appreciation** over time, reflecting potential capital gains for sellers. Conversely, other units may show a decrease in sale price or relatively stable values, indicating market fluctuations or specific unit characteristics.
      * *Example of Appreciation:* Unit with aptno **1611** shows a sale from $1,862,500 in 2021 to $2,240,000 in 2024, indicating a notable increase in value over approximately three years.
      * *Example of Price Fluctuation/Stability:* Unit with aptno **805** shows a sale price of $1,218,970 in 2021 and $1,180,000 in 2024. This could suggest a slight market adjustment or individual unit factors at play over its holding period.
  * **Holding Periods Vary**: The data illustrates a range of holding periods before resale. Some units are resold relatively quickly, indicating potential short-term investment strategies. Other units show longer holding periods, suggesting buyers intended for a more sustained ownership.
  * **Influence of Corporate Ownership**: The frequent appearance of entities like **BGY CITYVIEW LLC**, **RISLAND NEW YORK LLC**, and **HOLDING 12 SUB LLC** as owners, particularly in earlier years (e.g., 2023, 2024 listings), suggests that a significant number of units were initially acquired by **corporate entities or developers**. These entities likely served as intermediaries, gradually selling units to individual owners.
      * This pattern is evident in cases like the unit currently owned by "JIN, SHIYIFANG," where "BGY CITYVIEW LLC" and "RISLAND NEW YORK LLC" are listed as prior owners. Similarly, the unit owned by "DTC ESTATE LLC" shows "BGY CITYVIEW LLC" and "HOLDING 12 SUB LLC" as previous owners. This multi-step ownership transfer from corporate to individual buyers is a recurring theme.
  * **Dynamic Ownership Changes**: The `check(aptno)` function effectively traces the **ownership history** for each unit across different years (e.g., 2023, 2024, 2025, 2026). This provides a clear chain of title and helps in distinguishing between professional investors/developers and individual homeowners. The varying sale dates for duplicated apartment numbers directly confirm these ownership transfers.

### In-depth Look at Price Appreciation vs. Depreciation:

A closer examination of the individual resale transactions reveals that **price appreciation appears more prevalent than depreciation** within these specific examples from Skyline Tower.

**Units Demonstrating Appreciation:**

  * **Aptno 161 (RUSSI, LUCEDY):** Experienced a significant increase from **$1,862,500 (2021-03-24)** to **$2,240,000 (2024-11-01)**, an appreciation of **$377,500** over approximately 3 years and 7 months.
  * **Aptno 907 (WONG, ADAM GAH JUIN):** Saw its value rise from **$929,255 (2022-07-14)** to **$1,100,000 (2025-05-12)**, an appreciation of **$170,745** over roughly 2 years and 10 months.
  * **Aptno 20 (TANG, KEXIN):** Increased from **$1,645,135 (2023-01-04)** to **$1,817,300 (2024-10-23)**, gaining **$172,165** in approximately 1 year and 9 months.
  * **Aptno 21 (LEE, CHEONG WAI):** Appreciated from **$995,426 (2021-09-30)** to **$1,187,500 (2025-05-09)**, an increase of **$192,074** over about 3 years and 7 months.
  * **Aptno 26 (THERESA LI, ANTHEA):** Showed an increase from **$1,674,875 (2021-05-17)** to **$1,770,000 (2024-09-25)**, resulting in **$95,125** appreciation over approximately 3 years and 4 months.
  * **Aptno 47 (CHEN, ALLIE):** Gained **$30,729**, moving from **$1,764,271 (2021-10-07)** to **$1,795,000 (2024-05-06)** over roughly 2 years and 7 months.
  * **Aptno 28 (CHING, ORENDA ZHAN):** Saw a modest appreciation of **$18,905**, from **$1,156,095 (2021-10-07)** to **$1,175,000 (2024-08-30)** over nearly 3 years.

**Units Exhibiting Depreciation or Minimal Change:**

  * **Aptno 805 (HC805 INC.):** Experienced a depreciation of **-$38,970**, selling for **$1,180,000 (2024-07-30)** after an earlier sale at **$1,218,970 (2021-06-02)**, over approximately 3 years and 2 months.
  * **Aptno 188 (ZHANG, FUYIN):** Showed a substantial decrease of **-$795,630**, from **$2,317,588 (2021-09-17)** to **$1,521,958 (2022-10-18)**, over approximately 1 year and 1 month. This significant drop might warrant further investigation into the nature of the initial transaction (e.g., if it was a bulk transfer or non-arm's length sale) or specific market conditions at the time.
  * **Aptno 160 (ZANG, MENG):** Saw a depreciation of **-$125,285**, going from **$1,735,285 (2021-09-15)** to **$1,610,000 (2023-04-17)** over approximately 1 year and 7 months.

In summary, out of the detailed examples provided in the resale analysis, **seven units demonstrated appreciation**, while **three units showed depreciation**. This pattern suggests that while the Skyline Tower market generally favors appreciation, individual unit performance can be diverse and is influenced by various factors including market timing, holding period, and potentially the nature of the specific transactions.

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
