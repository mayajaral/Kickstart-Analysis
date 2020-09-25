# Kickstarting with Excel

## Overview of Project

### Purpose
The purpose of the project is to help Louise determine the best parameters to accquire succesful funding for her play *Fever* by analyzing Kickstarter, an online crowdfunding platform, data via Excel.
## Analysis and Challenges
The data was analyzed using Excel pivot tables, filtering & conditionals. To aquire a holistic understanding of the data new columns were created with unique analysis-
1. Percentage funding
   - The percentage funding was calculated using the **pledge**(E) and **goal**(D).
     -  =ROUND(E2783/D2783*100,0) 
2. Average Donation
   - The average donations were determined by dividing the **pledge** (E) amount by the **backers_count** (L) to obtain the average contribution. 
     -  =IFERROR(ROUND(E2783/L2783,2),0) 
3. Parent category & subcategory
   - The parent and subcategory columns were divided to provide for easier filtering and pivot table analysis.
4. Date Created, Date Ended, Years
   - The dates were originally available in UNIX time and were converted to readable dates and then had the years extracted.
     - Date Created
       -  =(((J2783/60)/60)/24)+DATE(1970,1,1)
     - Date Ended
       -  =(((I2783/60)/60)/24)+DATE(1970,1,1) 
     - Years
       -  =YEAR(S2783) 
### Analysis of Outcomes Based on Launch Date
The analysis of the outcome based on the launch date was performed using a pivot table. The pivot table was filtered via Parent Category and Years. The columns were the Outcomes, the rows were the Dates Created and the values were the number of successful, failed or cancelled outcomes. 
This looked like this filtering:

With this pivot table:

And the outcome of:


### Analysis of Outcomes Based on Goals
The analysis of the outcomes based on goals was performed using the COUNTIF function. This function was used to calculate the number of successes, failures and cancelled projects based on their goal bracket and subcategory. The formulas used were-
1. Number Successful
   - Less than 1000
     - =COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, "<1000", Kickstarter!$R:$R, "plays")
   - Brackets of 5000 between 1000 and 50000
     - =COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, ">=1000",Kickstarter!$D:$D, "<=4999", Kickstarter!$R:$R, "plays")
   - Greater than 50000
     - =COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, ">=50000", Kickstarter!$R:$R, "plays")
2. Number Failed
   - Less than 1000
     - =COUNTIFS(Kickstarter!$F:$F, "failed", Kickstarter!$D:$D, "<1000", Kickstarter!$R:$R, "plays")
    - Brackets of 5000 between 1000 and 50000
       - =COUNTIFS(Kickstarter!$F:$F, "failed", Kickstarter!$D:$D, ">=1000",Kickstarter!$D:$D, "<=4999", Kickstarter!$R:$R, "plays")
    - Greater than 50000
      - =COUNTIFS(Kickstarter!$F:$F, "failed", Kickstarter!$D:$D, ">=50000", Kickstarter!$R:$R, "plays")
3. Number Canceled
   - Less than 1000
     - =COUNTIFS(Kickstarter!$F:$F, "canceled", Kickstarter!$D:$D, "<1000", Kickstarter!$R:$R, "plays")
   - Brackets of 5000 between 1000 and 50000
     - =COUNTIFS(Kickstarter!$F:$F, "canceled", Kickstarter!$D:$D, ">=1000",Kickstarter!$D:$D, "<=4999", Kickstarter!$R:$R, "plays")
   - Greater than 50000
     - =COUNTIFS(Kickstarter!$F:$F, "canceled", Kickstarter!$D:$D, ">=50000", Kickstarter!$R:$R, "plays")
 
These numbers were then used to determine the percentage of total successful, failed and cancelled projects in each goal bracket, resulting in this table:

### Challenges and Difficulties Encountered

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
