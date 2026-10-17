# 🎬 Netflix SQL & Content Analysis

## 📌 Project Overview
This project performs an exploratory data analysis on the Netflix Movies and TV Shows dataset using **SQL (SQLite)** and **Python (`pandas`)**. The objective is to apply analytical concepts (such as horizontal trend analysis and common-size distribution) to extract key business insights regarding content strategies.

---

## 🛠️ Tech Stack & Tools
- **Language:** Python 3.x
- **Database:** SQLite3
- **Data Manipulation:** Pandas
- **Platform:** Kaggle Notebooks / Jupyter Notebook

---

## 📊 Key SQL Queries & Business Logic

### 1. Content Mix Analysis (Common-Size Distribution)
Evaluates the proportion of Movies vs. TV Shows in the catalog.
```sql
SELECT 
    type,
    COUNT(*) AS total_count,
    ROUND(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM netflix_titles), 2) AS percentage_share
FROM netflix_titles
GROUP BY type;
```
### 2. Geographic Content Reach (Top 10 Markets)
```sql
SELECT 
    country,
    COUNT(*) AS total_content
FROM netflix_titles
WHERE country IS NOT NULL
GROUP BY country
ORDER BY total_content DESC
LIMIT 10;
```
### 3. Content Addition Trend (Horizontal Analysis Post-2015)
```sql
SELECT 
    release_year,
    COUNT(*) AS total_content_released
FROM netflix_titles
WHERE release_year >= 2015
GROUP BY release_year
ORDER BY release_year DESC;
```
### 4. Audience Classification (Top Target Ratings)
```sql
SELECT 
    rating,
    COUNT(*) AS total_count
FROM netflix_titles
WHERE rating IS NOT NULL
GROUP BY rating
ORDER BY total_count DESC
LIMIT 10;
```
### Key Key Insights
Catalog Structure: Movies dominate the overall library, accounting for the majority share compared to TV Shows.

Geographic Concentration: Core production is centered in top primary markets led by the US and India.

Expansion Strategy: Content production saw significant post-2015 acceleration, reflecting aggressive platform scaling.
