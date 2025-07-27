## 🌟 Uber Fares Power BI Analysis Project

### 🌟 Names & IDs

* **Name**: Nkurunziza Yves
* **GitHub**: [amos1575](https://github.com/amos1575)
* **Email**: [nziza.amos1@gmail.com](mailto:nziza.amos1@gmail.com)
* **Course**: Introduction to Big Data Analytics (INSY 8413)
* **Instructor**: Eric Maniraguha ([eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw))
* **Assignment Date**: 20 July 2025
* **Groups**: A, B & E
* **Assignment Type**: Data Analysis Project
* **Tool**: Power BI Desktop
* **Dataset**: Uber Fares Dataset (from Kaggle)

---

## 🌀 1. Introduction: Project Overview and Objectives

This project explores the Uber Fares dataset with Power BI to extract insights into ride fares, durations, patterns, and influential variables. We developed an interactive dashboard and a comprehensive analytical report that includes statistical summaries, visual exploration, and business recommendations.

---

## 🧪 2. Methodology: Data Collection and Analysis Approach

### a. Data Understanding and Preparation

* Downloaded the Uber Fares dataset from Kaggle.
* Loaded data into a Pandas DataFrame using Python:

```python
import pandas as pd
df = pd.read_csv('uber_fares.csv')
df.info()
df.describe()
```

* Initial data assessment included checking for nulls and data types.
* Cleaned data by removing rows with missing fare amounts, invalid lat/lon, etc.:

```python
df.dropna(inplace=True)
df = df[df['fare_amount'] > 0]
```

* Exported cleaned data to CSV:

```python
df.to_csv('cleaned_uber_fares.csv', index=False)
```

* Screenshot saved in `screenshots/data_cleaning.png`

### b. Feature Engineering

* Created new time-based columns:

```python
df['pickup_datetime'] = pd.to_datetime(df['pickup_datetime'])
df['hour'] = df['pickup_datetime'].dt.hour
df['day'] = df['pickup_datetime'].dt.day
df['month'] = df['pickup_datetime'].dt.month
df['weekday'] = df['pickup_datetime'].dt.day_name()
```

* Added peak hour indicators and encoded days:

```python
df['peak_hour'] = df['hour'].apply(lambda x: 1 if 7 <= x <= 9 or 17 <= x <= 20 else 0)
```

* Exported enhanced dataset to Power BI.

---

## 📊 3. Analysis: Detailed Findings and Statistical Insights

### a. Descriptive Statistics

* Calculated metrics:

```python
print(df['fare_amount'].describe())
```

* Outliers were identified using box plots in Power BI.

### b. Visualizations and Relationships

* Fare amount vs. distance:

  * Strong positive correlation.
* Fare vs. hour of day:

  * Higher fares during peak commuting times.
* Visualizations: Histograms, time series, box plots shown in `screenshots/visuals/`

### c. DAX Measures in Power BI

```DAX
AvgFare = AVERAGE(UberFares[fare_amount])
TotalRides = COUNT(UberFares[id])
PeakHourRides = CALCULATE(COUNT(UberFares[id]), UberFares[peak_hour] = 1)
```

---

## 🌟 4. Results: Key Discoveries and Pattern Identification

* Peak hours (5–8 PM) showed highest ride frequencies.
* Fares were higher during weekends and holidays.
* Long-distance trips (>10km) accounted for top 15% of fares.
* Patterns consistent across different weekdays.

---

## 🌿 5. Conclusion: Summary of Main Findings

* Ride demand and pricing are strongly time-dependent.
* Distance, peak hours, and weekdays significantly affect fare.
* Strategic factors like time-of-day can influence business optimization.

---

## 💡 6. Recommendations: Data-Driven Business Suggestions

* Introduce dynamic pricing models for peak times.
* Promote ride offers during off-peak hours.
* Optimize driver distribution based on weekday and hour analysis.
* Integrate weather and traffic for enhanced predictive pricing.

---

## 📅 Submission Checklist

* [x] Power BI Dashboard (.pbix file) uploaded
* [x] Cleaned Dataset (.csv) included in `dataset/` folder
* [x] Python EDA script and Jupyter Notebook in `jupyter/` folder
* [x] Screenshots of visualizations, cleaning steps in `screenshots/`
* [x] This README as GitHub project documentation

---

### 🚀 Final Note

The Uber Fares Power BI Project provided hands-on experience with real-world data, from cleaning and feature engineering to DAX-driven visual insights. With a clear structure and interactive visualizations, this project enables smarter pricing strategies and demand forecasting.

> **Deadline:** 25 July 2025, before Sabbath begins
> **Submission Method:** GitHub repo + email to [eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw)

Thank you to our instructor Eric Maniraguha for the guidance and support throughout this insightful assignment! 📚
