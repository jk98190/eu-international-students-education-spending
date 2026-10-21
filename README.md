# EU International Students vs Education Spending

Does the rise in international students in the EU come mainly from regions that invest less in education? This project tests that hypothesis using correlation analysis and simple machine learning in Python.

## Hypothesis

1. The number of international students in the EU has grown in recent years.
2. The largest communities come from Africa and South Asia.
3. These students come from regions with lower education investment (and a weaker economic position) than the EU.

## Project structure

```
.
├── cleaning.py               # Cleans the raw CSV files and saves clean_*.csv
├── hypothesis_analysis.py    # Trend, correlation and regression analysis
└── README.md
```

## Data

| File | Description |
|---|---|
| `government-spending-on-education-as-a-share-of-gdp.csv` | Government education spending (% of GDP) by country and year |
| `european_university_students.csv` | University students in European countries by sector, sex and education level |
| `european_international_students_quickstart.csv` | International students per European country, with breakdown by origin region |
| `economic_indicators_clean.csv` | Country-level economic indicator by year (World Bank wide format) |

Add your data sources and download links here.

## Method

1. **Cleaning** (`cleaning.py`): renames columns, removes duplicates and missing values, converts dates, and drops aggregate rows from the EU student file.
2. **Trend analysis**: yearly totals, growth by origin (Africa, Asia, India, China, Europe) and each origin's share of the total.
3. **Regional comparison**: average education spending and median economic indicator for Africa, South Asia and the EU, each shown as a percentage of the EU level. Countries are matched on ISO3 codes.
4. **Correlation analysis**: Pearson and Spearman correlations between students sent and origin-region spending or economic indicator, on levels and on year-over-year changes, plus a correlation heatmap.
5. **Machine learning** (scikit-learn linear regression):
   - Trend and 3-year forecast per origin group.
   - Students sent against one predictor at a time.
   - Students sent against spending and economic indicator together (standardised coefficients).

## How to run

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
python cleaning.py
python hypothesis_analysis.py
```

File paths are set to a local folder in both scripts. Change them to match where your data is stored.

## Limitations

- The international students file gives origin by **region only**, so regional averages stand in for the countries students actually come from. `from_india` is used as a proxy for South Asia.
- The datasets may overlap on only a few years, which limits statistical power.
- The number of countries reporting can change between years, which can affect yearly totals.
- Correlation does not show causation. Other factors, such as tuition cost, scholarships and visa rules, are not modelled.

## Tools

Python, pandas, NumPy, Matplotlib, Seaborn, SciPy, scikit-learn
