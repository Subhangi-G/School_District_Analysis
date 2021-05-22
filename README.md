# School_District_Analysis

## Overview of Project 

### Purpose
The purpose of this analysis is to make sure that the state testing standards are upheld in the event of propable academic dishonesty amongst high schools of a particular school district.\
To that end, the reading and the math grades of ninth standard at Thomas High School are replaced by NaN values.\
A school district analysis is then performed to update the following metrics.\
- The district summary.\
- The schools summary.\
- The top 5 performing schools, based on the overall passing rate.\
- The bottom 5 performing school, based on the overall passing rate.\
- The average math score for each grade level from each school.\
- The average reading score for each grade level from each school.\
- The scores by school spending per student.\
- The scores by school size.\
- The scores by school type.\

### Resources used
- Data Source : schools_complete.csv, students_complete.csv
- Software : Python 3.7.9, Jupyter Notebook 6.1.4

## Results 
The student data file and school data file were read into the Jupyter Notebook as Dataframes.\
The math and reading scores of the ninth graders from Thomas High School were successfully changed to NaNs in the student data frame.



### The District Summary :
The changed student data frame and the school data frame were then merged, and this was used in the following analyses.\
The total number of school, and total budget for the district were extracted from the dataframe.\
The total number of students used for calculating percentages were adjusted to exclude the ninth graders from Thomas High School, and this was used in further analyses.\
The average and math and reading scores of students accross the district were calculated.\
The passing grade was set at 70%. The percentage of students who passed  math, reading, and math and reading together were calculated for the whole district.\
All of the information for the district was then summarized into a district summary dataframe, shown below.

### The Schools Summary:
For the school summary, the type of each school, whether district or charter, was extracted from the school dataframe.\
Information similar to what was obtained and calculated for the district, were obtained for each high school in the district.\
The data for the passing percentage of students for Thomas High School were adjusted for the missing ninth graders.\
All the information were then summarized into the school summary.

### The 5 Top and Bottom Performing Schools:
The top and bottom 5 performing schools were obtained from the school summary dataframe, based upon thier overall passing grade.\

### The Average Math and Reading Scores for each grade type from each school:
The math and reading scores for each grade were obtained from the merged dataframe, and then grouped by each school to get the average for each school.\

### The Scores by School Spending Per Student:
The maximum and minimum budget per student, from the school summary dataframe, was used to create four spending bins.\
The schools were then put into the appropriate spending bins and the scores and passing percenatges were calculated for each of the spending bins.

### The Scores by School Size, and School Type:
Four bins for school size were created, and schools were assigned to the bins depending upon their total number of students.\
The scores and passing percentages for each bin was then calculates. Similar analyses was done depending upon the type of school, whether district or charter.

## Analysis
A comparison was done between the metrics obtained before and after the replacement of the grades of ninth graders from Thomas High School.\
- The district summary did not show much change. The average reading scores were identical, and the other numbers were only very slightly lower after the analyses.\
- The school summary is not expected to change overall.\
The only expected change would be for Thomas High School, which was negligible after the calculations were adjusted to include only students from 10th through the 12th grade.\
- Thomas High School still figured within the top 5 performing schools. The removal of ninth grade scores did not have any visible impact.\
- No changes were observed in the average math scores for each grade level from each school, except the scores for the ninth graders from Thomas High School were removed.\
- Similarly, no changes were observed in the average reading scores for each grade level from each school, except the scores for the ninth graders from Thomas High School were removed.\
- The scores by school spending per student were not impacted. This is expected because the scores of ninth graders will not impact the school budget for each student.\
However, it is observed is that higher budget per student does not have a positive impact on student performace. On the contrary, there is a negative correlation between spending per student and the scores.
- The scores by school size were not impacted after replacing the grades, for similar reasons as above. Schools with greater than 2000 students performed markedly lower.
- The scores by the school type were not impacted by the analyses for similar reasons. However charter schools performed better than district schools.

## Summary
Replacing the math and reading scores of ninth graders from Thomas High School did not have any visible impact on the overall analysis.\
However a change was observed in the category of student passing percentage in math, reading , and math and reading taken together.
1. Percentage of students passing math was 66.9% which changed to 93.2%\
2. Percentage of students passing reading was 69.7% which changed to 97.%\ 
3. Overall percentage of students passing math and reading changed from 65.1 to 90.6% \
The changes observed are expected because the total number of students used to calculate the percentages were adjusted to only include the students from the 10th through 12 grade. This would give a more accurate number because the grades taken into consideration are of the 10th through the 12th grade students.
