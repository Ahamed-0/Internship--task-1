# Netflix Movies and TV Shows – Exploratory Data Analysis (EDA)

**CodeAlpha Data Analytics Internship – Task 2**

## Objective
Perform a rigorous Exploratory Data Analysis (EDA) on the Netflix Movies and TV Shows dataset to evaluate catalog structure, diagnose and clean data quality issues, uncover temporal and categorical patterns, detect anomalies, conduct formal statistical hypothesis testing, and communicate evidence-based insights through publication-grade visualizations.

## Dataset
- **Name:** Netflix Movies and TV Shows
- **Source:** [Kaggle - Netflix Movies and TV Shows by Shivam Bansal](https://www.kaggle.com/datasets/shivamb/netflix-shows)
- **File used:** `netflix_titles.csv`
- **Columns (12 original):** `show_id, type, title, director, cast, country, date_added, release_year, rating, duration, listed_in, description`

> The dataset file `netflix_titles.csv` is included directly in this repository root.

## Technologies Used
Python · Pandas · NumPy · SciPy · Matplotlib · Seaborn · Jupyter Notebook

## Project Structure
```
netflix-eda/
├── Netflix_EDA.ipynb        # Complete executed notebook with outputs and charts
├── Netflix_EDA_backup.ipynb # Safety backup copy of the original notebook
├── netflix_titles.csv       # Original dataset (7,787 rows x 12 columns, untouched)
├── requirements.txt         # Project dependencies including pandas, scipy, seaborn
├── README.md                # Project documentation and verified findings
└── README_backup.md         # Safety backup copy of the original README
```

## Analysis Steps
1. **Import Libraries:** Set up core analytical and visualization environments (`pandas`, `numpy`, `scipy.stats`, `matplotlib`, `seaborn`).
2. **Data Inspection:** Evaluate raw dimensions, column data types, missing value percentages, and summary statistics (`head`, `tail`, `info`, `describe`).
3. **Data Quality Audit:** Systematically detect missingness, exact duplicate rows, repeated keys (`show_id`), duration/rating column displacements, and text padding spaces.
4. **Data Cleaning & Feature Engineering:**
   - Strip leading/trailing whitespace across all text columns.
   - Drop identical duplicate rows (if justified).
   - Defensively resolve duration values misplaced in ratings.
   - Impute missing categorical attributes (`director`, `cast`, `country`, `rating`) with `"Unknown"`.
   - Preserve missing date and duration values as `NaT`/`NaN` without artificial fabrication.
   - Convert `date_added` to datetime and engineer 5 helper features: `year_added`, `decade`, `duration_value`, `duration_unit`, and `years_to_add`.
5. **Guiding Exploratory Questions:**
   - Content type split (Movies vs. TV Shows).
   - Peak release years and historical distribution.
   - Top contributing countries (multi-label exploded).
   - Leading genres (multi-label exploded).
   - Common content ratings.
   - Release year vs. Netflix addition timelines.
   - Catalog quality audit summary.
6. **In-Depth Exploratory Analysis & Statistical Hypothesis Testing:**
   - Numerical and categorical variable profiling.
   - Cross-tabulated relationship analysis (ratings by type, movie length across decades).
   - Anomaly detection (IQR duration outliers, negative acquisition intervals).
   - Formal Chi-Square Test of Independence between content type and release period.
7. **Visualizations:** Five publication-ready visualizations with titles, axis labels, value annotations, and analytical interpretations.
8. **Key Findings:** Summarized data-driven metrics directly calculated from the verified dataset.
9. **Conclusion & Limitations:** Executive analytical takeaways paired with transparent methodological constraints.

---

## How to Run

**Important:** Open and run `Netflix_EDA.ipynb` as a Jupyter notebook. Do **not** execute `python Netflix_EDA.ipynb` as a plain script (notebooks contain JSON structure and null tokens).

### Option A – VS Code
1. Ensure `netflix_titles.csv` is in the same directory as `Netflix_EDA.ipynb`.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open `Netflix_EDA.ipynb` in VS Code.
4. Select your Python interpreter/kernel (top-right of the notebook interface).
5. Click **Run All** (or choose **Kernel → Restart & Run All Cells**).

### Option B – Local Jupyter Notebook / JupyterLab
1. Ensure `netflix_titles.csv` is in the workspace folder.
2. Install dependencies and start Jupyter:
   ```bash
   pip install -r requirements.txt
   jupyter notebook
   ```
3. Open `Netflix_EDA.ipynb` and select **Kernel → Restart & Run All**.

### Option C – Google Colab
1. Navigate to [Google Colab](https://colab.research.google.com).
2. Choose **File → Upload notebook** and select `Netflix_EDA.ipynb`.
3. In Colab's file browser on the left, upload `netflix_titles.csv`.
4. In Step 2 of the notebook, update:
   ```python
   DATA_PATH = "/content/netflix_titles.csv"
   ```
5. Click **Runtime → Run all**.

---

## Key Findings (Verified from Notebook Execution)

All findings below are directly generated and validated from the executed `Netflix_EDA.ipynb` notebook:

### 1. Dataset Dimensions & Integrity
- **Original Dimensions:** 7,787 rows × 12 columns.
- **Cleaned Dimensions:** 7,787 rows × 17 columns (includes 5 engineered features: `year_added`, `decade`, `duration_value`, `duration_unit`, and `years_to_add`).
- **Row Retention:** 100% (0 fully duplicate rows detected; 0 duplicate `show_id` values; 0 rows dropped).

### 2. Data Quality & Missingness Profile
- **Director:** 2,389 missing values (30.68%) — highest missingness in the catalog.
- **Cast:** 718 missing values (9.22%).
- **Country:** 507 missing values (6.51%).
- **Date Added:** 10 missing values (0.13%).
- **Rating:** 7 missing values (0.09%).
- **Duration / Misplaced Values:** 0 misplaced durations in the rating column; 0 duration/type mismatches.

### 3. Content Type Distribution
- **Movies:** 5,377 titles (**69.05%**).
- **TV Shows:** 2,410 titles (**30.95%**).
- Netflix's catalog contains approximately 2.23 times more movies than episodic TV shows overall.

### 4. Release Year & Catalog Addition Trends
- **Release Year Span:** 1925 to 2021 (median release year: 2017).
- **Peak Production Year:** 2018 with **1,121 titles** released.
- **Recency Concentration:** **84.9%** of all catalog titles were released in 2010 or later.
- **Addition Acceleration:** Additions surged between 2016 and 2019, peaking in **2019 (2,153 titles)** and **2020 (2,009 titles)**.
- **Acquisition Velocity:** **57.0%** of titles were added to Netflix within their release year (median gap = 1 year).

### 5. Geographical & Genre Leadership
- **Top 3 Production Countries:**
  1. United States: 3,796 title mentions (36.4% of all country mentions)
  2. India: 990 title mentions
  3. United Kingdom: 723 title mentions
- **Top 3 Genres:**
  1. International Movies: 2,437 titles
  2. Dramas: 2,106 titles
  3. Comedies: 1,471 titles

### 6. Audience Ratings Distribution
- **Top 3 Ratings:** TV-MA (2,863 titles; 36.77%), TV-14 (1,931 titles; 24.80%), TV-PG (806 titles; 10.35%).
- Over **61.5%** of Netflix's catalog is targeted at mature or older teen audiences (TV-MA and TV-14).

### 7. Catalog Anomalies
- **Duration Outliers (IQR Method):** 337 movies fall outside the normal length range (43 to 155 minutes).
  - Shortest films: *Silent* (3 min), *Shootout at Lokhandwala* excerpt (4 min).
  - Longest films: *Black Mirror: Bandersnatch* (312 min), *The School of Mischief* (253 min).
- **Temporal Inconsistencies:** 12 titles have `date_added` recorded prior to their `release_year` (e.g. *Hans Teeuwen: Real Rancour*, *Fuller House*), likely due to festival premieres or delayed year metadata tagging.
- **Historical Outliers:** Earliest title is *Pioneers: First Women Filmmakers* (1925), followed by WWII archival documentaries from 1942–1943.

---

## Statistical Hypothesis Testing

### Pearson's Chi-Square Test of Independence
To evaluate whether Netflix's catalog composition has fundamentally evolved over time, we tested for an association between content type (`Movie` vs. `TV Show`) and historical release period (`Before 2000`, `2000–2009`, `2010 onward`).

- **Null Hypothesis ($H_0$):** Content type (`Movie` vs. `TV Show`) is independent of the release period. (The proportions of Movies and TV Shows remain identical across historical eras.)
- **Alternative Hypothesis ($H_1$):** Content type is not independent of the release period. (A statistically significant association exists between content type and release period.)
- **Significance Level ($\alpha$):** 0.05.

#### Observed Contingency Table:
| Content Type | Before 2000 | 2000–2009 | 2010 onward | Total |
| :--- | :---: | :---: | :---: | :---: |
| **Movie** | 402 (89.53%) | 601 (82.55%) | 4,374 (66.17%) | 5,377 |
| **TV Show** | 47 (10.47%) | 127 (17.45%) | 2,236 (33.83%) | 2,410 |
| **Total** | 449 | 728 | 6,610 | 7,787 |

#### Expected Frequencies Table (under $H_0$):
| Content Type | Before 2000 | 2000–2009 | 2010 onward |
| :--- | :---: | :---: | :---: |
| **Movie** | 310.04 | 502.69 | 4,564.27 |
| **TV Show** | 138.96 | 225.31 | 2,045.73 |

#### Test Statistics & Assumption Checks:
- **Chi-Square Statistic ($\chi^2$):** 175.8836
- **Degrees of Freedom ($df$):** 2
- **p-value:** $6.42 \times 10^{-39}$
- **Assumptions Met:** Yes. Minimum expected cell frequency is $138.96 \ge 5$.

#### Conclusion & Analytical Interpretation:
Because the $p$-value ($6.42 \times 10^{-39}$) is drastically smaller than $\alpha = 0.05$, we **reject the null hypothesis ($H_0$)**. There is a statistically significant association between content type and the era of release.
- In pre-2000 titles, Movies constituted **89.53%** of entries, while TV Shows were negligible (**10.47%**).
- In the streaming era (2010 onward), TV Shows surged to **33.83%** of additions.
- **Substantive Insight:** While this statistical test demonstrates a structural association in catalog composition rather than direct causality, it empirically confirms Netflix's modern strategic pivot toward serialized television.

---

## Limitations
1. **Catalog Snapshot without Consumption Metrics:** The dataset captures titles present in the catalog at the time of scraping; it lacks user viewership, watch hours, completion rates, or subscriber popularity ratings.
2. **Missing Information Preserved as "Unknown":** Descriptive columns (`director`, `cast`, `country`) had up to 30.7% missing entries. These were assigned `"Unknown"` rather than dropped to prevent catastrophic row loss, but director and cast analyses remain incomplete.
3. **Multi-Country and Multi-Genre Aggregation:** Titles often list multiple co-producing countries and multiple genres separated by commas. Exploding these lists means titles are counted once per label, reflecting total participation rather than exclusive volume.
4. **Acquisition Anomalies:** 12 titles display negative acquisition intervals (`years_to_add < 0`), likely reflecting metadata recording inconsistencies or delayed broadcast releases.
5. **Association vs. Causation:** All statistical tests describe historical patterns in catalog curation and licensing availability, not viewer preference or causal mechanisms.
