# 📱 Indian Kids Screen Time — Data Cleaning & Analysis

> **85.5% of kids in this dataset exceeded the recommended daily screen time limit.**  
> That was the first number I saw after cleaning the data. Everything else followed from there.

This project is a full end-to-end data analysis pipeline — raw CSV to cleaned dataset to visual insights — built as part of my data analytics internship. The dataset covers **9,712 children aged 8–18** across Urban and Rural India, tracking daily screen time, device usage, and reported health impacts.

---

## 📂 Project Structure

```
├── Indian_Kids_Screen_Time_Analysis.ipynb   # main notebook (run this)
├── Indian_Kids_Screen_Time.csv              # raw dataset
├── Indian_Kids_Screen_Time_Cleaned.csv      # output after cleaning
└── README.md
```

---

## 🔍 What's in the Notebook

The notebook is split into five sections:

**1. First Look** — shape, dtypes, null counts, duplicates. No cleaning yet, just understanding what we're working with.

**2. Data Cleaning** — four deliberate steps, each with a reason:
- Removed 44 duplicate rows
- Filled `Health_Impacts` nulls with `"None Reported"` instead of dropping them — a null here means no impact was reported, not a data error. Dropping would've removed a third of the dataset.
- Dropped 226 rows where screen time = 0 but `Exceeded_Recommended_Limit = True` — that's a contradiction, not an outlier.
- Flagged (not removed) extreme screen time values above the IQR upper bound — they're unusual but internally consistent.

**3. Visualizations** — seven charts, each answering a specific question:
- Does screen time increase with age?
- Which device type leads to the most usage?
- Urban vs Rural — is location actually a factor?
- How does the educational-to-recreational ratio change across age groups?
- What health impacts are being reported, and how often?
- Are there gender differences in screen time or health outcomes?

**4. Insights** — findings backed by code, not just assertions.

**5. Conclusion** — what the data says, what it doesn't say, and what I'd do next.

---

## 📊 Key Findings

- **85.5% of kids exceeded** the recommended screen time limit — this is the norm, not the exception.
- Screen time peaks at **age 17 (avg 4.56 hrs/day)** — the increase across age groups is gradual but consistent.
- **Urban vs Rural gap is nearly zero** (4.34 vs 4.37 hrs/day). Rural India isn't lagging behind on screen exposure.
- **Less than 43% of screen time is educational** at the median — across all age groups, most screen use is recreational.
- **Kids who exceeded the limit reported more health impacts on average**, particularly poor sleep and eye strain. The association exists, though correlation ≠ causation.
- **Device type barely matters** — smartphones, tablets, TVs, and laptops all cluster around the same average daily usage. The problem isn't the device.

---

## 🛠 Tools & Libraries

- Python 3
- pandas — data loading, cleaning, groupby analysis
- matplotlib + seaborn — all visualizations
- Jupyter Notebook

Install dependencies:
```bash
pip install pandas matplotlib seaborn jupyter
```

Run the notebook:
```bash
jupyter notebook Indian_Kids_Screen_Time_Analysis.ipynb
```

---

## 💡 One Thing Worth Calling Out

The `Health_Impacts` column stores multiple conditions in a single string — like `"Poor Sleep, Anxiety, Eye Strain"`. Most people would just run `.value_counts()` on it and get 15 weird combined labels. I split and counted each condition individually, which gives a much cleaner picture of what's actually being reported and how often.

---

## 📌 Dataset

The dataset covers children aged 8–18 across India, with columns for:
`Age`, `Gender`, `Avg_Daily_Screen_Time_hr`, `Primary_Device`, `Exceeded_Recommended_Limit`, `Educational_to_Recreational_Ratio`, `Health_Impacts`, `Urban_or_Rural`

---

## 👤 About

Built by Sarthak as part of a data analytics internship project.  
Feel free to fork, use, or suggest improvements.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](www.linkedin.com/in/sarthak-chauhan-13b417298)
