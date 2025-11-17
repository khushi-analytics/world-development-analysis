# World Development Indicators Analysis

## Project Motivation
The World Bank collects and provides economic, social, and development data for countries worldwide.  
This project analyzes the **World Development Indicators (WDI)** dataset to understand the socioeconomic factors that drive GDP per capita, uncover creative insights, and predict economic outcomes using machine learning.  

---

## Installation
This project requires Python 3.x and the following packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```
---

## Repository Structure

```
world-development-analysis/
│
├── README.md # Project documentation
├── .gitignore # Ignore unnecessary files
│
├── data/
│ ├── raw/ # Original CSV files from World Bank
│ │ └── WDI_Data.csv
│ └── processed/ # Cleaned CSV files ready for analysis
│ └── WDI_Data_Processed.csv
│
└── notebooks/
└── world_development_indicators_analysis.ipynb
```

---

## How to Interact with the Project

1. Open `notebooks/wdi_analysis.ipynb` in Jupyter Notebook or Google Colab.  
2. Run all cells sequentially:
   - Data Gathering
   - Data cleaning & Missing Value Handling  
   - Exploratory Data Analysis (EDA)  
   - Prepare Data for Random Forest Modeling
   - Random Forest Model
   - Feature Importance  
   - Predictive Scenario 

Visualizations, tables, and metrics are displayed directly in the notebook.  
Processed datasets can be saved back to `data/processed/` for reproducibility.

---

## Data Cleaning & Preparation

Original WDI data was downloaded in a wide format, with year columns like `[YR2000]`.

### Steps Performed

- Removed `[YRxxxx]` from column names.  
- Converted year columns to numeric.  
- Reshaped data from wide to long format.  
- Pivoted indicators to columns.  
- Renamed columns for readability and machine learning.  
- Handled missing values:
  - Forward-fill and backward-fill within each country.  
  - Remaining NaNs replaced by country-level median.

---

## Exploratory Data Analysis (EDA)

- **Correlation Matrix**: Life expectancy, school enrollment, and poverty rate strongly influence GDP per capita.  
- **Distributions**: GDP per capita is right-skewed; life expectancy and school enrollment roughly normal.  
- **Time Trends**: Life expectancy improved significantly in low-income countries over 2000–2023.  
- **Inequality Analysis**: Positive correlation observed between Gini index, poverty, and unemployment which highlights inequality patterns across countries

---

## Machine Learning Modeling

- **Target variable**: `gdp_per_capita`  
- **Features**: `gdp_growth`, `life_expectancy`, `school_enrollment`, `poverty_rate`, `gini_index`, `inflation`, `unemployment`  
- **Model**: Random Forest Regressor  

### Evaluation Metrics

- R²: 0.97
- MAE: 1374.49

### Feature Importance

Most important features are life expectancy, school enrollment, and poverty rate.

---

## Predictive Scenario Example

**Scenario**:  
Increase life expectancy by 5 years, school enrollment by 10%, and reduce poverty rate by 2%.

**Predicted GDP per capita**: $2649.91 

**Interpretation**:  
Improvements in social indicators drive meaningful GDP growth.

---

## Business Insights

- **Key drivers of GDP per capita**: Life expectancy, school enrollment, poverty rate.  
- **Trends over time**: Low-income countries improving life expectancy and education.  
- **Inequality insights**: Higher Gini index is associated with higher poverty and unemployment.  
- **Resilient countries**: Some countries maintain GDP growth despite inflation fluctuations.  
- **Clustering**: Countries can be grouped by socioeconomic profiles, useful for policy analysis.

---

## Acknowledgements

- World Bank Open Data: [World Development Indicators](https://databank.worldbank.org/source/world-development-indicators)  
- Python libraries: pandas, numpy, matplotlib, seaborn, scikit-learn
