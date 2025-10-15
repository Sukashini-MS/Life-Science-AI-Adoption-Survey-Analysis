# 🧠 Life Science AI Adoption Survey Dashboard

## Project Overview
This project focuses on analyzing survey data from Life Science organizations to understand their AI adoption patterns. The goal was to explore how different organizations are adopting AI, their budget allocations, challenges they face, and the perceived impact of AI on their operations.

<img width="1920" height="1019" alt="Life Science Project 15-10-2025 21_16_59" src="https://github.com/user-attachments/assets/32c1f855-32c2-4370-8efb-0a64a59ffc83" />



## 📊 Tools Used
- Jupyter Notebook
- (Python – Pandas, Matplotlib, Seaborn)
- Power BI
- Power Query
- DAX

## Data Cleaning/Preparation
In the initial data preparation phase,the following tasks are performed:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

## Exploratory Data Analysis
EDA involved exploring the Survey data to answer key questions, such as:
### A. General AI Adoption Analysis
1.What percentage of organizations have High / Medium / Low / No AI adoption?

2.How does AI adoption vary by Country or Organization_Type?

3.Correlation between Years_Using_AI and Perceived_Impact_of_AI.

### B. Use Cases & Challenges
4.Most common Primary AI Use Cases across all respondents.

5.Most frequent Biggest Challenges cited by organizations.

6.How do challenges vary by AI adoption level or organization type?

<img width="1920" height="1020" alt="Project explanation and presentation and 1 more page - Personal - Microsoft​ Edge 11-10-2025 22_10_41" src="https://github.com/user-attachments/assets/2ad791c6-1edb-4f73-a1e4-0f80e4f5f88f" />


### C. Budget & Impact
7.Distribution of AI Budgets by organization type or country.

8.Does Budget_for_AI correlate with Perceived_Impact_of_AI?

9.Compare budget ranges across high vs. low adoption organizations.

### D. Future Plans
10.How do future plans differ across adoption levels?

## Data Analysis
- How does AI adoption vary by Country or Organization_type?
```python
# Count of each adoption level per country
country_counts = df.groupby(['Country', 'AI_Adoption_Level']).size().reset_index(name='Count')

# Total orgs per country
country_totals = df.groupby('Country').size().reset_index(name='Total')

# Merge & calculate percentage
country_summary = country_counts.merge(country_totals, on='Country')
country_summary['Percentage'] = (country_summary['Count'] / country_summary['Total']) * 100
country_summary
```
- Most common Primary AI Use Cases across all respondents.
```python
## Split Primary_AI_Use_Cases and count frequencies
AI_level_counts = (
    df["Primary_AI_Use_Cases"]
    .dropna()
    .str.split(",")
    .explode()         # Breaks multiple Cases into separate rows
    .str.strip()       # Remove extra spaces
    .value_counts()
)
```
<img width="1920" height="1020" alt="Project explanation and presentation and 1 more page - Personal - Microsoft​ Edge 11-10-2025 22_09_36" src="https://github.com/user-attachments/assets/2d18918f-46eb-44f3-8d6f-c3488e43f4de" />

- How do Challenges vary by AI adoption level or organization type?
```python
# Split challenges and clean spaces
df_exploded = df.assign(
    Biggest_Challenges = df['Biggest_Challenges']
    .str.split(',')
).explode('Biggest_Challenges')

# Clean whitespace
df_exploded['Biggest_Challenges'] = df_exploded['Biggest_Challenges'].str.strip()

df_exploded.head()
```

## Results
<img width="1920" height="1020" alt="Project explanation and presentation and 1 more page - Personal - Microsoft​ Edge 11-10-2025 22_11_58" src="https://github.com/user-attachments/assets/31f72313-ef1d-42f4-a3eb-9c10f2899d71" />
<img width="1920" height="1020" alt="Project explanation and presentation and 1 more page - Personal - Microsoft​ Edge 11-10-2025 22_12_35" src="https://github.com/user-attachments/assets/6603ee5c-480e-41d0-8797-7a52de530306" />

## 🚀 Key Insights
- 69% of organizations are at medium to high adoption levels, showing a mature AI landscape in the Life Sciences sector.
- Diagnostics, Pharmacovigilance, and Medical Imaging are the top 3 primary AI use cases, each with nearly 400+ respondents using them.
- Most organizations rated AI impact as 4 or 5 out of 5, indicating positive outcomes and strong confidence in AI’s value.
- Pharmaceutical and Academic organizations show the highest levels of AI adoption, ahead of biotech and medical device companies.
- A majority plan to explore new use cases and increase AI budgets, signaling continued investment and expansion.
- Ethical concerns and budget constraints are the top challenges, followed by integration issues and talent shortages.
  
## 🖼️ Dashboard Preview

<img width="1920" height="1019" alt="Life Science Project 15-10-2025 21_15_50" src="https://github.com/user-attachments/assets/0c184a3e-dee3-41aa-b7a1-43b2ea20d7a5" />


## 📂 Files Included
- [CaseStudy1_LifeScienceAI_SurveyData.xlsx](https://github.com/user-attachments/files/22871342/CaseStudy1_LifeScienceAI_SurveyData.xlsx)




