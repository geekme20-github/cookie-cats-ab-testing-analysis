# 🐱 Cookie Cats: A/B Testing for Mobile Game Design

## 📌 Project Overview
This project analyzes an A/B test performed on the popular mobile puzzle game, **Cookie Cats**. The goal was to examine the impact on player retention and engagement when moving the first "gate" (a progression barrier) from **Level 30** to **Level 40**.

## 🛠️ Tech Stack
- **Language:** Python 3.11.8
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, SciPy (Stats)
- **Methodology:** Hypothesis Testing, Bootstrapping, Exploratory Data Analysis (EDA)

## 📊 The Dataset
The dataset contains 90,189 players who installed the game during the A/B test.
- `userid`: Unique player ID.
- `version`: Whether the player was in the Control group (`gate_30`) or Treatment group (`gate_40`).
- `sum_gamerounds`: Total rounds played in the first 14 days.
- `retention_1`: Did the player return 1 day after installing?
- `retention_7`: Did the player return 7 days after installing?



## 🧪 Hypothesis Framework

### 1. Engagement (Game Rounds)
- **H₀**: There is no difference in the distribution of game rounds between versions.
- **Hₐ**: There is a significant difference in the distribution of game rounds.
- **Test:** Mann-Whitney U Test (due to high skewness).

### 2. Retention (1-Day & 7-Day)
- **H₀**: Retention rates are identical for both groups.
- **Hₐ**: Retention rates differ significantly between groups.
- **Test:** Bootstrapping (1,000 resamples) to determine the probability of difference.

## 🧹 Key Data Findings & Cleaning
- **Outlier Detection:** Identified an extreme outlier in the `gate_30` group (49,854 rounds) that threatened to bias the mean. This record was removed.
- **Data Skewness:** The game rounds data was found to be highly skewed (Skewness Coefficient: ~185), justifying the use of non-parametric statistical tests.



[Image of power law distribution graph]


## 📈 Results & Analysis

### 1. Retention Analysis
Through Bootstrapping, we calculated the probability that Level 30 retention is higher than Level 40:
- **1-Day Retention:** ~96% probability that `gate_30` is better.
- **7-Day Retention:** ~99.9% probability that `gate_30` is better.

### 2. Engagement Analysis
The Mann-Whitney U test returned a p-value of **0.0509**, suggesting a marginal but notable difference in distribution, favoring the earlier gate.

## 💡 Final Recommendation
**Do not move the gate to Level 40.**
The data shows a clear decrease in long-term retention when the gate is moved later. This is likely due to "hedonic adaptation"—by forcing a break at Level 30, we prevent player burnout and increase the likelihood of them returning to the game long-term.

---

## 🚀 How to Run the Analysis
2. Ensure you have `pandas`, `seaborn`, and `scipy` installed.
3. Run the Jupyter Notebook `Nb.ipynb`.
