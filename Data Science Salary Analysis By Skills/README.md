
# Data Science Salary Analysis by Skills

## Introduction

As part of Luke Barousse's Microsoft Excel course, I created an Excel sheet to analyse the highest-paying skills in the data science market. In this project we set out to understand what skills most employers are requesting.

### Questions to Analyse

In this project, we set out to answer the following questions:

1. **Do more skills get you better pay?**
2. **What is the salary for data jobs in different regions?**
3. **What are the top skills in the data science industry?**
4. **What are the salaries of the most in-demand skills?**

### Excel Functions Used

In this project, we utilised the following Excel features:

- **Pivot Tables**
- **Pivot Charts**
- **Power Query**
- **Power Pivot**
- **DAX (Data Analysis Expressions)**

### Data Jobs Dataset

The data set used for this project contains real-world data science job information for the year 2023. The dataset is made up of over 30,000 records and includes detailed information on the job titles, salaries, locations and the required skills.

## 1. Do more skills get you better pay?

### Tool: Power Query (ETL)

#### Extract

First, I used Power Query to extract the original data and create two queries. First, one with all of the data jobs information, and another listing the skills for each job in the data set.

#### Transform

I then transformed each query by configuring the columns to have the proper data types, removing redundant columns, cleaning text data and trimming excess white space.
- data_jobs_salary

  <img width="248" height="305" alt="powerquery_data_jobs_salary" src="https://github.com/user-attachments/assets/ae0472e3-3867-4664-a3eb-5b9fac0883f2" />

- data_jobs_skills

  <img width="248" height="317" alt="powerquery_data_jobs_skills" src="https://github.com/user-attachments/assets/40820556-c5b3-41e6-b5bf-f1ecbf712d64" />

#### Load

Finally, I loaded both transformed queries into the workbook.
- data_jobs_salary

<img width="1661" height="988" alt="powerquery_data_jobs_salary_data" src="https://github.com/user-attachments/assets/802fff99-6a75-42d5-ba14-76013e05ca9c" />

- data_job_skills

<img width="1667" height="991" alt="powerquery_data_jobs_skills_data" src="https://github.com/user-attachments/assets/dc7567c6-f95f-4aa8-a468-b78b050f3f34" />

### Analysis

#### Insights

From the imported data, one sees that there is a positive correlation between the number of skills requested in job postings and the median salary, particularly in Senior roles. Roles that require fewer skills seem to offer lower salaries, suggesting that more specialised skill sets give higher market value.

<img width="1246" height="714" alt="scatter_plot" src="https://github.com/user-attachments/assets/278416c1-bea2-4401-894f-ebf198a769fa" />

#### Conclusion

The above trend emphasises the importance of acquiring multiple relevant skills, particularly for individuals aiming for Senior roles.

## 2. What is the salary for data jobs in different regions?

### Tools: PivotTables & DAX

#### Pivot Tables

Using the data model created using Power Pivot, it then became easy to create pivot tables to show the required data. Moving `job_title_short` to the rows and `salary_year_avg` into the values of the pivot table, the following measure was used to calculate the median salary for jobs specifically located in the United States:

```
=CALCULATE([Median Salary],data_jobs_salary[job_country] = "United States")
```

#### DAX

To calculate the median yearly salary overall, the following DAX command was used:

```
=MEDIAN(data_jobs_salary[salary_year_avg])
```

### Analysis

#### Insights

Senior roles command higher median salaries both in the United States (where the majority of the data set is sourced from) and internationally, highlighting the global demand for high-level data expertise. The salary disparity between US and non-US roles is particularly notable in high-tech jobs:

<img width="789" height="262" alt="median_country_salary_table" src="https://github.com/user-attachments/assets/87553089-11c8-49d3-968b-f744ea1ec90d" />

#### **Conclusions**

These salary insights are helpful for companies looking to align their offers with market standards while still taking account of geographic variations in the median salary.

## 3. What are the top skills in the data science industry?

### Tool: Power Pivot

#### Power Pivot

To analyse the data further, I created a data model in Power Pivot by integrating the `data_jobs_salary` and `data_jobs_skills` tables into one model. Since the data had already been cleaned in Power Query, Power Pivot was simply used to create a relationship between these two tables.

#### Data Model

Using the `job_id` column, I created a relationship between the two tables comprising the data model:

<img width="571" height="457" alt="power_pivot_diagram" src="https://github.com/user-attachments/assets/dc68cf13-dbc8-448c-954c-b2edad06362c" />

#### Power Pivot Menu

After joining the two tables, I made use of the Power Pivot menu to further refine the data model. In particular, the Power Pivot window makes creating measures easy.

### Analysis

#### Insights

It is immediately clear from the data that SQL and Python are the most sought-after skills in many different data science jobs, reflecting their foundational role in data cleaning, processing and analysis. One also sees emerging tools such as Amazon Web Server (AWS) and Azure, showing the data science industry's shift towards cloud services.

<img width="1052" height="689" alt="data_science_skill_chart" src="https://github.com/user-attachments/assets/9907b806-3c87-4407-81f6-7d4573e3663f" />

#### Conclusions

Having an understanding of which skills are most in-demand in the data science industry is important, as it allows training courses to focus their programmes on the most in-demand technologies for data science roles.

## 4. What are the salaries of the most in-demand skills?

### Tool: Advanced Charts (Pivot Chart)

#### PivotChart

To plot the median salary against skill counts, I made use of a Pivot table, with the primary axis being the median salary (pictured as a clustered column) and the secondary axis being the skill count (as a series of markers). To make the chart easier to understand and interpret, I made use of a gentle blue colour scheme and changed the markers to a diamond shape.

### Analysis

#### Insights

The most in-demand skills such as Python, SQL and Oracle are associated with higher median salaries, reinforcing their importance in high-paying data science jobs. On the other hand, technologies such as Microsoft PowerPoint and Microsoft Word are associated with the lowest median salaries and counts, indicating less demand in the data science sector.

<img width="1094" height="685" alt="data_science_skills_salary_chart" src="https://github.com/user-attachments/assets/21c06cdb-eb2a-4476-ad3d-9af94a7159f8" />

### Conclusions

The above chart, as well as the analysis carried out in the earlier sections of the project, highlights the importance of investing the time to learn high-value skills such as Python and SQL (which are evidently tied to higher-paying roles).
