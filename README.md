# Netflix Movies and TV Shows – Exploratory Data Analysis (EDA)

**CodeAlpha Data Analytics Internship – Task 2**

## Objective
Perform Exploratory Data Analysis on the Netflix Movies and TV Shows dataset to understand its structure, find data quality issues, explore trends and patterns, detect anomalies, and communicate insights with statistics and visualizations.

## Dataset
- **Name:** Netflix Movies and TV Shows
- **Source:** https://www.kaggle.com/datasets/shivamb/netflix-shows
- **File used:** `netflix_titles.csv`
- **Columns:** `show_id, type, title, director, cast, country, date_added, release_year, rating, duration, listed_in, description`

> The dataset is **not included** in this repository. Download it from Kaggle (see below).

## Technologies Used
Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook / Google Colab

## Project Structure
```
netflix-eda/
├── Netflix_EDA.ipynb     # the full analysis
├── netflix_titles.csv    # download from Kaggle and place here
├── requirements.txt
└── README.md
```

## Analysis Steps
1. Import libraries
2. Load and inspect the data (head/tail, shape, dtypes, `info()`, `describe()`)
3. Identify data quality issues (missing values, duplicates, inconsistent values)
4. Clean the data on a working copy (strip spaces, fix misplaced values, fill text gaps with "Unknown", convert `date_added` to datetime, split `duration`)
5. Answer seven guiding questions (type split, top years, countries, genres, ratings, trends, issues)
6. Exploratory analysis (summary statistics, relationships, anomalies)
7. Five visualizations (Matplotlib + Seaborn), each with an interpretation
8. Key findings (generated from the data)
9. Conclusion

## How to Run

**Important:** Open and run `Netflix_EDA.ipynb` as a Jupyter notebook. Do **not** run `python Netflix_EDA.ipynb`. The `.ipynb` file is JSON (it uses `null` for empty execution counts). Python will raise `NameError: name 'null' is not defined` if you execute the notebook as a script.

### Option A – VS Code
1. Download `netflix_titles.csv` from the Kaggle link above (free Kaggle account needed; click **Download**, then unzip).
2. Put the CSV in the same folder as `Netflix_EDA.ipynb`.
3. In a terminal in this folder, install libraries:
   ```bash
   pip install -r requirements.txt
   ```
4. Open `Netflix_EDA.ipynb` in VS Code (do not use **Run Python File**).
5. Select the Python kernel (top-right of the notebook, or `Python: Select Interpreter`).
6. Run all cells with **Run All** (or `Notebook: Run All`).

### Option B – Local Jupyter
1. Download `netflix_titles.csv` and place it next to `Netflix_EDA.ipynb`.
2. Install libraries and start Jupyter:
   ```bash
   pip install -r requirements.txt
   jupyter notebook
   ```
3. Open `Netflix_EDA.ipynb` and choose **Kernel → Restart & Run All**.

### Option C – Google Colab
1. Go to https://colab.research.google.com → **File → Upload notebook** → select `Netflix_EDA.ipynb`.
2. Click the folder icon on the left, then the upload icon, and upload `netflix_titles.csv`.
3. In Step 2 of the notebook, set `DATA_PATH = Path("/content/netflix_titles.csv")`.
4. Choose **Runtime → Run all**.

### Changing the file path
Edit the line `DATA_PATH = Path.cwd() / "netflix_titles.csv"` in Step 2 of the notebook.

## Key Findings
> **Fill this in after running the notebook.** Step 8 of the notebook prints a summary generated from the real data – copy those numbers here. Do not write numbers that you have not seen in your own output.

- **Dataset size:** _rows_ × _columns_ (original)
- **Main data quality issues:** _columns with most missing values, duplicates, odd values_
- **Movies vs TV Shows:** _counts and percentages_
- **Release-year trends:** _peak year, share of recent titles_
- **Leading countries / genres:** _top 3 of each_
- **Most common ratings:** _top 3_
- **Anomalies:** _unusual movie lengths, titles added before release, etc._

## Limitations
- The dataset is a snapshot of the catalogue; it contains no viewing or popularity data.
- Several columns (`director`, `cast`, `country`) contain missing values; they are labelled "Unknown" rather than guessed, and "Unknown" is excluded from country rankings.
- Titles with several countries or genres are counted once per country/genre, so those counts add up to more than the number of titles.
- `date_added` and `duration` were not imputed when missing.
- This is a descriptive analysis only – it shows patterns, not causes.
