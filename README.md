# School District Analysis

## Project Overview

The Chief Data Sciencist for a city school district has given you the following tasks to complete to analyze data on student funding and standardized test scores to uncover insights, performance trends and patterns.

  1. Top 5 and bottom 5 performing schools, based on overall passing rate.
  2. The average math and reading scores received by students in each grade level at each school.
  3. School performance based on the budget per student.
  4. School performance based on the school size.
  5. School performance based on the type of school.

## Resources

  1. Data Source: schools_complete.csv, students_complete.csv
  2. Software: Python 3.7.6, Jupyter Lab 1.2.6
  
  - One thing to note, when you look at the files, Github does not render all the outputs correctly. However, if you run them on your own or use the following site below, the results will render correctly. 
  
    > https://nbviewer.jupyter.org/
 
 - When you load the page, copy the URL for this repository (School_District_Analysis) and paste it into their search bar and press 'Go!'.
 - You will get to choose which file to view, along with the output correctly rendered.
 
## Challenge

After completing the following tasks, we discovered that the score averages for ninth graders from Thomas High School are incorrect. After assessing the situation with the school superintendent and the chief data scientist, we decide the best approach is to:

- Replace the ninth-grade math and reading scores from Thomas High School.
- Keep all other data associated with the ninth-grade students and Thomas High School intact.

## Method

To compare the results between these changes:

1. We created a duplicate notebook to conduct the changes.
2. Corrected the students' names so there are no professional prefixes or suffixes.
3. Replace the reading and math scores for ninth graders at Thomas High School with NaN.
   - Use *loc* on the *student_data_df* DataFrame to select the columns by condition.
   - Set the column you want equal to 'NaN' by using *np.nan* for the reading and math scores separately.
   - In order to use *np.nan*, you will need to import Numpy.
4. Your code to do step 3 will look like the following:

  > student_data_df.loc[(student_data_df['grade'] == '9th') & (student_data_df['school_name'] == 'Thomas High School'), ['reading_score', 'math_score']] = np.nan

5. Merge the clean student data with the school dataset.

## Summary

After replacing the reading and math scores, we are able to answer a few questions about how the results from PyCitySchools and PyCitySchools Challenge were affected. The results shows the following:

### 1. District Summary

| |PyCitySchools DataFrame|PyCitySchools Challenge DataFrame|
|-|----------------------|--------------------------------|
|Average Math Score|79.0|78.9|
|Average Reading Score|81.9|81.9|
|% Passing Math|75%|74%|
|% Passing Reading|86%|85%|
|% Overall Passing|65%|64% |
 
As we can see, the replacement changed the Average Math Score dropping by .1 and a reduction by 1% for % Passing Math, % Passing Reading and % Overall Passing.

### 2. School Summary

When we look at the School Summary DataFrame, we look at the results for Thomas High School because the data removed was only from Thomas High School and the other schools' results were not affected. (The data below has been rounded to two decimal places for the math and reading scores, and rounded to the nearest whole number for the % Passings)

| |PyCitySchools DataFrame|PyCitySchools Challenge DataFrame|
|-|----------------------|--------------------------------|
|Average Math Score|83.42|83.36|
|Average Reading Score|83.85|83.90|
|% Passing Math|93%|67%|
|% Passing Reading|97%|70%|
|% Overall Passing|91%|65%|

We see some drastic changes with the % Passing columns, dropping around 25% after changing the math and reading scores NaN for students at Thomas High School. The Average Math Score dropped by .6 and the Average Reading Score went up by .05.

### 3. Thomas High School's performance, relative to the other schools, after replacing ninth graders' math and reading scores

1. PyCitySchools DataFrame:

| Top 5 | % Overall Passing | | Bottom 5 | % Overall Passing |
|-------|-------------------|-|----------|-------------------|
| Cabrera High School| 91.33%| | Rodriguez High School| 52.99%|
| Thomas High School| 90.95%| | Figueroa High School| 53.20%|
| Griffin High School| 90.60%| | Huang High School| 53.51%|
| Wilson High School| 90.58%| | Hernandez High School| 53.53%|
| Pena High School| 90.54%| | Johnson High School| 53.54%|

2. PyCitySchools Challenge DataFrame:

| Top 5 | % Overall Passing | | Bottom 5 | % Overall Passing |
|-------|-------------------|-|----------|-------------------|
| Cabrera High School| 91.33%| | Rodriguez High School| 52.99%|
| Griffin High School| 90.60%| | Figueroa High School| 53.20%|
| Wilson High School| 90.58%| | Huang High School| 53.51%|
| Pena High School| 90.54%| | Hernandez High School| 53.53%|
| Wright High School| 90.33%| | Johnson High School| 53.54%|

Within these tables, we have rounded the data to two decimal places. Before we adjusted the ninth graders' reading and math scores, Thomas High School was 2nd place in the Top 5 performing schools. After the scores were changed to 'NaN', Thomas High School's % Overall Passing became 65%, which takes the school out of the Top 5, but not low enough to be put into the Bottom 5 performing schools. 

One thing to note, before and after the adjustments, there weren't any changes to the Bottom 5 performing schools.

### 4. Math and Reading Scores by Grade 

Replacing the ninth graders' math and reading scores changes one aspect for the math and reading scores by grade DataFrame. All other values remain the same except when you scroll down to the row for Thomas High School after the adjustments, the average score for the 9th grade shows 'nan'.

### 5. Scores by School Spending

Replacing the ninth graders' math and reading scores only changes their averages and percentage passings for Thomas High School (refer to School Summary). It did not affect their school spending in terms of the numbers.

  - Total Students: 1635
  - Total School Budget: $1,043,130.00
  - Per Student Budget: $638.00
  - Spending Ranges (Per Student): $630-644
  
However, when you take the overall passing for the spending per student range, we see the following:

1. PyCitySchools DataFrame:

|Spending range| % Overall Passing|
|--------------|------------------|
| <$584| 90.37|
|$585-629|81.42|
|$630-644|62.86|
|$645-675|53.53|

2. PyCitySchools Challenge DataFrame:

|Spending range| % Overall Passing|
|--------------|------------------|
| <$584| 90.37|
|$585-629|81.42|
|$630-644|56.39|
|$645-675|53.53|

We see here that after we replaced the math and reading scores, there was a 6% drop for the % Overall Passing in the $630-644 spending range.

### 6. Scores by School Size

After running the code and replacing the math and reading scores to 'NaN', we see a few numbers have changed. Since Thomas High School has 1635 students, they are within the medium category for school size, which will be the results that you see below.

|School Size - Medium (1000-2000) |PyCitySchools DataFrame|PyCitySchools Challenge DataFrame|
|-|----------------------|--------------------------------|
|Average Math Score|83.4|83.4|
|Average Reading Score|83.9|83.9|
|% Passing Math|94%|88%|
|% Passing Reading|97%|91%|
|% Overall Passing|91%|85%|

We see that the Average Math and Reading Score does not change, however, the % Passing for Math, Reading and Overall Passing has reduced by 6%.

### 7. Scores by School Type

We ran a quick check and identified Thomas High School's school type was Charter. We displayed the change between the two files below:

|School Type - Charter|PyCitySchools DataFrame|PyCitySchools Challenge DataFrame|
|-|----------------------|--------------------------------|
|Average Math Score|83.5|83.5|
|Average Reading Score|83.9|83.9|
|% Passing Math|94%|90%|
|% Passing Reading|97%|93%|
|% Overall Passing|90%|87%|

We see that the change for the % Passings dropped around 4%, and the Average Math and Reading Scores remain the same.

### Challenge Summary

After looking at these results and the differences it shows after the changes, there are some more questions that we may consider looking into:

1. How were the math and reading scores changed in the first place? Is this a one-time incident or does this happen often?
2. If this happened once, should this change the way Thomas High School is funded?

Aside from these questions, it seems that there was an average 4-6% change to the % Passing Math, % Passing Reading and % Overall Passing. The only change that was a lot greater was the School Summary DataFrame for Thomas High School with their % Passings dropping around 25%. When we look at other data, we see that school sizes larger than 2000 students has a lower average as opposed to the schools with less than 1000 students and schools with 1000-2000 students.

### Usage

If you would like to run this code on your own computer and play around the numbers to get your own results:

1. Download Anaconda to your computer and install Jupyter Notebook/Jupyter Lab if you don't already have it.
2. Create a Development Environment that has all the required packages need to run this code.
    - I am using Windows, so the following is how to open it on Windows.
    - Open your Anaconda Command Prompt and type the following:

      > conda create -n PythonData python=3.7 anaconda

3. Download the files you would like to run and save them in a folder together.
4. Open the Anaconda Command Prompt (if not already opened) and navigate to the folder holding your downloaded files.
6. Once you are in that directory, type *jupyter lab* or *jupyter notebook*.
7. It will open a webpage and you will have access to the two files in your side panel.
