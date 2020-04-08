# SAT & ACT Analysis


##### Author: Andrea Yoss: [LinkedIn](https://www.linkedin.com/in/andreayoss)


## Table of Contents

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Datasets](#Datasets)
- [Data Dictionary](#Data-Dictionary)
- [Conclusion](#Conclusion)
- [Data Sources](#Data-Sources)


## Problem Statement

In recent years, more and more students are taking the ACT exam over the SAT exam. The ACT has even partnered with States in the US to encorporate the test into each State's High School curriculum.  Unfortunately, these States that have incorporated the ACT test in their curriculum participation rates are actually seeing some of the worst average Composite scores in the United States of America.  
  
In this project, I set out to understand why states that prepare their students for the ACT exam exclusively, appear to doing worse than states that do not offer such support, with all their statewide Composite averages ranked in the bottom half of the country.  



## Executive Summary


Using the aggrecate SAT and ACT scores and participation rates by state for 2017 and 2018, I worked to solve this problem.

I started off by importing the [SAT Scores](./data/sat_2017.csv) and [ACT Scores](./data/act_2017.csv) for 2017, and confirming that the import was successful by displaying the first five rows of each dataset, using `.head()`.  I then [cleaned](#Data-Cleaning-Process) the data to allow for me to analyze it.

-
### Data Cleaning Process

1. Checked if the data was complete by looking for any null/ empty values in the data set.  I did not find any for either dataset.  

2. Tested if the provided numeric data was in the [range](#Table-1-Allowable-Range-for-Each-SAT_2017-and-ACT_2017-Numeric-Variable) of possible lower- and upper-bounds by checking if the actual min/max values for each of the variables in the datasets were in that allowable [range](#Table-1-Allowable-Range-for-Each-SAT_2017-and-ACT_2017-Numeric-Variable).  From the datasets, I noticed some issues resulting from the variable's data type (ie, the minimum and maximum Participation rates were incorrect in both data sets because its data type was an object/ string when it should be a float or integer value, as shown in [Table 2](#Data-Types-of-Each-Feature)), as well as issues with the data itself being multiple standard deviations away from the mean or outside the allowable [range](#Table-1-Allowable-Range-for-Each-SAT_2017-and-ACT_2017-Numeric-Variable) entirely.      
 
 
#### Table 1 Allowable Range for Each SAT_2017 and ACT_2017 Numeric Variable
|Test|Variable|Minimum Value|Maximum Value|
|---|---|---|---|
|SAT|Participation|0|100|
|SAT|Evidence-Based Reading and Writing|200|800|
|SAT|Math|200|800|
|SAT|Total|400|1600|
|ACT|Participation|0|100|
|ACT|English|1|36|
|ACT|Math|1|36|
|ACT|Reading|1|36|
|ACT|Science|1|36|
|ACT|Composite|1|36|
  

3. Fixed any errors I identified while checking the reasonability of numeric variables in the datasets and then renamed my columns to . To address any issues with the data values, I compared those values to the source data for the 2017 [SAT](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/) and the 2017 [ACT](https://www.act.org/content/dam/act/unsecured/documents/cccr2017/ACT_2017-Average_Scores_by_State.pdf) tests, and replaced those values with the correct ones, where needed. To convert data types to the [desired data type](#Data-Types-of-Each-Feature), I used the python function `.astype()` on the data, after removing any non-numeric characters.


#### Table 2 Data Types of Each Feature
|Test|Feature|Data Type|
|---|---|---|
|SAT|State|object|
|SAT|Participation|float|
|SAT|Evidence-Based Reading and Writing|int|
|SAT|Math|int|
|SAT|Total|int|
|ACT|State|object|
|ACT|Participation|float|
|ACT|English|float|
|ACT|Math|float|
|ACT|Reading|float|
|ACT|Science|float|
|ACT|Composite|float|

-

Once my data was clean, and unnecessary rows had been removed, I merged the 2017 ACT and SAT into a single dataframe, and exported my consolidated 2017 dataframe to a new csv file.  After importing, cleaning and merging the [2018 SAT dataframe](./data/sat_2018.csv) and the [2018 ACT dataframe](./data/act_2018.csv), I merged all dataframes into a single csv file that I used for most of my analyses.

Through exploratory data analysis, I recognized some important relationships:
1. SAT Participation Rates and ACT Participation Rates have a negative correlation
2. SAT Participation Rates and SAT Total Scores have a strong negative correlation
3. ACT Participation Rates and ACT Composite Score have a strong negative correlation
4. Exams from  2017 to 2018 are positively correlated for both the SAT and ACT


## Datasets

#### Table 3 Datasets
|Name|Description|
|---|---|
|[2017 SAT Scores](./data/sat_2017.csv)|This dataset includes aggregate SAT scores and participation rates by state for 2017|
|[2017 ACT Scores](./data/act_2017.csv)|This dataset includes aggregate ACT scores and participation rates by state for 2017|
|[2018 SAT Scores](./data/sat_2018.csv)|This dataset includes aggregate SAT scores and participation rates by state for 2018|
|[2018 ACT Scores](./data/act_2018.csv)|This dataset includes aggregate ACT scores and participation rates by state for 2018|



## Data Dictionary

#### Table 4 Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|The name of a State located in the United States of America|
|sat_participation_17|float|SAT|The SAT participation rate of eligible students in a specific state in 2017 (units in %) | 
|act_participation_17|float|ACT|The ACT participation rate of eligible students in a specific state in 2017 (units in %) | 
|act_english_17|float|ACT|The average english section score in the ACT across exam takers in a specific state in 2017|
|act_math_17|float|ACT|The average math section score in the ACT across exam takers in a specific state in 2017|
|act_reading_17|float|ACT|The average reading section score in the ACT across exam takers in a specific state in 2017|
|act_science_17|float|ACT|The average science section score in the ACT across exam takers in a specific state in 2017|
|act_composite_17|float|ACT|The average ACT composite score in the ACT across exam takers in a specific state in 2017; a student's composite score is the average of his/ her section scores (english, math, reading, and science)|
|sat_math_17|int|SAT|The average math section score in the SAT across exam takers in a specific state in 2017|
|sat_reading_and_writing_17|int|SAT|The average reading/ writing section score in the SAT across exam takers in a specific state in 2017|
|sat_total_2017|int|SAT|The total is the average total SAT score across exam takers in a specific state; a student's total score is the sum of his/ her section scores (math and reading/writing) in 2017|
|sat_participation_18|float|SAT|The SAT participation rate of eligible students in a specific state in 2018 (units in %) | 
|act_participation_18|float|ACT|The ACT participation rate of eligible students in a specific state in 2018 (units in %) | 
|act_composite_18|float|ACT|The average ACT composite score in the ACT across exam takers in a specific state in 2018; a student's composite score is the average of his/ her section scores (english, math, reading, and science)|
|sat_math_18|int|SAT|The average math section score in the SAT across exam takers in a specific state in 2018|
|sat_reading_and_writing_18|int|SAT|The average reading/ writing section score in the SAT across exam takers in a specific state in 2017|
|sat_total_2018|int|SAT|The total is the average total SAT score across exam takers in a specific state; a student's total score is the sum of his/ her section scores (math and reading/writing) in 2018|




## Analysis

Both the SAT and ACT exams have a negative relationship between their participation rates and their total scores.  When there are less students taking an the exam, and students have the choice whether or not to take it, there is a selection bias, as the students who take the exam will therefore do better than when the participation rate is greater, and more students who do not choose and may not be ready for the exam take it and get lower scores. Based on my exploration of the data, it seems that this is why 17 states with 100% participation in the ACT in 2018 fell below the mean, not the curriculum or state.

## Conclusion

---

## Data Sources


- 







