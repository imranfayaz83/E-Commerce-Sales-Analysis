# 🛒 E-Commerce Sales & Profit Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?style=for-the-badge&logo=pandas)
![Plotly](https://img.shields.io/badge/Plotly-5.0%2B-3F4F75?style=for-the-badge&logo=plotly)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **An end-to-end exploratory data analysis (EDA) of the Sample Superstore dataset — uncovering revenue trends, profitability patterns, sub-category performance, and customer segment insights through interactive visualizations.**

--
## Project Overview

This project performs a comprehensive **Exploratory Data Analysis (EDA)** on a retail e-commerce dataset (`Sample_Superstore.csv`) to answer critical business questions:

- **When** do peak sales and profits occur throughout the year?
- **Which product categories and sub-categories** drive the most revenue?
- **Which customer segments** are most valuable in terms of sales and profitability?
- **What is the Sales-to-Profit ratio** across segments — and where are margins being lost?

The analysis uses **Plotly** for fully interactive, publication-quality charts and **Pandas** for all data wrangling and transformation tasks.

---

## Key Findings

| Insight | Detail |
|---|---|
|**Peak Sales Month** | **November** — `$352,461` in total sales |
|**Lowest Sales Month** | **February** — `$59,751` in total sales |
|**Highest Profit Month** | **December** — `$43,369` in total profit |
|**Top Revenue Category** | **Technology** — 36.6% of total sales |
|**Most Balanced Category** | Office Supplies (31.3%) and Furniture (32.3%) are nearly equal |
|**Segment Performance** | Sales and Profit analysed across Consumer, Corporate, and Home Office segments |
|**Sales-to-Profit Ratio** | Calculated per segment to identify profit efficiency and margin health |

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3.8+** | Core programming language |
| **Pandas** | Data loading, cleaning, transformation, and feature engineering |
| **Plotly Express** | High-level interactive charts (line, pie, bar) |
| **Plotly Graph Objects** | Custom grouped bar charts with fine-grained control |
| **Plotly Colors** | Consistent pastel color palettes across all visuals |
| **Jupyter Notebook** | Interactive development and presentation environment |

---

## Dataset

**File:** `Sample_Superstore.csv`  
**Encoding:** `latin-1`  
**Domain:** Retail / E-Commerce

The dataset contains transactional records from a fictional US-based superstore, including:

| Column | Description |
|---|---|
| `Order Date` | Date the order was placed |
| `Ship Date` | Date the order was shipped |
| `Category` | High-level product category (Furniture, Office Supplies, Technology) |
| `Sub-Category` | Granular product type (e.g., Chairs, Phones, Binders) |
| `Segment` | Customer segment (Consumer, Corporate, Home Office) |
| `Sales` | Revenue generated per transaction |
| `Profit` | Net profit per transaction |

> **Note:** This is a sample/demo dataset commonly used for business intelligence practice. It is not real commercial data.

---

## Project Structure

```
E-Commerce-Analysis/
│
├── E_Commerce_Analysis.ipynb    # Main analysis notebook
├── Sample_Superstore.csv        # Source dataset
└── README.md                    # Project documentation (this file)
```

---

## Analysis Breakdown

### 1.Data Loading & Initial Exploration
- Loaded the dataset using `pd.read_csv()` with `latin-1` encoding to handle special characters
- Used `.head()`, `.describe()`, and `.info()` to understand shape, data types, and basic statistics

### 2.Data Cleaning & Type Conversion
- Converted `Order Date` and `Ship Date` from `object` to `datetime64` using `pd.to_datetime()`
- Verified type changes with `.info()` post-conversion

### 3.Feature Engineering
Three new time-based columns were derived from `Order Date`:

```python
data['Order Month']        = data['Order Date'].dt.month        # 1–12
data['Order Year']         = data['Order Date'].dt.year         # e.g., 2017
data['Order Days Of Week'] = data['Order Date'].dt.dayofweek    # 0=Monday, 6=Sunday
```

### 4.Sales Analysis
- **Monthly Sales:** Line chart tracking total monthly sales — identifies seasonal peaks and troughs
- **Sales by Category:** Donut pie chart showing proportional revenue split across 3 categories
- **Sales by Sub-Category:** Bar chart drilling into 17 sub-categories for granular comparison

### 5.Profit Analysis
- **Monthly Profit:** Line chart tracking total monthly profit — December peaks while January dips
- **Profit by Category:** Donut pie chart for category-level profit contribution
- **Profit by Sub-Category:** Bar chart revealing which sub-categories are most and least profitable

### 6.Customer Segment Analysis
- **Sales & Profit by Segment:** Grouped bar chart comparing Sales vs. Profit side-by-side across Consumer, Corporate, and Home Office segments
- **Sales-to-Profit Ratio:** Calculated metric per segment to surface profit efficiency:

```python
Sales_Profit_by_Segment['Sales_to_Profit_ratio'] = (
    Sales_Profit_by_Segment['Sales'] / Sales_Profit_by_Segment['Profit']
)
```
> A **higher ratio** signals more revenue is needed to generate each unit of profit — a potential margin concern.

---

## Visualizations

All charts are built with **Plotly** and are fully interactive (hover, zoom, filter):

| Chart | Type | Key Insight |
|---|---|---|
| Monthly Sales Analysis | Line Chart | November peaks at $352K |
| Sales by Category | Donut Pie | Technology leads at 36.6% |
| Sales by Sub-Category | Bar Chart | Granular revenue breakdown |
| Monthly Profit Analysis | Line Chart | December most profitable |
| Profit by Category | Donut Pie | Tech dominates profit too |
| Profit by Sub-Category | Bar Chart | Some sub-categories lose money |
| Sales & Profit by Segment | Grouped Bar | Consumer segment leads overall |
| Sales-to-Profit Ratio | Table | Segment-wise margin efficiency |

---

## Installation & Setup

### Prerequisites
Ensure you have Python 3.8+ installed.

### 1. Clone the Repository
```bash
git clone https://github.com/imranfayaz83/e-commerce-analysis.git
cd e-commerce-analysis
```

### 2. Create a Virtual Environment (Recommended)
```bash
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
```

### 3. Install Dependencies
```bash
pip install pandas plotly jupyter
```

Or install from a requirements file:
```bash
pip install -r requirements.txt
```

**`requirements.txt`:**
```
pandas>=2.0.0
plotly>=5.0.0
jupyter>=1.0.0
```

### 4. Add the Dataset
Place `Sample_Superstore.csv` in the project root directory.

---

## Usage

### Launch Jupyter Notebook
```bash
jupyter notebook E_Commerce_Analysis.ipynb
```

### Run All Cells
In Jupyter: **Kernel → Restart & Run All**

All Plotly charts will render interactively inline within the notebook.

---

## 🔮 Future Improvements

- [ ] **Geographic Analysis** — Map-based visualization of sales/profit by US state and region
- [ ] **Year-over-Year Comparison** — Multi-year trend analysis using `Order Year` column
- [ ] **Discount Impact Analysis** — Study correlation between discount rates and profit margins
- [ ] **Shipping Mode Analysis** — Compare sales and delivery performance across shipping types
- [ ] **RFM Customer Segmentation** — Recency, Frequency, Monetary analysis for customer profiling
- [ ] **Predictive Modelling** — Forecast future sales using time-series models (Prophet, ARIMA)
- [ ] **Dashboard Export** — Convert key charts to a Dash or Streamlit web dashboard

---

## Author

**Imran Fayaz Sheikh**  
Data Analyst | Data Science Professional  
📧 eeeimran0@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/imranfayaz-8b0206286) | [GitHub](https://github.com/imranfayaz83)  
📍 Jammu & Kashmir, India

---

## 📄 License

This project is licensed under the **Imran Fayaz Sheikh** — feel free to use, modify, and distribute with attribution.

---

> ⭐ *If you found this project helpful, consider starring the repository!*
