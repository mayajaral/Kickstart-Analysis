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
![Pivottablelaunchdatafilters](https://github.com/mayajaral/Kickstart-Analysis/blob/master/ReadMEImages/Pivottablelaunchdatafilters.PNG)

And the outcome of:
![Pivottablelaunchdata.PNG](https://github.com/mayajaral/Kickstart-Analysis/blob/master/ReadMEImages/Pivottablelaunchdata.PNG)


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
![OutcomesGoals.PNG](https://github.com/mayajaral/Kickstart-Analysis/blob/master/ReadMEImages/OutcomesGoals.PNG)
### Challenges and Difficulties Encountered
The challenges were encountered in utilizing the COUNTIF function as it requires a specific formatting and multiple filtering criteria to accurately use. This took some experimenting to reach the correct result and determine the parameters & limitations of the COUNTIF function. 
## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
![Theater_Outcomes_vs_Launch.PNG](https://github.com/mayajaral/Kickstart-Analysis/blob/master/Resources/Theater_Outcomes_vs_Launch.PNG)
  1. We see that May is the best month to launch a campaign, as it boasts a 110% percenting funding for succesful campaigns. The range of April to August all show good results for funding. This indicates the summer months see a high volume of succesful campaigns.
  2. We see that December is the worst month to launch a campaign, with a downward trend of campaign success from October to December, indicating that the winter months are not good for funding. This could be due to the added expenses of the school year as well as the Thanksgiving and Winter holidays with their additional household expenses in food costs, gifts and travel. 
- What can you conclude about the Outcomes based on Goals?
![OOutcomes_vs_Goals.png](https://github.com/mayajaral/Kickstart-Analysis/blob/master/Resources/Outcomes_vs_Goals.png)
The graph indicates that the lower the goal outcome the more likely the campaign is to be succesful, with the price increase correlating to a higher failure and lower success rate. The anomoly in this trend are the 35000 to 45000 data points which also show a high success rate, probably due to confounding factors or specific large donors. Largely though a lower goal indicates a higher chance of success.
- What are some limitations of this dataset?
  - The dataset does not provide data on individual donations made to these campaigns, which is most relevent in identifying large donations. The lack of specificity of large donations that drastically change the outcome of the campaign makes it difficult to identify anomolies or to track the selection criterea of large donors. 
  - The dataset does not provide data on the social media or outreach efforts made by the campaign. This data would give insight into whether outreach effects outcome, especially across social media. This data would be useful in developing a marketting plan to potentially improve results.
- What are some other possible tables and/or graphs that we could create?
  - The length of the campaign in relation to the outcome would be a useful metric could provide another evaluatory metric. 
  - The effectiveness of the Kickstarter spotlight feature in improving the outcomes of campaigns in similar categories, goals and launch data brackets. 
  
