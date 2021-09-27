# Campaign Analysis – Theater Outcomes and Play Goals
## Overview
### The analysis provided in the following was for a returning customer named Louise. Louise has been participating in fundraising activities and is using our analysis to focus her efforts and identify strategies to implement successful Kickstarter campaigns in the future. 
Louise recently had a Kickstarter campaign close for the play *Fever*, she wants to compare how similar campaigns for plays preformed in relation to their launch dates. Louise would also like to better understand the relationship between the funding dollar goal and the overall success of play campaigns. 
---
## Analysis and Challenges: 
### Using the dataset that was provided to us by Louise in an excel file, we first had to distill the data in order to get more relevant and easily understood datapoints for this analysis. Since Louise wanted to wanted to know outcomes based on launch dates, one of the first challenges in breaking down the data so that it was easier to understand required us to convert the existing date related data that was listed with the Unix timestamps to a standard date format using the following formula:
=(((J2/60)/60)/24)+DATE(1970,1,1)
Using the result of the above formula we also created a new data field showing the year only using the following formula: 
=YEAR(S2)
Once those data fields were generated, we were able to pivot the data in excel. Using the pivot table generated, we created two filters. The first filter was for the Parent Category, for Louise’s analysis we have it set to “theater” only. The second filter is for the years of the campaigns, this will enable Louise to filter by year in the event she would like to do further analysis. 
Below, there is an image of the chart we generated for Louise’s analysis. This chart shows the count of theater fundraising campaign outcomes by month. In the future, we’ll reference this chart as “Theater Outcomes Based on Launch Date” 
---
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/90698381/134994790-e5949fdc-358e-4fc4-a555-3743e23be6ee.png)
---
### The next area that Louise wanted to gain further insight on was the relation of play funding goals to their successes. We used the pre-determined ranges that were set by Louise to aggregate the count of successful, failed, and canceled play campaigns. Using the dataset provided to us, we created a COUNTIFS function in excel to generate another table. The formula for this function varied by range but below is an example of a formula we used to find the successful play campaigns that had a funding goal of 1,000 dollars to 4,999 dollars. 
=COUNTIFS(Kickstarter!$D:$D, ">=1000",Kickstarter!$D:$D, "<=4999", Kickstarter!$F:$F,"successful", Kickstarter!$R:$R,"plays")
One challenge with this formula is that it was not consistent across all ranges and we needed to manually adjust for each range as well as the outcome. 
As percentage is a better representation than a simple number, we further distilled the results of the COUNTIFS function to show the percentage of each category in relation to its outcome. Below is the chart we generated for this analysis and for future reference it will be referred to as “Outcomes Based on Goal”. 
---
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/90698381/134994833-9b2e6a28-8285-4590-8202-4ffd3e70fb56.png)
---
## Results: 
### Conclusions based on Theater Outcomes by Launch Date: 
- Based on our findings, the number of successful campaigns peak in May, taper off in the months that follow with the lowest rate of success in December. 
- The spring and summer months appear to have the highest volume of campaigns overall and during that time there appear to be more failed campaigns, it is visible that with zero cancelations in the moth of October there is a sharp increase in failed campaigns. 
### Conclusions based on Outcomes Based on Goal:
- Based on the chart and data we referenced, the highest rate of success to failure is when campaigns have a goal of 1000 dollars or less. The rate of success appears to decline as the goal increases. While the chart shows moderate success with campaigns 35000 dollars to 45000 dollars the over all trend is that there is a lower rate of success when the goal increases. One limitation of showing the percentage of outcomes in the chart is that there is not a visual for the volume of campaigns for each goal range. 
### Limitations of Dataset: 
While somewhat compressive for the analysis currently required there are inherent limitations of the data set used for Louise’s analysis. At only a few thousand records, the sample is somewhat small. Having the dataset provided to us by Louise may bring into question its reliability. While the country is provided there may not be enough granularity to create actionable insights geographically. The goal and pledged values in the data set appear to be in dollars, I do not feel it would be safe to assume that this field is truly listed in dollars based on the variations in the country for each campaign. It could be possible that goal and pledge amounts would have different results converted into a single currency.  
Future Analysis: 
Many tables and charts could be created with the dataset provided. In relation to the analysis that Louise is preforming, creating a more compressive chart showing outcomes based on date overlapped with goal amount for would tell a better story for outcomes than simply listing the number of theater outcomes by date. We also feel that showing the volume of campaigns in relation to the percentage of outcomes based on goal would create a more meaningful insight into the outcome of play campaigns.
