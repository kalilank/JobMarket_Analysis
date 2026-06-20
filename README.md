# ⋆˚꩜｡ AI & Data Science Job Market Analysis ｡꩜˚⋆
> Exploratory analysis and salary prediction on 10,000 job postings across 7 countries — built to answer questions every entry-level data candidate should know.
---
## ₊⊹ Business Questions ⊹₊
This project aims to answer four core questions for entry-level job seekers:
| # | Question |
|---|----------|
| Q1 | Which job titles are most open to entry-level candidates? |
| Q2 | Do larger companies offer more remote opportunities? |
| Q3 | Which industries actively hire Bachelor-level, no-experience candidates? |
| Q4 | What salary can an entry-level candidate realistically expect? |
---
## 𝜗ৎ Dataset 𝜗ৎ 
- **.ᐟ Source:** [AI and Data Science Job Market Dataset](https://huggingface.co/datasets/shree0910/AI-and-Data-Science-Job-Market-Dataset)
- **.ᐟ Size:** 10,000 rows × 18 columns
- **.ᐟ Coverage:** 7 countries, 6 job titles, 6 industries, 2020–2026
- **.ᐟ Note:** Dataset shows signs of synthetic generation (like uniform country salary distributions and perfectly balanced skill columns), these findings should be viewed with that limitation in mind.
---
## ✿ Approach ✿
```
Data Loading ➜ EDA ➜ Feature Engineering ➜ Bivariate Analysis ➜ ML Classification
```
**⬩➤ Key decisions made:**
.ᐟ Retained 4 salary outliers over $200k since they represent valid Senior AI/ML Engineer roles at multinational companies rather than data errors.
.ᐟ Converted binary skill columns from numerical to categorical data types.
.ᐟ Created Low, Mid, and High salary tiers using the 33rd and 67th percentiles to ensure balanced class distributions.
---
## 𖤝 Key Findings 𖤝
### .ᐟ Q1 : Entry-Level Openings by Role
All data roles show comparable entry-level availability with roughly 560 to 600 postings each. ML Engineer and AI Engineer roles lead slightly.
**→ No single role is significantly easier to break into than others.**
### .ᐟ Q2 : Remote by Company Size
Remote opportunities are evenly distributed across all company sizes. Startups lead marginally with 918 postings compared to 844 at Enterprise companies, which is only about an 8% difference.
**→ Don't limit your remote job search to large companies because startups are just as remote-friendly.**
### .ᐟ Q3 : Entry-Level % by Industry
All industries allocate roughly 10% to 12% of their postings to entry-level candidates with Bachelor's degrees. E-commerce leads at 12.4%, while Finance trails slightly at 10.0%.
**→ Your choice of industry matters less than you might expect since the job market is uniformly accessible across sectors.**
### .ᐟ Q4 : Entry-Level Salary by Industry
E-commerce offers the highest median entry salary at $90.7k, and Technology offers the lowest at $83.5k. This is only about an 8% difference.
**→ E-commerce is the clear sweet spot because it offers both the highest entry-level acceptance rate and the highest starting salary.**
---
## [|°ᴗ°|] ML Model : Salary Tier Prediction
**.ᐟ Model:** Random Forest Classifier
**.ᐟ Accuracy:** 92% (balanced classes)
| Class | Precision | Recall | F1 |
|-------|-----------|--------|----|
| Low   | 0.97      | 0.94   | 0.96 |
| Mid   | 0.87      | 0.89   | 0.88 |
| High  | 0.92      | 0.92   | 0.92 |
**Top features driving salary:**
1. `experience_level` (~26%)
2. `job_title` (~24%)
3. `company_size` (~7%)
4. Everything else < 5% each
**→ Role and seniority account for roughly 50% of the salary prediction model, while individual skills like Python and SQL rank at the very bottom. This means that who you are matters more than what tools you know.**
---
## 🛠 Tech Stack 🛠
- Python, Pandas, Matplotlib, Seaborn
- Scikit-learn (RandomForestClassifier, LabelEncoder)
- HuggingFace Datasets
---
##  🗁 Structure 🗁
```
├── jobMarket.ipynb    # Main analysis notebook
└── README.md
```
---
## ✶⋆.˚ Limitations & Next Steps ✶⋆.˚
- Synthetic Data: The dataset is likely synthetic, so real-world validation is highly recommended.
- Model Optimization: The model's performance could be improved by applying hyperparameter tuning techniques like GridSearchCV.
- Future Scope: The next logical step is to run this same analysis on a verified, real-world dataset scraped from platforms like LinkedIn or Glassdoor.