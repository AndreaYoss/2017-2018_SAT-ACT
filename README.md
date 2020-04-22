# SAT & ACT Analysis


##### Author: Andrea Yoss: [LinkedIn](https://www.linkedin.com/in/andreayoss)

---
## Table of Contents

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Analysis](#Analysis)
- [Data Dictionary](#Data-Dictionary)
- [Datasets](#Datasets)


---
## Problem Statement

As part of the college admissions process, students can take either the SAT or ACT assessment. While the purpose of both exams is to demonstrate [college readiness](https://www.usnews.com/education/best-colleges/articles/act-vs-sat-how-to-decide-which-test-to-take), the exams differ slightly in structure, scoring, timing, and content. Depending on a particular student's skillset, he or she might perform better in one exam over the other.  For example, while the ACT allows students to use calculators for all math problems, the SAT exam includes a math section that prohibits the use of a calculator; a student who is not strong in math or is susceptible to making careless errors when performing calculations, might perform better on the ACT compared to the SAT.

Since colleges and universities accept the scores of either exam, one would think that students choose to take the particular exam they believe they will do the best on. However, this is not typically the case due to financial limitations, as well as disparities in accessibility.

In recent years, states have developed partnerships with the ACT or the College Board, who runs the SAT.  These contracts not only provide students in the state with the ability to take the particular exam for free, but also in some cases, incorporate the exam into the curriculum.  For instance, in 2018, Illinois entered into a contract with the College Board, to exclusively provide high school students in their state with annual 9th-, 10th-, and 11th-grade tests, as well as use the SAT and PSAT exams as a measure of an Illinois school's overall performance, accounting for ["20% of that school's rating in acheivement and growth."](https://chicago.chalkbeat.org/2018/7/27/21105418/illinois-has-embraced-the-sat-and-the-act-is-mad-about-it)      

Partnerships between the states and exam providers benefit high school students by providing direct access to that particular exam for free; however, states that have entered into these contracts, and have incorporated these exams into their curriculum, actually have much lower scores than states that have not.
  
In this project, I set out to understand why states with 100% statewide participation, and prepare their students for the ACT or SAT exam exclusively, appear to doing worse than states that do not offer such support, with all their statewide total/ composite averages ranked in the bottom half of the country.    


---
## Executive Summary

Using the aggrecate SAT and ACT scores and participation rates by state for 2017 and 2018, I worked to understand why states with 100% participation for a particular exam tend to do worse on that exam, compared to states with lower participation rates.  

After importing my datasets, I cleaned them by removing all null values and verifying the data types for each feature. I then checked if the provided data was reasonable.  First, I evaluated if the data was even possible, given each variable's allowable range, as defined in my [data dictionary](#Data-Dictionary). Then, I analyzed the distributions of my features from the summary statistics of the data to determine if the data seemed reasonable. I compared any data values that seemed suspect to the source data for the exams, and replaced any incorrect values with the actual/ correct values.  

Through exploratory data analysis, I recognized some important relationships:
1. SAT Participation Rates and ACT Participation Rates have a negative correlation.
2. SAT Participation Rates and SAT Total Scores have a strong negative correlation.
3. ACT Participation Rates and ACT Composite Score have a strong negative correlation.
4. Exams from  2017 to 2018 are positively correlated for both the SAT and ACT.


---
## Analysis


### *Participation Rates*
From our analysis, we found that statewide average participation rates for one test in a given year were inversely proportional to statewide participation rates for the other test for that state in the same year - with approximate correlations in 2017 and 2018 = -0.84. Additionally, in most states, the average participation rates for a particular exam remained constant from year to year. Specifically, we found that the correlation between 2017 and 2018 SAT participation rates was 0.87, and the correlation between 2017 and 2018 ACT participation rates was 0.92.
  
However, we noticed that this trend did not hold in a few instances.  For example, from 2017 to 2018, the ACT participation rates in **Illinois** and **Colorado** decreased significantly (going from close to 100% to 43% and 30%, respectively), while at the same time, their SAT participation rates increased substantially, with both states going from <10% participation in the SAT to 100% participation).  Through external research, we found that these changes in participation from 2017 to 2018 were due to new partnerships between those particular statesa and the College Board, the entity that administers the SAT Exam. 
  
### Total/ Composite Scores
Both the SAT and ACT exams have a negative relationship between their participation rates and their total/ composite scores, with correlations of -0.87 and -0.86, respectively.  This is primarily due to **selection bias**. When the exam is not required for students in a particular state, and students have the choice whether or not to take it, students will likely only choose to take the exam if they feel they can do well on it (at least compared to the other exam).  Since the only students who end up taking non-required exams are the students who choose to take it, these states will have higher total/ composite scores, while having lower participation rates (compared to states where the exam is mandatory, i.e., 100% participation). 

#### Figure 1: 2018 ACT Participation vs. Composite Scores

![Figure 1: 2018 ACT Participation vs. Composite Scores](https://github.com/AndreaYoss/2017-2018_SAT-ACT/blob/master/Images/2018_ACT.png)


<img src="../Images/2018_ACT.png"  width="1000" height="350">


#### Figure 2: 2018 SAT Participation vs. Total Scores
<img src="../Images/2018_SAT.png">


Take Illinois and Colorado, for example. When the SAT Exam became required in 2018, average total SAT scores *decreased* from 2017 to 2018, by approximately 15% in Colorado and 9% in Illinois, while at the same time, average composite ACT scores *increased* from 2017 to 2018, by approximately 15% in Colorado and 12% in Illinois.


---
## Datasets

|Name|Description|
|---|---|
|[2017 SAT Scores](./data/sat_2017.csv)|This dataset includes aggregate SAT scores and participation rates by state for 2017|
|[2017 ACT Scores](./data/act_2017.csv)|This dataset includes aggregate ACT scores and participation rates by state for 2017|
|[2018 SAT Scores](./data/sat_2018.csv)|This dataset includes aggregate SAT scores and participation rates by state for 2018|
|[2018 ACT Scores](./data/act_2018.csv)|This dataset includes aggregate ACT scores and participation rates by state for 2018|


---
## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|The name of a State located in the United States of America|
|sat_participation_17|float|SAT|The SAT participation rate of eligible students in a specific state in 2017 (units in %); range from 0-100| 
|act_participation_17|float|ACT|The ACT participation rate of eligible students in a specific state in 2017 (units in %); range from 0-100| 
|act_english_17|float|ACT|The average english section score in the ACT across exam takers in a specific state in 2017; range from 1-36|
|act_math_17|float|ACT|The average math section score in the ACT across exam takers in a specific state in 2017; range from 1-36|
|act_reading_17|float|ACT|The average reading section score in the ACT across exam takers in a specific state in 2017; range from 1-36|
|act_science_17|float|ACT|The average science section score in the ACT across exam takers in a specific state in 2017; range from 1-36|
|act_composite_17|float|ACT|The average ACT composite score in the ACT across exam takers in a specific state in 2017; a student's composite score is the average of his/ her section scores (english, math, reading, and science); range from 1-36|
|sat_math_17|int|SAT|The average math section score in the SAT across exam takers in a specific state in 2017; range from 200-800|
|sat_reading_and_writing_17|int|SAT|The average reading/ writing section score in the SAT across exam takers in a specific state in 2017; range from 200-800|
|sat_total_2017|int|SAT|The total is the average total SAT score across exam takers in a specific state; a student's total score is the sum of his/ her section scores (math and reading/writing) in 2017; range from 400-1600|
|sat_participation_18|float|SAT|The SAT participation rate of eligible students in a specific state in 2018 (units in %); range from 0-100| 
|act_participation_18|float|ACT|The ACT participation rate of eligible students in a specific state in 2018 (units in %); range from 0-100| 
|act_composite_18|float|ACT|The average ACT composite score in the ACT across exam takers in a specific state in 2018; a student's composite score is the average of his/ her section scores (english, math, reading, and science); range from 1-36|
|sat_math_18|int|SAT|The average math section score in the SAT across exam takers in a specific state in 2018; range from 200-800|
|sat_reading_and_writing_18|int|SAT|The average reading/ writing section score in the SAT across exam takers in a specific state in 2017; range from 200-800|
|sat_total_2018|int|SAT|The total is the average total SAT score across exam takers in a specific state; a student's total score is the sum of his/ her section scores (math and reading/writing) in 2018; range from 400-1600|