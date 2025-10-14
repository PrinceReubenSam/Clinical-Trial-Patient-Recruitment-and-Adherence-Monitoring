# End-to-End Power BI Project: Clinical Trial Recruitment & Adherence Monitoring

## 1. Project Overview

This repository showcases a complete, end-to-end data analytics project designed to tackle critical inefficiencies in the pharmaceutical research pipeline. The project focuses on creating a robust Power BI solution for **patient recruitment and adherence monitoring** for clinical trials.

The entire project was developed from the ground up. It began with the **programmatic generation of a complex, multi-table relational dataset** using Python, simulating real-world clinical data from various sources. This raw data was then ingested, modeled, and transformed within Power BI to create a suite of powerful, interactive dashboards.

The final solution moves beyond static spreadsheets, providing stakeholders with real-time, actionable insights into recruitment velocity, site performance, and patient adherence. It empowers managers to forecast trial completion dates accurately, mitigate risks proactively, and ultimately, help bring new treatments to market faster.

---

## 2. The Problem Identified

The core challenge in clinical trial management is the lack of a centralized, dynamic, and insightful view of the entire recruitment and adherence funnel. The key problems this project solves include:

*   **Fragmented Data Silos:** In reality, clinical data is not in one clean file. It's spread across multiple systems for patient records, medications, lab results, and trial management (EHR, CTMS, etc.). This makes a holistic analysis extremely difficult.
*   **Lack of Real-Time Visibility:** Static reports make it impossible to track daily or weekly progress, leading to slow responses to emerging issues.
*   **Inefficient Site Performance Management:** Without standardized, integrated metrics, it's difficult to objectively compare clinical sites, preventing the timely implementation of support or corrective action.
*   **Poor Patient Adherence Tracking:** Manually tracking patient compliance across thousands of visits and medication schedules is prone to error and doesn't provide an immediate view of at-risk individuals.

---

## 3. How It Was Solved: An End-to-End Approach

This project was executed from start to finish, mirroring a real-world analytics workflow from data engineering to business intelligence.

### Phase 0: Synthetic Data Generation

The project's foundation is a high-quality, realistic dataset. A Python script was developed to generate a comprehensive, relational dataset for **800 unique patients**.

*   **Technology Used:** Python
*   <img width="1418" height="1090" alt="image" src="https://github.com/user-attachments/assets/4112fa99-ab43-470f-950b-3386725124ae" />

*   **Key Libraries:** `pandas`, `numpy`, `uuid`, `random`, `datetime`.
*   **Methodology:** The script was designed to output 10 distinct but related CSV files, mimicking the normalized structure of a production database from an Electronic Health Record (EHR) or clinical trial management system.
*   **Generated Files:**
    1.  `patients`: Core demographic data for each of the 800 patients.
    2.  `organizations`: Details of the clinical sites/hospitals participating in the trial.
    3.  `providers`: Information on the healthcare providers managing the patients.
    4.  `conditions`: Records of patient diagnoses.
    5.  `encounters`: Logs of every patient visit or "encounter" with a provider.
    6.  `procedures`: Specific medical procedures performed during encounters.
    7.  `observations`: Clinical observations (e.g., lab results, vitals) taken during encounters.
    8.  `medications`: Prescribed medications for patients.
    9.  `trial_recruitment`: The central log of each patient's journey through the trial funnel (screened, enrolled, randomized, etc.).
    10. `adherence_tracking`: A log to track patient adherence to the trial protocol.

### Phase 1: Data Integration and Modeling (Power BI)

This phase was the most critical, involving the transformation of the 10 normalized source files into a clean, efficient analytical model.

*   **Data Ingestion & Transformation (Power Query):** All 10 CSV files were imported into Power BI's Power Query Editor. An extensive series of steps was performed to clean, merge, and prepare the data:
    *   **Data Integration:** Tables were merged to create a holistic view. For example, `patients` data was merged with `trial_recruitment` to link demographics to trial status. `encounters` was enriched with data from `procedures`, `observations`, and `conditions`.
    *   **Data Cleaning:** Ensured data types were correct, handled potential null values, and standardized categorical data.
    *   **Feature Engineering:** Created new calculated columns to support the analysis, such as `Enrollment Duration` (from `trial_recruitment` dates) and `Visit Variance` (from `adherence_tracking`).

*   **Data Modeling (Star Schema):** After transformation, the data was modeled into a **star schema** for optimal query performance and intuitive analysis.
    *   **Fact Tables:** The core of the model was likely built around one or two fact tables, such as `Fact_Enrollment` (derived from `trial_recruitment`) and `Fact_Visits` (derived from `encounters`).
    *   **Dimension Tables:** These fact tables were surrounded by rich dimension tables, including `Dim_Patient`, `Dim_Site` (from `organizations`), `Dim_Provider`, `Dim_Medication`, and a master `Dim_Date` calendar table. This schema is the gold standard for business intelligence and allows for fast, flexible "slicing and dicing" of the data.

### Phase 2: DAX Implementation and KPI Creation

With the robust model in place, Data Analysis Expressions (DAX) were written to calculate the key performance indicators (KPIs). These measures operate on the integrated data model to provide powerful insights.

*   **Recruitment Metrics:** `Total Enrolled`, `Screen Failure Rate`, `Randomization Rate`, `Recruitment Velocity`.
*   **Adherence Metrics:** `Overall Adherence Score`, `Dropout Rate`, and a `Dropout Risk Flag` to identify at-risk patients.

### Phase 3: Dashboard Visualization and Insights

A series of purpose-built dashboards were designed to present the insights in a clear, interactive, and actionable way. The final dashboards allow users to move from a high-level executive summary down to a granular view of a single patient or site.

---

## 4. Repository Contents

This GitHub repository contains all the necessary files to explore this project:

*   **/Project File/**
    *   `Clinical_Trial_Dashboard.pbix`: The complete Power BI file.
*   **/Data/**
    *   This directory contains the **10 CSV files** generated by the Python script, representing the raw, normalized source data for the project: `adherence_tracking.csv`, `conditions.csv`, `encounters.csv`, `medications.csv`, `observations.csv`, `organizations.csv`, `patients.csv`, `procedures.csv`, `providers.csv`, `trial_recruitment.csv`.
*   **/Images/**
    *   Screenshots of the key dashboard pages for a quick preview.
    *   <img width="584" height="330" alt="image" src="https://github.com/user-attachments/assets/f69f665a-8832-48d6-ac44-d39e24468b69" />
    *   <img width="584" height="331" alt="image" src="https://github.com/user-attachments/assets/634c401c-9d73-47a1-9dd9-82941be528f0" />


*   `README.md`: This detailed project explanation.

---

## 5. How To Use This Project

1.  **Clone the repository** to your local machine.
2.  **Ensure you have Power BI Desktop** installed.
3.  **Open the `Clinical_Trial_Dashboard.pbix` file**.
4.  **Explore the dashboards!** All visuals are interactive.
5.  **(Important) Data Source Settings:** The `.pbix` file is configured to look for the CSV files in a specific local path. Upon opening, you may need to update the data source settings in Power BI to point to the location of the `/Data/` folder on your machine. This can be done via `Transform data` -> `Data source settings`.


---

## Connect with Me

This end-to-end project was developed by **Reuben Samuel**. I am passionate about leveraging data engineering and business intelligence to solve complex problems and create actionable insights from raw data.

I'd love to connect with you to discuss data analytics, Power BI development, or potential opportunities. Please feel free to reach out or view my professional profile on LinkedIn.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Reuben%20Samuel-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/reuben-samuel-b55b97234/)
