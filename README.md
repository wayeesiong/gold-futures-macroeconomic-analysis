# Macroeconomic Determinants of U.S. Gold Futures Prices

An econometric analysis of how key U.S. macroeconomic variables influence gold futures prices using monthly data from 2014 to 2024.

This project applies regression modelling, diagnostic testing and robust estimation techniques to evaluate the relationship between gold futures prices and major macroeconomic indicators.

---

## Project Overview

Gold is widely regarded as a store of value, portfolio diversifier and safe-haven asset during periods of economic uncertainty.

This study investigates whether movements in major U.S. macroeconomic variables help explain changes in gold futures prices.

The analysis focuses on five potential determinants:

- U.S. Dollar Index
- Consumer Price Index
- M2 Money Supply
- Federal Funds Effective Rate
- Industrial Production Index

The dependent variable is the U.S. gold futures price.

---

## Research Question

**How do major U.S. macroeconomic variables influence U.S. gold futures prices?**

The study examines the individual effects of:

1. U.S. Dollar Index
2. Consumer Price Index
3. Money Supply
4. Interest Rate
5. Industrial Production Index

---

## Data

The analysis uses monthly observations from **March 2014 to March 2024**.

| Variable | Description |
|---|---|
| GF | U.S. Gold Futures Price |
| USD | U.S. Dollar Index |
| CPI | U.S. Consumer Price Index growth |
| MS | M2 Money Supply |
| IR | Federal Funds Effective Rate |
| IPI | U.S. Industrial Production Index |

**Observations:** 121 monthly data points

The underlying dataset is available here:

[View dataset](data/gold-futures-macro-data.xlsx)

---

## Methodology

The empirical analysis was conducted in several stages.

### 1. Ordinary Least Squares

An initial OLS regression was estimated to examine the relationship between gold futures prices and the five macroeconomic variables.

### 2. Multicollinearity Diagnostics

Multicollinearity was examined using:

- Correlation matrix
- Variance Inflation Factor (VIF)

All VIF values remained below 10.

### 3. Heteroscedasticity Diagnostics

The residual variance was examined using:

- Graphical analysis
- Breusch-Pagan-Godfrey test
- White test

Both formal tests indicated the presence of heteroscedasticity.

### 4. Autocorrelation Diagnostics

Serial correlation was evaluated using:

- Residual plots
- Durbin-Watson statistic
- Correlogram
- Breusch-Godfrey Serial Correlation LM test

The initial model displayed positive autocorrelation.

### 5. HAC / Newey-West Standard Errors

Heteroscedasticity and autocorrelation consistent standard errors were applied to improve statistical inference.

### 6. Lagged Dependent-Variable Model

A lagged gold futures price term, **GF(-1)**, was incorporated into the model.

Lag selection was evaluated using:

- Akaike Information Criterion (AIC)
- Hannan-Quinn Criterion (HQC)

The first-order lag specification produced the lowest AIC and HQC and was selected as the preferred model.

---

## Model Development

The analysis followed an iterative model-development process:

**Initial OLS Model**

↓

**Diagnostic Testing**

↓

**Heteroscedasticity and Autocorrelation Identified**

↓

**HAC / Newey-West Adjustment**

↓

**Lagged Dependent Variable Added**

↓

**Final GF(-1) HAC Model**

This approach allowed the model specification to be refined based on the statistical properties of the residuals rather than relying solely on the initial OLS estimates.

---

## Final Model Results

The preferred model includes the first lag of the gold futures price.

| Variable | Coefficient | p-value | Result |
|---|---:|---:|---|
| USD | -2.7134 | 0.0869 | Significant at 10% |
| CPI | -1.7260 | 0.9083 | Not significant |
| MS | 0.0186 | 0.0023 | Significant at 1% |
| IR | 19.2918 | 0.0016 | Significant at 1% |
| IPI | -9.1504 | 0.0002 | Significant at 1% |
| GF(-1) | 0.7734 | 0.0000 | Significant at 1% |

### Model Statistics

- **R²:** 0.9670
- **Adjusted R²:** 0.9653
- **Durbin-Watson:** 2.0186
- **AIC:** 11.0405
- **Breusch-Godfrey p-value:** 0.7065

The final specification substantially improves the treatment of serial correlation compared with the initial model.

---

## Key Findings

### Money Supply

M2 money supply has a statistically significant positive relationship with gold futures prices.

Holding other variables constant, an increase of USD 1 billion in M2 is associated with an approximately **USD 0.0186 increase in the gold futures price**.

### Interest Rate

The Federal Funds Effective Rate has a statistically significant positive relationship with gold futures prices.

A one-percentage-point increase in the federal funds rate is associated with an approximately **USD 19.29 increase in gold futures prices**, holding other variables constant.

### Industrial Production

Industrial production has a statistically significant negative relationship with gold futures prices.

A one-unit increase in the Industrial Production Index is associated with an approximately **USD 9.15 decrease in gold futures prices**, holding other variables constant.

### Lagged Gold Futures Price

The strongest dynamic relationship is observed in the previous month's gold futures price.

A USD 1 increase in the previous month's gold futures price is associated with an approximately **USD 0.77 increase in the current month's price**, holding other variables constant.

### U.S. Dollar Index and CPI

The U.S. Dollar Index is significant only at the 10% level in the final specification, while CPI is statistically insignificant.

---

## Key Takeaway

The results suggest that gold futures prices are influenced not only by contemporary macroeconomic conditions but also strongly by their own recent price behaviour.

After accounting for model diagnostics, **money supply, interest rates, industrial production and the previous month's gold futures price remain statistically significant determinants of gold futures prices**.

---

## Repository Structure

```text
gold-futures-macroeconomic-analysis/
│
├── README.md
│
├── data/
│   ├── README.md
│   └── gold-futures-macro-data.xlsx
│
├── analysis/
│   ├── README.md
│   └── gold-futures-analysis.wf1
│
└── report/
    ├── README.md
    └── gold-futures-macroeconomic-analysis.pdf
