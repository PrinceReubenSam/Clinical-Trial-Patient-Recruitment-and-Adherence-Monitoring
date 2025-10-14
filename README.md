# Power BI for Clinical Trial Recruitment & Adherence Monitoring

## 1. Project Overview

This project provides a comprehensive Power BI solution designed to tackle critical inefficiencies in the pharmaceutical research pipeline, specifically focusing on **patient recruitment and adherence monitoring** for clinical trials.

Traditionally, trial management relies on static spreadsheets, which leads to reactive problem-solving, costly delays, and a lack of clear, real-time insights. Delays in recruitment alone can cost companies millions and significantly postpone the availability of vital new treatments.

This interactive dashboard transforms the process by providing trial managers, executives, and site coordinators with real-time, actionable insights into:
*   **Recruitment Velocity:** Tracking the pace of patient enrollment against targets.
*   **Site Performance:** Comparing and evaluating the effectiveness of different clinical sites.
*   **Patient Adherence:** Monitoring patient compliance with visit schedules and medication protocols.
*   **Dropout & Failure Analysis:** Identifying trends in patient dropouts and screen failures to mitigate risks proactively.

The solution empowers stakeholders to move from a reactive to a proactive management style, enabling them to identify bottlenecks, forecast trial completion dates more accurately, and ultimately, bring new treatments to market faster.

---

## 2. The Problem Identified

The core challenge in clinical trial management is the lack of a centralized, dynamic, and insightful view of the entire recruitment and adherence funnel. The key problems addressed by this project include:

*   **Lack of Real-Time Visibility:** Static reports make it impossible to track daily or weekly progress, leading to slow responses to emerging issues like underperforming sites or high dropout rates.
*   **Inefficient Site Performance Management:** Without standardized metrics, it's difficult to objectively identify which clinical sites are excelling and which are struggling, preventing the timely implementation of support or corrective action.
*   **Poor Patient Adherence Tracking:** Manually tracking thousands of patient visits and medication schedules is prone to error and doesn't provide an immediate view of at-risk patients who may drop out of the trial.
*   **Difficulty in Forecasting:** Inaccurate or delayed data makes it challenging to forecast key milestones, including the final recruitment date, which impacts budget and resource planning.
*   **Fragmented Data:** Data often exists in disparate systems like an Electronic Data Capture (EDC) and a Clinical Trial Management System (CTMS), making a holistic analysis difficult.

---

## 3. How It Was Solved: The Power BI Solution

This project was executed from start to finish, beginning with raw, simulated data and ending with a suite of interactive executive dashboards. The process involved three main phases:

### Phase 1: Data Preparation and Modeling

The foundation was built on a robust and scalable data model.

*   **Data Sourcing:** Data was simulated to mirror real-world EDC and CTMS systems, organized into three core tables:
    1.  `Fact_Patient_Enrollment`: A detailed log of every patient screened, enrolled, failed, or withdrawn.
    2.  `Fact_Patient_Visits`: A transactional table logging every scheduled and completed patient visit.
    3.  `Dim_Site`: A dimension table containing details for each participating research site.

*   **Data Transformation (in Power Query):** The raw data was cleaned and enriched to create meaningful metrics:
    *   **Visit Variance:** Calculated the difference between `Actual_Visit_Date` and `Scheduled_Visit_Date` to quantify patient adherence.
    *   **Enrollment Duration:** Calculated the days between `Screening_Date` and `Enrollment_Date` to identify administrative bottlenecks at various sites.
    *   **Date Dimension:** A standard calendar table was created to enable robust time-intelligence analysis (e.g., monthly and quarterly trends).

*   **Data Modeling (Star Schema):** A logical star schema was created in Power BI to ensure efficient querying and scalability. The `Dim_Site` table was related to both the `Fact_Patient_Enrollment` and `Fact_Patient_Visits` tables, creating a clean and powerful analytical model.

### Phase 2: DAX Implementation and KPI Creation

Once the model was in place, Data Analysis Expressions (DAX) were used to create the key performance indicators (KPIs) that drive the dashboard.

*   **Recruitment & Progress Metrics:**
    *   `Total Screened`, `Total Enrolled`, `Total Randomized`
    *   `Screen Failure Rate`: `(Total Screened - Total Enrolled) / Total Screened`
    *   `Randomization Rate`: `Total Randomized / Total Enrolled`
    *   `Recruitment Velocity`: Average number of patients enrolled per week.
    *   `Avg Days to Enrollment/Randomization`: Pinpoints delays in the funnel.

*   **Adherence & Retention Metrics:**
    *   `Overall Adherence Score`: `Total Completed Visits / (Total Completed Visits + Total Missed Visits)`
    *   `Dropout Rate`: Calculated the percentage of enrolled patients who later withdrew.
    *   `Dropout Risk Flag`: A conditional column identifying patients with adherence below a 70% threshold, flagging them as "At-Risk".

### Phase 3: Dashboard Visualization and Insights

A series of purpose-built dashboards were created to serve different analytical needs, from high-level overviews to granular deep dives.

*   **Enrollment Overview:** This dashboard provides a snapshot of the entire recruitment funnel. The **line chart** visualizes cumulative enrollment over time, instantly showing if the trial is on, ahead of, or behind schedule. The **funnel chart** breaks down the journey from "screened" to "randomized," clearly highlighting where in the process candidates are dropping off.

*   **Site Performance Leaderboard:** This is a crucial tool for operational management. It provides a **table** that ranks each clinical site across key metrics like Total Enrolled, Screen Failure Rate, and Enrollment Velocity. The **"Enrollment Over Time" line chart** allows for a direct visual comparison of how different sites are trending against each other, making it easy to spot top performers and those needing support.

*   **Adherence Tracking Dashboard:** This view focuses entirely on patient retention and compliance. It monitors the **Overall Adherence Score** and tracks **Medication Taken Counts**. The **"Dropout Risk Summary" pie chart** provides an immediate count of "Low Risk" vs. "At-Risk" patients, while the table allows managers to drill down to the individual `patient_id` to see who is non-compliant.

*   **Final Executive Dashboard:** This high-level summary consolidates the most critical KPIs into a single view. It features:
    *   **Headline KPIs:** `Total Enrolled`, `Enrollment Rate`, and `Adherence Rate`.
    *   **Trend Analysis:** A dual-axis line chart showing **Monthly Enrolled vs. Monthly Randomized** patients to track momentum.
    *   **Comparative Analysis:** A **bar chart for Site Performance Comparison** across enrollment, adherence, and randomization rates, providing a clear, concise tool for strategic decision-making.

---

## 4. Repository Contents

This GitHub repository contains all the necessary files to explore this project:

*   **/Project File/**
    *   `Clinical_Trial_Dashboard.pbix`: The complete Power BI file containing the data model, DAX calculations, and all dashboard pages.
*   **/Data/**
    *   `Fact_Patient_Enrollment.csv`: The source data for patient enrollment details.
    *   `Fact_Patient_Visits.csv`: The source data for all patient visit logs.
    *   `Dim_Site.csv`: The source data for all clinical site information.
*   **/Images/**
    *   `Enrollment_Overview.png`: Screenshot of the main enrollment dashboard.
    *   `Site_Performance_Leaderboard.png`: Screenshot of the site comparison dashboard.
    *   `Adherence_Tracking.png`: Screenshot of the patient adherence dashboard.
    *   `Executive_Dashboard.png`: Screenshot of the final summary dashboard.
*   `README.md`: This detailed project explanation.

---

## 5. How To Use This Project

To get started with this project:

1.  **Clone the repository** to your local machine.
2.  **Ensure you have Power BI Desktop** installed.
3.  **Open the `Clinical_Trial_Dashboard.pbix` file** located in the `/Project File/` directory.
4.  **Explore the dashboards!** All visuals are interactive. Click on data points, use the slicers, and drill down to see how the data is connected.
5.  **(Optional) Refresh Data:** If you modify the source CSV files, you can refresh the data in Power BI by clicking the "Refresh" button in the Home ribbon. You may need to update the file paths in `Transform data` -> `Data source settings` if Power BI cannot find them automatically.
