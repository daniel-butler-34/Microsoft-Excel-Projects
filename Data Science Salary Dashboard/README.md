# Data Science Salary Dashboard in Excel

<img width="1883" height="708" alt="salary_dashboard" src="https://github.com/user-attachments/assets/eafbb689-bcf5-4941-91e8-72347803c9cb" />

## Introduction

This data jobs salary dashboard was created as part of my aim to build experience using Microsoft Excel. The data we used contains detailed information on job titles, salaries, locations, and essential skills from multiple countries.

### Dashboard File
My final dashboard is in [Salary_Dashboard.xlsx](Salary_Dashboard.xlsx).

### Excel Skills Used

To create this dashboard, the following Excel functions were used for the analysis:

- **Charts**
- **Formulas and Functions**
- **Data Validation**

### Data Jobs Dataset

The data set used for this project contains real-world data science job information for the year 2023. The dataset is made up of over 30,000 records and includes detailed information on the job titles, salaries, locations and the required skills.

## Building the dashboard

### Charts

#### Data Science Job Salaries - Bar Chart

<img width="1081" height="708" alt="dashboard_bar_chart" src="https://github.com/user-attachments/assets/436323d1-a361-4e64-876d-fe836712a559" />

This chart utilises Excel's bar chart feature (with formatted salary values) and horizontally oriented allowing for easy visual comparisons. The job titles are also sorted in descending order by salary, improving readability. This bar chart enables easy identification of salary trends, for example noting that Senior roles are typically higher-paying than non-senior roles.

#### Country Median Salaries - Map Chart

<img width="1355" height="710" alt="dashboard_map" src="https://github.com/user-attachments/assets/d8e09f56-769b-40f2-a06b-0f6515693b79" />

This chart utilises Excel's map chart feature to put the median salaries in each country onto the globe, allowing easy comparison between countries. This allows the user to gain an immediate understanding of geographic salary trends, by identifying lighter and darker-coloured regions.

### Formulas and functions used

#### Median Salary by Job Titles

The completed dashboard uses the following Excel formula to calculate the median salary for each job title:

```
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

The formula checks the job title, country and schedule type, making sure to exclude blank entries. This provides specific salary information for a given job title, region and schedule type which is entered by the user. This formula populates the below table, with the appropriate value then being displayed on the dashboard.

Background Table:

<img width="281" height="201" alt="background_table" src="https://github.com/user-attachments/assets/19338563-0e3e-4dfa-b2e3-3ad8d4f463d4" />

Dashboard Implementation:

<img width="580" height="666" alt="dashboard_implementation" src="https://github.com/user-attachments/assets/9422b50c-d7a2-4d2d-ab6b-446330272ce3" />

#### Count of Job Schedule Type

To count the number of jobs by schedule type, we make use of the following Excel formula, which uses the `FILTER()` function to exclude entries which do not match the schedule type selected by the user. Zero values are also automatically omitted. 

```
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

This formula populates the below table, which gives a list of unique job schedule types

Background Table

<img width="184" height="105" alt="background_table_job_type" src="https://github.com/user-attachments/assets/05b66245-3ad2-40ec-bfeb-1f35caa309b5" />

Dashboard Implementation:

<img width="583" height="649" alt="dashboard_implementation_job_type" src="https://github.com/user-attachments/assets/588550e8-d117-48cc-b558-26ee91daf01d" />

### Data Validation Processes:

#### Filtered List

A filtered list is used as a data validation rule under the `Job title`, `Country` and `Type` options on the dashboard, as shown below:

<img width="290" height="264" alt="data_validation" src="https://github.com/user-attachments/assets/45b1f7f8-a2f2-455d-ab5b-89e177eef98d" />

Restricting these entries to predefined inputs improves the overall usability of the dashboard, while ensuring that none of the backend formulas run into errors as a result of the user potentially entering erroneous data into any one of the fields.

