# Netflix Movies & TV Shows: Data Wrangling and Exploratory Data Analysis

## Gray Interface '26 – Task 1

### Author

Apurva Gautam

---

# Project Overview

The objective of this project is to perform comprehensive Data Wrangling and Exploratory Data Analysis (EDA) on the Netflix Movies and TV Shows dataset. Rather than building predictive models, the focus of this project is on extracting, cleaning, transforming, and visualizing data to uncover meaningful insights about Netflix's content library.

The dataset contains metadata for thousands of Netflix Movies and TV Shows, including information about cast members, directors, countries, genres, descriptions, release dates, and durations.

This project was implemented entirely in Google Colab using Python, Pandas, Matplotlib, Seaborn, Plotly, NetworkX, and WordCloud.

---

# Dataset

Dataset Source:

Netflix Movies and TV Shows Dataset

Kaggle Dataset:
https://www.kaggle.com/datasets/shivamb/netflix-shows

Dataset Size:

* Original Records: 8,807
* Features: 12+

---

# Data Engineering Pipeline

Before creating visualizations, the dataset required extensive cleaning and restructuring.

## 1. Duration Fix

### Problem

The `duration` column contained two completely different types of information:

Examples:

* Movie → "90 min"
* TV Show → "2 Seasons"

Keeping both formats in a single column makes numerical analysis impossible.

### Solution

The numeric portion of the duration was extracted and separated into two independent columns:

* `movie_duration`
* `tv_seasons`

### Why This Was Necessary

This transformation allows independent analysis of:

* Movie runtime distributions
* TV Show season distributions

without mixing incompatible units.

---

## 2. Unnesting Arrays

### Problem

Several columns stored multiple values inside a single cell:

* cast
* director
* country
* listed_in

Example:

India, United States

This format prevents accurate counting and aggregation.

### Solution

The columns were split using commas and expanded into separate rows using Pandas `explode()`.

### Result

| DataFrame        | Rows   |
| ---------------- | ------ |
| Original Dataset | 8,807  |
| Country Data     | 10,850 |
| Cast Data        | 64,951 |
| Director Data    | 9,612  |
| Genre Data       | 19,323 |

### Why This Was Necessary

This enabled:

* Accurate actor frequency analysis
* Country-level analysis
* Director analysis
* Genre analysis
* Collaboration network construction

---

## 3. Datetime Parsing

### Problem

The `date_added` column was stored as plain text.

Example:

September 25, 2021

This format does not support temporal analysis.

### Solution

The column was converted into a proper datetime object.

Additional features extracted:

* `added_year`
* `added_month`
* `added_day`

### Why This Was Necessary

These engineered features enabled:

* Year-wise growth analysis
* Monthly trend analysis
* Weekly content addition analysis

---

# Exploratory Data Analysis & Visualizations

---

## Visualization 1: Distribution of Movies vs TV Shows

### Objective

Understand the overall composition of Netflix's catalog.

### Observation

Movies significantly outnumber TV Shows in the dataset.

### Insight

Netflix's catalog remains movie-heavy, although TV Shows have become increasingly important in recent years.

---

## Visualization 2: Netflix Content Growth Over Time

### Objective

Analyze how Netflix expanded its content library over time.

### Observation

The number of titles added increased dramatically after 2015.

### Insight

Netflix experienced rapid content expansion during the streaming boom period, reflecting aggressive investment in content acquisition and production.

---

## Visualization 3: Movies vs TV Shows Over Time

### Objective

Investigate how Netflix's content strategy changed over the years.

### Observation

Movie additions dominated the early years.

TV Show additions accelerated rapidly after 2015.

### Insight

Netflix gradually shifted toward serialized content, likely due to changing audience preferences and the success of binge-watching formats.

---

## Visualization 4: Monthly Release Trends

### Objective

Identify which months see the highest content additions.

### Observation

Certain months consistently show higher content additions than others.

### Insight

Netflix appears to follow seasonal release strategies, concentrating content additions during specific periods of the year.

---

## Visualization 5: Top Content-Producing Countries

### Objective

Determine which countries contribute the most content.

### Observation

The United States dominates the platform, followed by countries such as India and the United Kingdom.

### Insight

Netflix's content library is heavily influenced by major entertainment industries, while still maintaining international diversity.

---

## Visualization 6: Most Frequent Actors

### Objective

Identify actors appearing most frequently across Netflix titles.

### Observation

A small number of actors appear repeatedly across multiple productions.

### Insight

Certain actors maintain strong and recurring relationships with Netflix productions.

---

## Visualization 7: Most Frequent Directors

### Objective

Identify directors with the largest Netflix presence.

### Observation

Several directors have significantly more titles than others.

### Insight

Netflix appears to collaborate repeatedly with successful directors.

---

## Visualization 8: Genre Distribution

### Objective

Understand which genres dominate Netflix.

### Observation

Drama, Comedy, and International content appear frequently.

### Insight

Netflix prioritizes broad audience appeal while simultaneously expanding global content offerings.

---

## Visualization 9: Genre Trends Heatmap

### Objective

Examine how genre popularity changes over time.

### Observation

Some genres consistently dominate while others emerge only during specific periods.

### Insight

Netflix continuously adapts its content strategy according to audience demand and market trends.

---

## Visualization 10: International Co-Production Network

### Objective

Analyze collaborations between countries.

### Observation

Several countries form strong production partnerships.

### Insight

Netflix increasingly relies on international collaborations to produce globally appealing content.

---

## Visualization 11: International Co-Production Heatmap

### Objective

Identify the strongest country partnerships.

### Observation

A small number of country pairs account for most collaborations.

### Insight

Certain international partnerships serve as major content-production hubs.

---

## Visualization 12: Actor–Director Collaboration Analysis

### Objective

Discover the most frequent actor-director partnerships.

### Observation

Specific actor-director pairs collaborate repeatedly.

### Insight

Successful creative partnerships often result in recurring collaborations.

---

## Visualization 13: Genre Distribution for Top Actors

### Objective

Analyze genre specialization among frequently appearing actors.

### Observation

Some actors appear across many genres while others specialize.

### Insight

Actor versatility varies significantly across the Netflix catalog.

---

## Visualization 14: Genre Combination Analysis

### Objective

Identify the most common genre pairings.

### Observation

Certain genres frequently occur together.

### Insight

Netflix often combines complementary genres to maximize audience reach.

---

## Visualization 15: Horror vs Comedy Word Clouds

### Objective

Compare language used in content descriptions across genres.

### Observation

Distinct vocabulary patterns emerge between Horror and Comedy titles.

### Insight

Genre-specific themes strongly influence marketing descriptions and storytelling approaches.

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab

---

# Key Findings

1. Netflix contains substantially more Movies than TV Shows.
2. Content additions increased dramatically after 2015.
3. TV Shows became an increasingly important component of Netflix's strategy.
4. The United States remains the dominant content producer.
5. International collaborations play a major role in content creation.
6. Drama and Comedy are among the most prevalent genres.
7. Strong actor-director partnerships are visible throughout the dataset.
8. Genre combinations reveal Netflix's strategy of appealing to diverse audiences.
9. Text analysis demonstrates clear thematic differences between genres.

---

# Conclusion

This project demonstrates the importance of data cleaning and exploratory analysis before any machine learning workflow. Through systematic preprocessing and extensive visualization, meaningful patterns were extracted regarding Netflix's content strategy, global reach, collaborative production networks, genre preferences, and growth trends.

The analysis highlights how effective data wrangling transforms raw metadata into actionable insights, reinforcing the principle that understanding the data is often more valuable than immediately applying predictive models.