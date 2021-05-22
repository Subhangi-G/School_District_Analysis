# School_District_Analysis

## Overview of Project 

### Purpose
The purpose of this project is to aggragate the data from a city school district, to perform analyses, in order to provide insights about performance trends with respect to various school and district metrics.\
In this case, the analyses is performed to make sure that the state testing standards are upheld in the event of propable academic dishonesty, amongst ninth graders of Thomas High Schools, in this particular school district.\
To that end, the reading and the math scores, of ninth graders at Thomas High School, are replaced by NaN values.\
A school district analysis is then performed to update the following metrics.
- The district summary.
- The schools summary.
- The top 5 performing schools, based on the overall passing rate.
- The bottom 5 performing school, based on the overall passing rate.
- The average math score for each grade level from each school.
- The average reading score for each grade level from each school.
- The scores by school spending per student.
- The scores by school size.
- The scores by school type.

### Resources used
- Data Source : schools_complete.csv, students_complete.csv
- Software : Python 3.7.9, Jupyter Notebook 6.1.4, Pandas 1.1.3, Numpy 1.17.0, Anaconda 1.7.2

## Results 
The student data file and school data file were read into Jupyter Notebook as dataframes.\
The math and reading scores, of the ninth graders from Thomas High School, are to be disregarded. To achieve this, they were successfully changed to NaNs in the student data frame. (The student names are hidden to protect privacy)
![NaNs](https://user-images.githubusercontent.com/71800628/119212212-75343980-ba7c-11eb-8714-6f81fd9b3f4b.png)

### The District Summary:
The modified student dataframe, and the school dataframe were then merged (school_data_complete_df), and this was used in the following analyses.\
The total number of schools, and the total budget for the district were extracted from the dataframe, as shown below;
```
# Calculate the Totals (Schools and Students)
school_count = len(school_data_complete_df["school_name"].unique())
student_count = school_data_complete_df["Student ID"].count()

# Calculate the Total Budget
total_budget = school_data_df["budget"].sum()
```
The total number of students, used for calculating passing percentages, were adjusted to exclude the ninth graders from Thomas High School, and this was used in further analyses to obtain the district summary.\
The average and math and reading scores, of students accross the district, were calculated.\
The passing grade was set at 70%. The percentage of students who passed  math, reading, and math-and-reading together were calculated for the whole district. Part of the code is referenced below.
```
# Calculate the students who passed both reading and math.
per_passing_math_reading = school_data_complete_df[(school_data_complete_df["reading_score"] >= 70)
                                               & (school_data_complete_df["math_score"] >= 70)]
```
\
All of the information for the district were then summarized into a district summary dataframe, shown below.

![school_district_summary](https://user-images.githubusercontent.com/71800628/119212298-0f947d00-ba7d-11eb-81b7-db2b51e6530a.png)

### The Schools Summary:
For the school summary, the type of each school, whether district or charter, was extracted from the school dataframe.\
Information similar to what was obtained, and calculated for the district summary, were obtained for each high school in the district.\
The data for the passing percentage of students, for Thomas High School, were adjusted for the missing ninth graders.\
All the information were then summarized into the school summary.

### The 5 Top and Bottom Performing Schools:
The five top, and bottom performing schools, based upon their overall passing grade, were obtained from the school summary dataframe.\
The 5 top performing schools is referenced below.

![top_5_schools](https://user-images.githubusercontent.com/71800628/119212367-744fd780-ba7d-11eb-9271-54aa084a3d8e.png)

### The Average Math and Reading Scores for each grade type from each school:
The math and reading scores, for each grade, were obtained from the merged dataframe, and then grouped by each school to get the average for each school.\
Part of the code, used for math scores, is referenced below.
```
# Create a Series of scores by grade levels using conditionals.
ninth_graders_math = school_data_complete_df[(school_data_complete_df["grade"] == "9th")]["math_score"]
tenth_graders_math = school_data_complete_df[(school_data_complete_df["grade"] == "10th")]["math_score"]
eleventh_graders_math = school_data_complete_df[(school_data_complete_df["grade"] == "11th")]["math_score"]
twelfth_graders_math = school_data_complete_df[(school_data_complete_df["grade"] == "12th")]["math_score"]

# Group each school Series by the school name for the average math score.
ninth_grade_avg_math = ninth_graders_math.groupby([school_data_complete_df["school_name"]]).mean()
tenth_grade_avg_math = tenth_graders_math.groupby([school_data_complete_df["school_name"]]).mean()
eleventh_grade_avg_math = eleventh_graders_math.groupby([school_data_complete_df["school_name"]]).mean()
twelfth_grade_avg_math = twelfth_graders_math.groupby([school_data_complete_df["school_name"]]).mean()
```
### The Scores by School Spending Per Student:
The maximum and minimum budget per student, from the school summary dataframe, was used to create four spending bins.
```
# Establish the spending bins and group names.
spending_bins = [0, 585, 630, 645, 675]
group_names = ["<$584", "$585-629", "$630-644", "$645-675"]
```
The schools were then put into the appropriate spending bins and the scores and passing percenatges were calculated for each of the spending bins.

### The Scores by School Size, and School Type:
Four bins for school size were created, and schools were assigned to the bins depending upon their total number of students.
```
# Establish the bins.
size_bins = [0, 1000, 2000, 5000]
group_names = ["Small (<1000)", "Medium (1000-2000)", "Large(2000-5000)"]
```
The scores and passing percentages for each bin were then calculates.\
Similar analyses was done depending upon the type of school, whether district or charter.

## Analysis
A comparison was done between the metrics obtained before, and after the replacement of the grades, of ninth graders from Thomas High School.
- The district summary did not show much change. The average reading scores were identical, and the other numbers were only very slightly lower after the analyses.
- The school summary is not expected to change overall.\
The only expected change would be for Thomas High School, which was negligible after the calculations were adjusted to include only students from 10th through the 12th grade.This can be seen below.\
From analysis before replacing ninth grade scores:

![THC_before_replacement](https://user-images.githubusercontent.com/71800628/119212875-d6f6a280-ba80-11eb-9e03-e780b2dfec0f.png)

From From analysis after replacing ninth grade scores:

![THC_after_replacement](https://user-images.githubusercontent.com/71800628/119212882-e37afb00-ba80-11eb-9137-028aa97e06eb.png)

- Thomas High School still figured within the top 5 performing schools. The removal of ninth grade scores did not have any visible impact.
- No changes were observed in the average math scores, for each grade level, from each school, except the scores for the ninth graders from Thomas High School were removed.

![math_grade_per_school](https://user-images.githubusercontent.com/71800628/119212942-4c627300-ba81-11eb-9eef-969dd1b41e56.png)

- Similarly, no changes were observed in the average reading scores, for each grade level, from each school, except the scores for the ninth graders from Thomas High School were removed.
- The scores by school spending per student were not impacted. This is expected because the scores of ninth graders will not impact the school budget for each student.\
However, it is observed is that higher budget per student does not have a positive impact on student performace. On the contrary, there is a negative correlation between spending per student and the scores. 
- The scores by school size were not impacted after replacing the grades, for similar reasons as above. Schools with greater than 2000 students performed markedly lower, as seen below.\

![school_size_analysis](https://user-images.githubusercontent.com/71800628/119212522-9007ad80-ba7e-11eb-810f-abee27d784d2.png)

- The scores by the school type were not impacted by the analyses for similar reasons. However charter schools performed better than district schools.

![school_type_analysis](https://user-images.githubusercontent.com/71800628/119212532-9ac24280-ba7e-11eb-90e1-186414b5faf6.png)


## Summary
Replacing the math and reading scores of ninth graders from Thomas High School did not have any visible impact on the overall analysis.\
However a change was observed in the category of student passing percentage in math, reading , and math and reading taken together.
1. Percentage of students passing math was 66.9% which changed to 93.2%
2. Percentage of students passing reading was 69.7% which changed to 97.%
3. Overall percentage of students passing math and reading changed from 65.1 to 90.6%\
The changes observed are expected because the total number of students used to calculate the percentages were adjusted to only include the students from the 10th through 12 grade. This would give a more accurate number because the grades taken into consideration are of the 10th through the 12th grade students.
