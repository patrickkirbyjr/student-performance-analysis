# Multi-Year Student Performance Analysis (STEM Grades)

## 📌 Project Overview
This project analyzes student performance data from Physical Science C (PSC) classes at Altoona Area High School (AAHS) over a three-year period (2023-2025). 

The primary objective was to move beyond anecdotal evidence and use statistical analysis to determine how external factors—specifically **instructional year**, **time of day (class period)**, and **class size**—impact student final grades.

## 📂 Dataset
The dataset consists of anonymized final average grades extracted from the school's Learning Information Management System (LIMS).

* **Source:** Real student grade records (2023-2025).
* **Privacy:** All personally identifiable information (PII) has been removed; records are referenced by a unique `Student ID`.
* **Size:** 262 total student records.

### Data Dictionary
| Column | Description | Data Type |
| :--- | :--- | :--- |
| `student_id` | Unique anonymized identifier for each student | `int` |
| `school_year` | Academic year ending (e.g., 2023, 2024, 2025) | `int` |
| `subject` | Course code (Focus: `PSC` - Physical Science C) | `string` |
| `class_period` | Time slot of the class (1-9) | `int` |
| `number_in_class` | Total count of students in that specific section | `int` |
| `final_grade` | The student's final average for the course (0-100) | `int` |

## 🛠️ Technologies & Libraries Used
The analysis was performed using **Python** within a Jupyter Notebook environment.

* **Data Manipulation:** `pandas`, `numpy`, `janitor` (for clean column names)
* **Visualization:** `seaborn`, `matplotlib`
* **Statistical Analysis:** `scipy.stats`, `scikit_posthocs`

## 📊 Methodology
The project follows a standard data science workflow:
1.  **Data Cleaning:** Renaming columns for consistency (snake_case) using `pyjanitor` and filtering for the target subject (PSC).
2.  **Exploratory Data Analysis (EDA):** Visualizing distributions using boxplots and stripplots to identify outliers and trends.
3.  **Normality Testing:** Using the **Shapiro-Wilk test** to determine if data followed a normal distribution.
    * *Result:* Data was determined to be non-normal (p < 0.05), requiring non-parametric tests.
4.  **Hypothesis Testing:**
    * **Kruskal-Wallis H-test:** Used to determine if there were statistically significant differences between three or more groups (e.g., Years, Class Periods).
    * **Dunn’s Test:** Used for post-hoc analysis to pinpoint exactly *which* groups differed significantly (e.g., 2023 vs. 2025).

## 💡 Key Findings

### 1. Year-Over-Year Trends
* **Observation:** Average grades increased consistently over the three years (2023: ~65%, 2024: ~76%, 2025: ~86%).
* **Statistical Result:** The improvement between **2023 vs 2025** and **2024 vs 2025** was statistically significant. The difference between 2023 and 2024 was not statistically significant (p > 0.05).
* **Conclusion:** Changes in instructional methods in 2025 likely contributed to a measurable improvement in student mastery.

### 2. Class Period Effects
* **Observation:** Grades varied based on the time of day.
* **Conclusion:** The data suggests a **"Morning Slump"** and an **"End-of-Day Slump,"** indicating that lesson effectiveness may drop during the earliest and latest periods of the day.

### 3. Class Size Effects
* **Observation:** Class sizes ranged from small (~13 students) to large (~24+ students).
* **Conclusion:** Statistical analysis showed significant performance differences based on class size, supporting the hypothesis that **smaller classes** (allowing for more one-on-one attention) correlate with higher academic performance.

## 🚀 How to Run This Analysis
1.  Clone this repository.
2.  Ensure the `data/y123_grades.csv` file is present (or replace with your own dataset matching the schema).
3.  Install dependencies:
    ```bash
    pip install pandas numpy pyjanitor matplotlib seaborn scipy scikit-posthocs
    ```
4.  Open `student-performance-analysis.ipynb` in Jupyter Lab or VS Code.
5.  Run all cells to reproduce the analysis and generate visualizations.