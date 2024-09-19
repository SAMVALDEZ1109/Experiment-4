# Experiment-4 :Data Wrangling and Visualization

## Objective: 

> To identify the codes and functions needed in cleaning and visualizing data

> To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

### ECE BOARD EXAM PROBLEM: Using the provided dataset, you'll perform data wrangling to extract specific insights and create visualizations to analyze how various factors contribute to average grades. 

#### Let's break down the tasks and expected outputs:

## Problem 1: Create Specific Dataframes

### Part A. Dataframe for Instrumentation Track and Luzon Hometown (Filename: Instru)

> Columns: Name, GEAS, Electronics >70

> Track: Constant as Instrumentation

> Hometown: Constant as Luzon

### Expected Behavior: 

> This Dataframe filters students who belong to the Instrumentation track, have a hometown in Luzon, and includes only those with an Electronics score greater than 70.

### Approach:

> Filter the dataset to only include rows where the Track column equals Instrumentation and Hometown equals Luzon.

> Extract the columns for Name, GEAS, and add a conditional column for Electronics greater than 70.

#### start of code

#importing necessary libraries

import pandas as pd

import matplotlib.pyplot as plt

import seaborn as sns

#load data spreadsheet

df = pd.read_excel('board2.xlsx')

df

#filter the students from Luzon with Instrumentation as their track

Instru = df[(df['Track'] == 'Instrumentation') & (df['Hometown'] == 'Luzon') & (df['Electronics'] > 70)]

#pick out the wanted columns to display the same output as the given output

Instru = Instru[['Name', 'GEAS', 'Electronics']]

Instru 

### Part B. Dataframe for Female Students in Mindanao (Filename: Mindy)

> Columns: Name, Track, Electronics, Average >=55

> Gender: Female

> Hometown: Constant as Mindanao

### Expected Behavior : 

> This Dataframe should include only female students from Mindanao and display their Name, Track, Electronics score, and whether their average grade is greater than or equal to 55.

### Approach :

> Filter for Gender = Female and Hometown = Mindanao.

> Extract the Name, Track, and Electronics columns.

> Calculate the average grade and include a conditional column Average >=55.

#### start of code

#Calculate the average of their scores

Mindy.loc[:,'Average'] = Mindy[['Math', 'GEAS', 'Electronics']].mean(axis=1)

#Include only the students with an average score that is greater or equal to 55

Mindy = Mindy[Mindy['Average'] >= 55]

Mindy

## Problem 2: Visualization Task

### Visualization Objective : 

> Create plots to analyze whether chosen track, gender, or hometown has a significant impact on the average grade.

### Steps:

> Track vs. Average Grade: Use a bar or box plot to show the relationship between a student’s chosen track (e.g., Instrumentation, Communication) and their average grades.

> Gender vs. Average Grade: Plot a comparison of average grades based on gender (e.g., male vs. female).

> Hometown vs. Average Grade: Visualize how students from different hometowns (e.g., Luzon, Visayas, Mindanao) perform on average.


#### start of code

#Use boxplot as the visualization technique to display the factors to the avg grade based on track

df['Average'] = df[['Math', 'GEAS', 'Electronics', 'Communication']].mean(axis=1)

print('Average Grade by Track:')

sns.boxplot (x='Track', y='Average', data=df)

plt.show()


#Use boxplot as the visualization technique to display the factors to the avg grade based on gender

df['Average'] = df[['Math', 'GEAS', 'Electronics', 'Communication']].mean(axis=1)

print('Average Grade by Gender')

sns.boxplot (x='Gender', y='Average', data=df)

plt.show()


#Use boxplot as the visualization technique to display the factors to the avg grade based on hometown

df['Average'] = df[['Math', 'GEAS', 'Electronics', 'Communication']].mean(axis=1)

print('Average Grade by Hometown')

sns.boxplot (x='Hometown', y='Average', data=df)

plt.show()


