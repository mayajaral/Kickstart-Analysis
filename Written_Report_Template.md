# Kickstarting with Excel

## Overview of Project

### Purpose
The purpose of the project is to help Louise determine the best parameters to accquire succesful funding for her play *Fever* by analyzing Kickstarter, an online crowdfunding platform, data via Excel.
## Analysis and Challenges
The data was analyzed using Excel pivot tables, filtering & conditionals. To aquire a holistic understanding of the data new columns were created with unique analysis-
1. Percentage funding
The percentage funding was calculated using the **pledge**(E) and **goal**(D).
''' =ROUND(E2783/D2783*100,0) '''
2. Average Donation
The average donations were determined by dividing the **pledge** (E) amount by the **backers_count** (L) to obtain the average contribution. 
''' =IFERROR(ROUND(E2783/L2783,2),0) '''
3. Parent category & subcategory
The parent and subcategory columns were divided to provide for easier filtering and pivot table analysis.
4. Date Created, Date Ended, Years
The dates were originally available in UNIX time and were converted to readable dates and then had the years extracted.
  - Date Created
      ''' =(((J2783/60)/60)/24)+DATE(1970,1,1) '''
  - Date Ended
      ''' =(((I2783/60)/60)/24)+DATE(1970,1,1) '''
  - Years
      ''' =YEAR(S2783) '''
### Analysis of Outcomes Based on Launch Date

### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
