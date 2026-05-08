# Structured Data Analysis Using NumPy — IPL Case Study

A pure **NumPy-based** data analysis project on the IPL dataset (2008–2020). No Pandas. No shortcuts. Just NumPy, vectorized operations, boolean masking, and core Python — analyzing real cricket data the hard way.

---

##  Project Overview

This project demonstrates how to perform complete structured data analysis using **only NumPy and core Python** — covering data loading, aggregation, ranking, filtering, joining, and scorecard generation — all without Pandas or dictionaries.

---

##  Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3.x** | Core language |
| **NumPy** | All data processing and analysis |
| **np.genfromtxt** | CSV loading |
| **Boolean Masking** | Filtering and grouping |
| **np.argsort** | Sorting and ranking |
| **np.unique** | Grouping and aggregation |

>  Pandas is strictly NOT used anywhere in this project

---

## Project Structure

```
ipl-numpy-analysis/
├── numpy_ipl_analysis.ipynb    # Main analysis notebook
├── matches.csv                 # Match-level IPL data
└── deliveries.csv              # Ball-by-ball delivery data
```

---

##  Dataset

**Source:** [IPL Complete Dataset 2008–2020 — Kaggle](https://www.kaggle.com/datasets/patrickb1912/ipl-complete-dataset-20082020)

### deliveries.csv — Key Columns Used

| Column | Description |
|---|---|
| `match_id` | Unique match identifier |
| `inning` | Inning number |
| `batting_team` | Team currently batting |
| `bowling_team` | Team currently bowling |
| `over` | Over number (1–20) |
| `ball` | Ball number within the over |
| `batter` | Batsman name |
| `bowler` | Bowler name |
| `non_striker` | Non-striker batsman |
| `batsman_runs` | Runs scored on that ball |

---

##  Tasks Overview

### Task 0 — Data Loading and Preprocessing
- Load both CSV files using `np.genfromtxt()`
- Handle headers, missing values, and mixed data types
- Extract relevant columns into separate NumPy arrays:
  `match_ids`, `batting_team`, `batter`, `bowler`, `batsman_runs`, `over`

---

### Task 1 — Total Runs per Match
- Compute total runs scored in each match
- Output: `[(match_id, total_runs), ...]`
- Uses: boolean masking and aggregation (no dictionaries)

---

### Task 2 — Top 5 Batters
- Find top 5 run-scorers across all matches
- Output: `[(player_name, total_runs), ...]`
- Uses: `np.unique()` for grouping, `np.argsort()` for ranking

---

### Task 3 — Strike Rate Calculation
- Formula: `Strike Rate = (Total Runs / Balls Faced) × 100`
- Count balls faced per batter using NumPy
- Output: Strike rate for every batter

---

### Task 4 — Economy Rate of Bowlers
- Formula: `Economy = Runs Conceded / Overs Bowled`
- Convert balls to overs: `balls ÷ 6`
- Aggregate runs conceded per bowler using vectorized ops

---

### Task 5 — Runs per Over (1 to 20)
- Calculate average runs scored in each of the 20 overs
- Output: `[avg_over_1, avg_over_2, ..., avg_over_20]`
- Uses: vectorized boolean masking per over

---

### Task 6 — Boundary Analysis
- Count total **Fours** and **Sixes** across all matches
- Bonus: Identify which batting team hit the most boundaries
- Uses: `np.where(batsman_runs == 4)`, `np.where(batsman_runs == 6)`

---

### Task 7 — Death Overs Analysis (Overs 16–20)
- Filter deliveries in death overs using combined boolean condition:
  `(over >= 16) & (over <= 20)`
- Output: Total runs in death overs + team with highest death over runs

---

### Task 8 — Highest Scoring Match
- Identify the match with the highest total runs
- Output: `(match_id, total_runs)`
- Uses: `np.argmax()` after aggregating per match

---

### Task 9 — Match Winner Approximation
- Determine match winner based on total runs per team per match
- Compare both teams' totals within each match
- Uses: `np.unique()` + boolean masking for each team

---

### Task 10 — Toss Impact Analysis
- Check whether the toss-winning team scores more runs
- Manually join `matches.csv` and `deliveries.csv` using `match_id`
- Compare runs scored by toss winner vs opponent
- Uses: manual NumPy join (no merge/join functions)

---

### Task 11 — Match Scorecard Generation
- Generate a structured scorecard for every match
- Output format:
```
Match 1:
  Team A: 180 runs
  Team B: 175 runs

Match 2:
  Team X: 200 runs
  Team Y: 198 runs
```
- Uses: NumPy grouping and aggregation logic only

---

##  Key NumPy Concepts Used

| Concept | Where Used |
|---|---|
| `np.genfromtxt()` | Loading CSV files |
| `np.unique()` | Grouping by batter, bowler, team |
| `np.where()` | Conditional filtering |
| `np.argsort()` | Sorting and ranking |
| `np.sum()` | Aggregating runs |
| `np.argmax()` | Finding highest values |
| Boolean Masking | Filtering rows by condition |
| Combined Conditions | `(over >= 16) & (over <= 20)` |
| Manual Join | Mapping match_id across two arrays |

---

##  Setup & Installation

### Step 1: Install NumPy
```bash
pip install numpy
```

### Step 2: Download the dataset
 https://www.kaggle.com/datasets/patrickb1912/ipl-complete-dataset-20082020

Place `matches.csv` and `deliveries.csv` in the project folder.

### Step 3: Run the notebook
```bash
jupyter notebook numpy_ipl_analysis.ipynb
```

---

##  Project Rules & Constraints

| Rule | Status |
|---|---|
| No Pandas |  Strictly followed |
| No loops for aggregation |  Vectorized ops used |
| No dictionaries for grouping | NumPy masking used |
| Only NumPy + core Python |  |

---

##  Project Outcomes

By completing this project you will develop:
- Strong understanding of NumPy arrays and vectorized operations
- Ability to perform grouping and aggregation without built-in abstractions
- Expertise in boolean masking and multi-condition filtering
- Skills in sorting and ranking using index arrays
- Experience in manually joining datasets using NumPy
- Confidence working with real-world structured data without high-level libraries

---

##  Author

**Your Name**
- GitHub: [@sushmasree2004](https://github.com/sushmasree2004)

---

##  License

This project is for educational purposes using publicly available IPL cricket data.
