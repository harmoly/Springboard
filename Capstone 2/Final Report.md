# Final Report - Capstone 2 - College Majors

## Introduction

The dataset used in this project can be found at https://www.kaggle.com/tunguz/college-majors. It contains information regarding salary, employment status, demographics, etc. according to different college majors. This project was intended to assist in generating a recommendation system for prospective students, given their career-related preferences. 

## 1. Data Wrangling

[Code](https://github.com/harmoly/Springboard/blob/main/Capstone%202/Capstone%202%20-%20Data%20Wrangling.ipynb)

Kaggle offered a number of different datasets. Here, we merge two of them containing our most relevant information for graduates of all ages. And of course, we remove null values and eliminate any obviously unneeded variables.

Variables: 

['Major', 'Major_category', 'Grad_total',
       'Grad_sample_size', 'Grad_employed', 'Grad_full_time_year_round',
       'Grad_unemployed', 'Grad_unemployment_rate', 'Grad_median', 'Grad_P25',
       'Grad_P75', 'Nongrad_total', 'Nongrad_employed',
       'Nongrad_full_time_year_round', 'Nongrad_unemployed',
       'Nongrad_unemployment_rate', 'Nongrad_median', 'Nongrad_P25',
       'Nongrad_P75', 'Grad_share', 'Grad_premium',
       'Total', 'Men', 'Women', 'ShareWomen', 'Sample_size', 'Employed',
       'Full_time', 'Part_time', 'Full_time_year_round', 'Unemployed',
       'Unemployment_rate', 'Median', 'P25th', 'P75th', 'College_jobs',
       'Non_college_jobs', 'Low_wage_jobs']
       
## 2. EDA

[Code](https://github.com/harmoly/Springboard/blob/main/Capstone%202/Capstone%202%20-%20EDA%20(3).ipynb)

## 3. Training and Preprocessing

[Code](https://github.com/harmoly/Springboard/blob/main/Capstone%202/Capstone%202%20-%20Preprocessing%20and%20Training%20Data%20Development%20(1).ipynb)

## 4. Modeling

[Code](https://github.com/harmoly/Springboard/blob/main/Capstone%202/Capstone%202%20-%20Modeling%20(1).ipynb)

## 5. Conclusion
  
Ultimately, we were able to achieve a number of tasks:

1. We generated a model that could accurately predict salary of a prospective student/job candidate, (within reason), given their major, gender, etc.
2. We have created the groundwork for a system to offer recommendations for majors, given a user's salary preferences, employment preferences, etc.
3. We have gained insight to work in tandem with the above tasks to offer as much predictive information as possible pertaining to the different majors and major categories included in this dataset.
