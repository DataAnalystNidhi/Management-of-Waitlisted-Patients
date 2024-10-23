# Management-of-Waitlisted-Patients


## Problem Statement
You have recently been hired as a Data Analyst for a well-known hospital that is currently facing challenges in determining the current number of patients and those on the waiting list. They require the data to be simplified yet detailed, accurately reflecting the current situation regarding patient numbers in the hospital.




##   Glossary

#### Inpatient
a patient who stays in a hospital while under treatment.

#### Outpatient
a patient who receives medical treatment without being admitted to a hospital.



## The Dataset

[Hospital_Patient_Waitlist_Dataset](https://github.com/DataAnalystChetan/Healthcare-Patient-Waitlist-Power-BI-Project/tree/main/Dataset)



## Objective
1. Track current status of patient waiting list
2. Analyze historical monthly trend of waiting list in Inpatient & Outpatient categories
3. Detailed specialty level & age profile analysis

#### Metrics Required
1.Average & Median Waiting List
2. Current Total Wait List

#### Data Scope
2018 - 2021



## Data Cleaning

 1. Combined and load all th "Inpatient" CSV files and load into power bi.
 2. Checked all data types of column are correct including date and numbers.
 3. checked and removed all blank rows from the dataset.
 4. Deleted all the duplicated values in the dataset.
 5. Combined and load all th "Outpatient" CSV files and load into power bi.
 6. Load "Mapping_Specialty" CSV file into software.

## Data Preparation

 1. In order to Append the Inpatient and Outpatient table Created the 'Case_type' column in outpatient table which was missing intially.
 2. Removed all the blank spaces in cells using the trim function.
 3. created a new Table called "All_data" by appendin 'Inpatient' and 'Outpatient' tables together.
 
 #### Created few measures in Power Bi using Dax for final repesentation.
 
> Average Wait List

    Average Wait List =  AVERAGE(All_Data[Total])

> Avg/Med Wait List

    Avg/Med Wait List =  SWITCH(VALUES('Calculation Method'[Cal Method]), "Average",[Average Wait List] , "Median", [Median Wait list])

> Dynamic Title

    Dynamic Title =  SWITCH(VALUES('Calculation Method'[Cal Method]), "Average","Key Indicatores - Patient Wait list (Average)" , "Median", "Key Indicatores - Patient Wait list (Median)")

> Latest Month Wait List

    Latest Month Wait List =  CALCULATE(SUM(All_Data[Total]),All_Data[Archive_Date] = MAX(All_Data[Archive_Date])) + 0

> Median Wait list

    Median Wait list =  MEDIAN(All_Data[Total])

> NoDataLeft

    NoDataLeft =  IF(ISBLANK(CALCULATE (SUM(All_Data[Total] ) , All_Data[Case_Type] <> "Outpatient" ) ),"No Data For Selected Criteria" , "")

>  NoDataRight

    NoDataRight =  IF(ISBLANK(CALCULATE (SUM(All_Data[Total] ) , All_Data[Case_Type] = "Outpatient" ) ),"No Data For Selected Criteria" , "")

> PY Latest Month Wait List

    PY Latest Month Wait List =  CALCULATE(SUM(All_Data[Total]),All_Data[Archive_Date] = EDATE(MAX(All_Data[Archive_Date]), -12)) + 0





## Data Modeling

![enter image description here](https://github.com/DataAnalystChetan/Healthcare-Patient-Waitlist-Power-BI-Project/blob/main/Dashboard%20Images/Modeling.png)

## Dashboard

![enter image description here](https://github.com/DataAnalystChetan/Healthcare-Patient-Waitlist-Power-BI-Project/blob/main/Dashboard%20Images/Summary.png)

![enter image description here](https://github.com/DataAnalystChetan/Healthcare-Patient-Waitlist-Power-BI-Project/blob/main/Dashboard%20Images/Detail%20View.png)

![enter image description here](https://github.com/DataAnalystChetan/Healthcare-Patient-Waitlist-Power-BI-Project/blob/main/Dashboard%20Images/Drill%20Down.png)
