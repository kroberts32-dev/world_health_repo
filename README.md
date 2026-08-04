# World Health Data Analysis — JPG Infant & Maternal Health Briefing

A pandas analysis of country-level health and economic indicators, prepared for JPG, a global infant and maternal health advocacy group. The notebook answers a set of questions posed by the group's founder, Josephina, in preparation for a presentation to the United Nations.

**Author:** Kasandra Roberts

**Course:** GB885 — Assignment 5

**Notebook:** `GB885_Assignment_5_Roberts_K.ipynb`

---

## Scenario

JPG advocates for infant and maternal health outcomes worldwide. Ahead of a UN presentation, the founder needs specific figures pulled from a global health dataset — comparisons across language groups, national rankings, and the relationship between infant mortality and out-of-pocket healthcare spending. This notebook uses pandas to retrieve and calculate those figures.

---

## Data

**Source:** `world-health-data-numbers.csv`
`https://raw.githubusercontent.com/katiegaertner/ML-Fundamentals/main/world-health-data-numbers.csv`

The CSV is read directly from the URL at runtime, so no local data file is required and no data is committed to this repository.

**Shape as loaded:** 194 rows × 18 columns (one row per country)

### Data dictionary

| Column | Description |
| --- | --- |
| `Country` | Country name |
| `Abbreviation` | Two-letter country code (used as the DataFrame index) |
| `Official Language` | Official language of the country |
| `Population` | Total population |
| `Pop_Density` | Population per square kilometer |
| `Land_Area` | Land area in square kilometers |
| `Birth_Rate` | Births per 1,000 people |
| `Fertility_Rate` | Births per woman |
| `Infant mortality_per_1k` | Infant deaths per 1,000 live births |
| `Maternal_Mortality_per_100k` | Maternal deaths per 100,000 live births |
| `Life_Expectancy` | Life expectancy at birth, in years |
| `Physicians_per_1k` | Physicians per 1,000 people |
| `oop_health_exp` | Share of health expenditure paid out of pocket |
| `GDP` | Gross domestic product, in USD |
| `CPI` | Consumer price index |
| `Minimum_Wage` | Minimum wage, in USD |
| `CO2_Emissions` | Carbon dioxide emissions |
| `Unemployment_Rate` | Unemployment rate |

---

## Data preparation

1. Load the CSV from the URL into a pandas DataFrame.
2. Set `Abbreviation` as the DataFrame index and sort the index alphabetically.
3. Drop Vatican City (`VA`), leaving 193 countries.
4. Create a calculated `GDP_per_capita` field as `GDP / Population`.
5. Sort by `Infant mortality_per_1k` and by `GDP_per_capita` as needed for ranking questions.

Filtering for language subsets is done with a boolean mask on `Official Language` rather than by creating a separate copy of the DataFrame.

---

## Business questions and findings

| # | Question | Finding |
| --- | --- | --- |
| 1 | How many rows are in the DataFrame? | 194 |
| 2 | How many columns are in the DataFrame? | 18 |
| 3 | What nation has the index value `DZ`? | Algeria |
| 4 | What is the official language of the nation in the 186th row? | Spanish (Venezuela) |
| 5 | How many countries have Spanish as their official language? | 19 |
| 6 | What is the mean infant mortality per 1,000 in Spanish-speaking countries? | 15.56 |
| 7 | What is the median maternal mortality rate per 100,000 in Spanish-speaking countries? | 65.0 |
| 8 | Which nation has the 4th highest GDP per capita? | Switzerland |
| 9 | What is the average maternal mortality rate per 100,000 across all nations? | 160.39 |
| 10 | What share of healthcare is paid out of pocket in the country with the lowest infant mortality? | Finland (1.4 per 1,000): 0.2 |
| 11 | What share of healthcare is paid out of pocket in the country with the highest infant mortality? | Central African Republic (84.5 per 1,000): 0.4 |

### Interpretation for JPG

The gap between the best and worst performing countries is stark: infant mortality in the Central African Republic is roughly 60 times Finland's rate. Out-of-pocket health spending is twice as high in the higher-mortality country, consistent with the argument that publicly funded care is associated with better infant outcomes — though this notebook establishes association, not causation, and does not control for GDP, physician supply, or other confounders.

Across all nations, the average maternal mortality rate of 160 per 100,000 sits far above the median for Spanish-speaking countries (65), reflecting a small number of countries with very high rates pulling the global average upward.

---

## How to run

1. Clone or download this repository.
2. Open `GB885_Assignment_5_Roberts_K.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
3. Run all cells from top to bottom. Several cells reassign the DataFrame, so running out of order will produce different results.

