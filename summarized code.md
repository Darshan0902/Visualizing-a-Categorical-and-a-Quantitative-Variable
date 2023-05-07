# Introduction to Data Visualization with Seaborn

<h2> Importing the needed libraries </h2> 
  
  ```
 # Importing the course packages
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Importing the course datasets
country_data = pd.read_csv('datasets/countries-of-the-world.csv', decimal=",")
mpg = pd.read_csv('datasets/mpg.csv')
student_data = pd.read_csv('datasets/student-alcohol-consumption.csv', index_col=0)
survey = pd.read_csv('datasets/young-people-survey-responses.csv', index_col=0)
  
  ```
  
  <h2> Count plots </h2>
  
  Use sns.catplot() to create a count plot using the survey_data DataFrame with "Internet usage" on the x-axis.

  
  ```
  # Separate into column subplots based on age category
sns.catplot(x="Internet usage", data=survey_data,
            kind="count")

# Show plot
plt.show()
  
  ```

Make the bars horizontal instead of vertical.

```
# Separate into column subplots based on age category
sns.catplot(y="Internet usage", data=survey_data,
            kind="count")

# Show plot
plt.show()
```


-Separate this plot into two side-by-side column subplots based on "Age Category", which separates respondents into those that are younger than 21 vs. 21 and older.


```

# Separate into column subplots based on age category
sns.catplot(y="Internet usage", data=survey_data,
            kind="count",col="Age Category")

# Show plot
plt.show()

```

<h2> Bar plots with percentages </h2>

Use the survey_data DataFrame and sns.catplot() to create a bar plot with "Gender" on the x-axis and "Interested in Math" on the y-axis.

```
# Create a bar plot of interest in math, separated by gender

sns.catplot(x="Gender",y="Interested in Math",data=survey_data,kind="bar")

# Show plot
plt.show()

```
<h2> Customizing bar plots </h2>

Use sns.catplot() to create a bar plot with "study_time" on the x-axis and final grade ("G3") on the y-axis, using the student_data DataFrame.


```
# Create bar plot of average final grade in each study category

sns.catplot(x="study_time",y="G3",data = student_data,kind="bar")



# Show plot
plt.show()

```

Using the order parameter and the category_order list that is provided, rearrange the bars so that they are in order from lowest study time to highest.


```
# List of categories from lowest to highest
category_order = ["<2 hours", 
                  "2 to 5 hours", 
                  "5 to 10 hours", 
                  ">10 hours"]

# Rearrange the categories
sns.catplot(x="study_time", y="G3",
            data=student_data,
            kind="bar",order=category_order)

# Show plot
plt.show()

```

Update the plot so that it no longer displays confidence intervals.

```
# List of categories from lowest to highest
category_order = ["<2 hours", 
                  "2 to 5 hours", 
                  "5 to 10 hours", 
                  ">10 hours"]

# Turn off the confidence intervals
sns.catplot(x="study_time", y="G3",
            data=student_data,
            kind="bar",
            order=category_order,ci=None)

# Show plot
plt.show()
```

<h2> Create and interpret a box plot </h2>

Use sns.catplot() and the student_data DataFrame to create a box plot with "study_time" on the x-axis and "G3" on the y-axis. Set the ordering of the categories to study_time_order.

```

# Specify the category ordering
study_time_order = ["<2 hours", "2 to 5 hours", 
                    "5 to 10 hours", ">10 hours"]

# Create a box plot and set the order of the categories

sns.catplot(x="study_time",y="G3",order=study_time_order,kind="box",data=student_data)



# Show plot
plt.show()

```

<h2> Omitting outliers</h2>

<br> Use sns.catplot() to create a box plot with the student_data DataFrame, putting "internet" on the x-axis and "G3" on the y-axis.
<br> Add subgroups so each box plot is colored based on "location".
<br> Do not display the outliers.


```
# Create a box plot with subgroups and omit the outliers

sns.catplot(x="internet",y="G3",hue="location",data=student_data,kind = 'box',sym="")




# Show plot
plt.show()

```


<h2> Adjusting the whiskers </h2>

Adjust the code to make the box plot whiskers to extend to 0.5 * IQR. Recall: the IQR is the interquartile range.

```

#Set the whiskers to 0.5 * IQR
sns.catplot(x="romantic", y="G3",
            data=student_data,
            kind="box")

# Show plot
plt.show()


```

Change the code to set the whiskers to extend to the 5th and 95th percentiles.


```

# Set the whiskers at the min and max values
sns.catplot(x="romantic", y="G3",
            data=student_data,
            kind="box",
            whis=[5, 95])

# Show plot
plt.show()

```

Change the code to set the whiskers to extend to the min and max values.

```
# Set the whiskers at the min and max values
sns.catplot(x="romantic", y="G3",
            data=student_data,
            kind="box",
            whis=[0,100])

# Show plot
plt.show()

```

<h2> Customizing point plots </h2>

Use sns.catplot() and the student_data DataFrame to create a point plot with "famrel" on the x-axis and number of absences ("absences") on the y-axis.


```
# Create a point plot of family relationship vs. absences
sns.catplot(x="famrel",y="absences",data = student_data,kind="point")


            
# Show plot
plt.show()

```

Add "caps" to the end of the confidence intervals with size 0.2.

```
# Remove the lines joining the points
sns.catplot(x="famrel", y="absences",
			data=student_data,
            kind="point",
            capsize=0.2)
            
# Show plot
plt.show()

```
Remove the lines joining the points in each category.

```

# Remove the lines joining the points
sns.catplot(x="famrel", y="absences",
			data=student_data,
            kind="point",
            capsize=0.2,join=False)
            
# Show plot
plt.show()

```







































