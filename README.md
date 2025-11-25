# Overview
Welcome to my analysis of the data job market, focusing on data analyst roles. This project was created out of desire to navigate and understand the job market more effectively. It delves into  the top paying and in demand skills to help find optimal job opportunities for data analysts

# Tools I Used
- python: pandas Library, Matplotlib Library, seaborn Library
- VS code
- Git & GitHub

# The Analysis

## 01. what are the most demanded skills for top 3 most popular data roles

to find the most demanded skills for top 3 most popular data roles, i filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3  roles. This query highlights the most popular job titles and their top skills, showing which skills i should pay attention to depending on the role i'm targeting.
[2_skills_Count.ipynb](Project/2_Skills_Count.ipynb)

### Visualize Data
```python

fig, ax = plt.subplots(len(job_titles),1)

for i, job_title in enumerate(job_titles):
    df_plot= df_skills_count[df_skills_count['job_title_short'] == job_title].head(5)
    df_plot.plot(kind='barh', x='job_skills', y='skill_count', ax=ax[i], title=job_title)
    ax[i].invert_yaxis()
    ax[i].set_ylabel('')
    ax[i].legend().set_visible(False)
fig.suptitle('count of top skills in job postings', fontsize=15) 
fig.tight_layout(h_pad=0.5)  # fix overlap
plt.show   
```

### Results
![Visualization for top skills for data nerds](/Project/Images/skills_demand.png)

### Insights
- python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists and Data Engineers
- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles.
- Data Engineers require more specialized technical  skills compared to Data Analysts and Data Scientists who are expected to be  proficient in more general data management and analysis tools(Excel, Tablue)

## 02. How are in demand skills trending for data analysts?

```python
from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:, :4]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

ax= plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()    

```   

### results

![trending top skills for data analysts in the US](/Project/Images/skills_trend_demand.png)

*bar graph visualizing the trending  top skills  for data analysts in the US in 2023.*

### Insights

- sql remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.
- Excel maintains a strong presence, though it shows a steady decline in job posting mentions, especially from August to November.
- Python sees a slight upward trend mid-year, reflecting its growing importance in data analytics roles
- Tableau usage dips slightly in the second half, potentially indicating a shift toward other BI tools or integrated data platforms.


## 03.  How well do jobs and skills pay for Data Analysts?

### Salary Analysis for data nerds

### visualize data

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short',order=job_order,)

ticks_x = plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()

```

#### Results
![salary distribution of data jobs in the US](/Project/Images/salary_distrubution.png)
*Box plot visualizing the salary distribution  for top 6 data job titles.*

#### Insights
- Senior-level roles dominate the top salary ranges, especially Senior Data Scientists and Senior Data Engineers, often exceeding $200K/year.
- Data Scientists and Data Engineers show similar median salaries, both higher than analyst roles but with a wide range of outliers, indicating variance in experience and company size.
- Data Analysts and Senior Data Analysts earn significantly less on average compared to engineering and science roles, typically ranging between $70K–$130K.The broad salary ranges and outliers across all roles suggest high variability in compensation based on skills, location, and company.
- Data Analysts are the entry point, but going for engineering or science roles offers a higher earning ceiling

# What I learned

Throughout this project , I deepend my understanding of the data analysis job market and enhanced my technical skills in Python, especially in data manipulation and visualization 

- Gained practical experience with Python's data analysis libraries

- Developed skills in cleaning and visualizing job market data

- Learned to extract actionable insights from real-world datasets

- Improved my ability to communicate data findings effectively

# Conclusion
As the data field continues to evolve, ongoing analysis will be essential to maintain a competitive edge. This project serves as both a practical foundation for job market navigation and a demonstration of how data analysis can inform career decisions. It underscores the importance of continuous learning in this dynamic field, where today's in-demand skills may evolve into tomorrow's fundamentals.                     
