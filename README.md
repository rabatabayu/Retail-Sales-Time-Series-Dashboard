# Retail Sales Time Series Analysis & Forecasting

**Tools:** Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy, Statsmodels, Prophet, Jupyter Notebook, Power BI

**Analysis:** Data Cleaning | Exploratory Data Analysis | Time Series Analysis | Statistical Testing | Forecasting | Business Intelligence

## Project Overview

Retail businesses face challenges in predicting customer demand due to fluctuating sales, seasonal patterns, differences across product categories, and promotional activities.

This project analyzes historical retail sales data from January 2013 to August 2017 to identify demand patterns, evaluate promotional relationships, and develop an accurate forecasting model.

Six forecasting approaches were compared to identify the most suitable model for predicting aggregate retail sales over the next 90 days.

## Project Objectives

1. Identify long-term sales trends, weekly seasonality, and year-end demand patterns.
2. Analyze product family performance and promotional relationships.
3. Evaluate time series characteristics using STL Decomposition, ADF, ACF, and PACF.
4. Compare six forecasting approaches using MAE and RMSE.
5. Generate a 90-day sales forecast and provide actionable recommendations for inventory and operational planning.

## Dataset Information

The original dataset contains:

| Description | Value |
|---|---|
| Total Records | 3,000,888 |
| Total Columns | 6 |
| Unique Stores | 54 |
| Product Families | 33 |
| Historical Period | January 2013 – August 2017 |
| Daily Modeling Observations | 1,688 |

**Main Features:**

- `id`: Unique observation identifier
- `date`: Sales transaction date
- `store_nbr`: Store identifier
- `family`: Product category
- `sales`: Recorded sales quantity
- `onpromotion`: Number of products under promotion

**Note:** The sales variable represents a recorded sales measure, not revenue or profit.

## Data Cleaning & Preparation

- Validated data types, missing values, and duplicate records.
- Converted the date column into datetime format.
- Examined outliers using descriptive statistics, histograms, and boxplots.
- Retained plausible outliers to preserve genuine demand fluctuations.
- Identified four missing calendar dates, all occurring on December 25 between 2013 and 2016.
- Assumed zero sales and zero promotions on those dates to maintain time series continuity, while explicitly marking the holiday assumption.
- Aggregated sales into a continuous daily dataset containing 1,688 observations.

## Exploratory Data Analysis — Key Findings

### 1. Weekly Seasonality

Weekend sales were approximately **39.4% higher than weekday sales**.

Sunday recorded the highest average daily sales of 821,794, while Thursday recorded the lowest at 503,173.

**Business Insight:** Retail demand follows a recurring weekly pattern, indicating opportunities to optimize inventory replenishment and workforce scheduling.

### 2. Year-End Sales Patterns

December consistently recorded above-average daily sales across four consecutive years.

Its average daily sales exceeded the corresponding annual averages by approximately **21.2% to 36.8%**.

**Business Insight:** Year-end demand patterns highlight the importance of preparing inventory and operational capacity ahead of December.

### 3. Product Family Performance

Three product families contributed approximately **63.6% of total recorded sales**:

| Product Family | Contribution |
|---|---:|
| GROCERY I | 32.0% |
| BEVERAGES | 20.2% |
| PRODUCE | 11.4% |

The categories also exhibited different growth trends and demand fluctuations.

**Business Insight:** Category-specific inventory strategies may be more appropriate than applying identical stock policies across all product families.

### 4. Promotion vs. Sales Relationship

Promotional activity showed a positive correlation with sales:

| Analysis | Correlation |
|---|---:|
| Daily Sales vs. Promotion | 0.5749 |
| Weekly Sales vs. Promotion | 0.8008 |
| Weekly Changes After Differencing | 0.0774 |

The substantial decrease after differencing suggests that shared growth trends may contribute to the strong original correlation.

**Business Insight:** Higher promotional activity does not automatically establish incremental sales growth. Additional analysis is required to estimate the causal impact of promotions.

## Time Series Analysis & Statistical Testing

### STL Decomposition

STL decomposition identified three important components:

- **Trend:** Long-term sales generally increased from 2013 to 2017.
- **Seasonality:** Strong recurring weekly sales fluctuations.
- **Residual:** Unexplained fluctuations and several extreme observations.

### ADF Stationarity Test

| Dataset | ADF p-value | Result |
|---|---:|---|
| Original Series | 0.099 | Unit root not rejected |
| First Differencing | <0.001 | Unit root rejected |
| Seasonal Differencing | <0.001 | Unit root rejected |

ACF analysis identified significant correlations at lags 7, 14, 21
