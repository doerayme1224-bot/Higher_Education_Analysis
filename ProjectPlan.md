# Project Plan
1. put the repository onto my system 
    - Find the repository for the project
    - Fork the repo
    - Clone the forked repo
2. open it on a notebook (*jupyter lab* in the terminal)
3. Make imports then read in the data
- imports made:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import missingno as msno
import numpy as np
```
4. understand the data
- the purpose of this step in this project is to make sure that I can navigate the data without feeling lost
    - first looked at it by typing the dataframe (df)
    - i used scripts I know to look at aspects of the data

```python
df.shape # first I used to shape to understand the amount of rows and columns I had within the df

df.isna().sum() # Then I used isna with sum to get a count of the amount of null values that I had within the dataset by column

df.info() # i used info to show me the dtype, as well as the non null count and even memory usage

df.describe() # used describe to give me summary  statistics (mean, median, st deviation) on the dataframe

df.describe(include = 'O') # used describe with parameter include = 'O' to look at only the columns that are not numerical 

msno.matrix(df) # gave me a heatmap of all the missing values within the df
```
5. data cleaning
- cause of `.isna().sum()` and tthe `msno.matrix` i know that my dataset has lots of missing data, here is my plan with each column. I also have some columns that don't really make sense at a first glance, and my plan with many of those is to rename them, and to change some of there values potentially *like in the Public (1)/ Private (2) column*
    - for a good amount of the fields, I plan on imputing the values in with the median, particularly if they have rows needed to be filled
    - for columns that focus on the either the cost of things, or that have many missing values, I plan to group them by the state and then fill them with either the median or mean for that specific state (except for maybe out of state tuition) 


`side note on outliers...`
`The way that I plan on lookin gat outliers is by devolping some visualizations using boxplots as a way of Identifying them, but I decided to scratch that cause I thought it was sloppy`
- I decided to lookup how to deal with/handel outliers, and with that I plan on using either the z-score method or the IQR(inner quartile range method) in order to handle outliers/identify them
- I should/could also mentiuon how the imputation of the median would handle many of those outliers


6. feature engineering 

- one of the ones that I already did was make a column called public or private that shows a string stating wether that college is public or private

- some of the things I want to change about the df
    - make the `Public (1)/ Private (2)` column a 0 or 1 (0 for public, 1 for private) and change its name 
    - a column that shows the estimated gross expense that students would make at that university (with, and without dorms)(with in state tuition and out of state tuition. etc)

*as for right now I rthink that this is fine for now I will have to look more into the data to make more features*

7. EDA/ creating visualizations
- a countplot that shows the amount of 


### more I couldve done with it
- develop questions
- 


### look at the ML template



*in every step of planning***you develop questions**
- 
*formalization of plan:***blueprint on approachiong projects**