# Higher Education Consulting Analytics: The Factors That Affect Graduation Rates
## Project Purpose
The purpose of this project is top look at how many aspects within the higher education sphere affect graduation rates, and strategies on how these differences can be addressed
## Data Dictionary
```
College Name: The full name of that specific university 
State: The US state that the university is in
Public (1)/ Private (2): wether the school is public or private, represented by a number 1 or 2  
appli. rec'd: The amount of applications that a university received            
# appl. accepted: The amount of applications that a university accepted          
# new stud. enrolled: The amount of new students that a unversity accepted      
% new stud. from top 10%: A percentage of the amount of new students that university received if that student was from the top 10 percent in highschool
% new stud. from top 25%: A percentage of the amount of new students that university received if that student was from the top 25 percent in highschool 
# FT undergrad: The amount of Full Time Undergrads that the school has           
# PT undergrad: The amount of Part Timr undergrads that the school has           
in-state tuition: The cost of that schools in-state tuition
out-of-state tuition: The cost of that schools out-of-state tuition      
room: The cost of a dorm room for that school                     
board: The cost of trhe meal plan for that school              
add. fees: The cost of any additional fees that that school has              
estim. book costs: an estimate of the cost for books for that school      
estim. personal $: an estimate of the cost for personal items for that student       
% fac. w/PHD: the percentage of faculty at that school that has a doctorate           
stud./fac. ratio: The ratio of studenbts for every faculty member at that school        
Graduation rate: The graduation rate at that school       
Public or Private: Tells wether a school is poublic or private, but as a string	
total cost (in state tuition): The total estimated cost of a student, if they paid for everything along with their in state tuition	for that school
total cost (out of state tuition):	The total estimated cost of a student, if they paid for everything along with their out of state tuition for that school	
Mean Tuition: The average tuition between in state tuition and out of state tuition for that school
```
## Summary
### Handling NaN Values and Outliers
- I handled NaN values in three different ways
1. Imputing with the median: for columns that had few missing values and weren't about money 
2. Imputting with the median by state: for columns that had many missing values or were about money
3. imputting with a 0: specifically for the '% new stud. from top %10' and '% new stud. from top %25' columns
- For outliers, I handled them with the IQR method
**EX:**
```python
low_amount_x = df['Mean Tuition'].quantile(0.25)
up_amount_x = df['Mean Tuition'].quantile(0.75)
x_range_1 = up_amount_x - low_amount_x
lower_bound_x = low_amount_x - 1.5 * x_range_1
upper_bound_x = up_amount_x + 1.5 * x_range_1

low_amount_y = df['Graduation rate'].quantile(0.25)
up_amount_y = df['Graduation rate'].quantile(0.75)
y_range = up_amount_y - low_amount_y
lower_bound_y = low_amount_y - 1.5 * y_range
upper_bound_y = up_amount_y + 1.5 * y_range

df_cleaned = df[(df['Mean Tuition'] >= lower_bound_x) & (df['Mean Tuition'] <= upper_bound_x) &
                (df['Graduation rate'] >= lower_bound_y) & (df['Graduation rate'] <= upper_bound_y)]
```
This ensured that for some of my key visualizations, I wouldn't have outliers
### key visuals
1. **[heatmap of correlation](Heatmap_of_Correlation.png)** a heatmap which shows the correlations between different numerical columns, this was helpful particularly when I was develoiping my questions and starting with my analysis
2. **[public or private grad rate](Graduation_Rate_by_School.png)** a barplot that shows the median graduation rates by wether the school was public or private, helpful as it showed that private schools usually have higher graduation rates that public schools
3. **[no outliers](Correlation_of_Tuition_and_Graduation_Rates.png)** **[with outliers](Correlation_of_Tuition_and_Graduation_Rate(with_Outliers).png)** 2 regplots that show the correlation between the graduation rate and the mean tuition. shows that there is a moderatly strong correlation between the two fields. one of them had outliers left in to show why I excluded them in the first place (impossible statistic)
4. **[no outliers](Graduation_Rates_by_SF_Ratio.png)** **[with outliers](Graduation_Rates_By_SF_Ratio(with_Outliers).png)** 2 scatter plots that show the graduation rate by the student faculty ratio and wether the school is public or private. it shows that public schools have higher student faculty ratios, but lower graduation rates than private schools. one of them shows why i left out the outliers (impossible statistic, again)
5. **[grad rate by state](Graduation_Rate_by_State.png)** a barplot which shows the graduation rate by each state. important as it shows that certain states have worse graduation rates than others.
6. barplot that shows the amount of applicants received by state, shows which states are propular to apply to
7. **[missing values](map_of_missing_values.png)** a heatmap that shows missing values. Good as it shows which columns have missing values, and how many missing values they have
## conclusion
#### my analysis was able to show that graduation rates are affected by many factors, specifically factors such as the State, the student facylty ratio, as well as the tuition price. With these insights, my recommendations to the universities as a whole is to...
1. staff more individuals within public schools, and/or within private schools that are underperforming
2. potentially consider staffing within states where the graduation rate is lower (such as New Mexico, Louisiana, and Nevada)
3. offer more resources to schools that have lower graduation rates, and potentially schools that have lower tuition rates
#### Other things to consider would be...
1. How could you model the success of certain private schools within public schools, and underpreforming private schools?
2. Tuition rates are really high in certain states, would it be possible to lower tuition rates without lowering graduation rates, or are tuition rates correlated with the amount of resources that a college can have access to?