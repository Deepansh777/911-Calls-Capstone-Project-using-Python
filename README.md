# 911-Calls-Capstone-Project

The dataset was taken from [Kaggle](https://www.kaggle.com/mchirico/montcoalert). The data contains the following fields:

* **lat:** String variable, Latitude
* **lng:** String variable, Longitude
* **desc:** String variable, Description of the Emergency Call
* **zip:** String variable, Zipcode
* **title:** String variable, Title
* **timeStamp:** String variable, YYYY-MM-DD HH:MM:SS
* **twp:** String variable, Township
* **addr:** String variable, Address
* **e:** String variable, Dummy variable (always 1)

## Conclusion

This dataset helped us understand the emergency frequency due to natural causes (health issues, etc.) and human mistakes(fire accident, road accident, etc.). The dataset was acquired from Kaggle. There were about 80,000 missing values. Most of them were from the zip code column. 

The most common cause of 911 calls is EMS, followed by Traffic and Fire. EMS accounts for about 50% of the total calls. The EMS-related calls appear to be linearly increasing over the years. On investigating the causes further, it was found that Vehicle Accident is responsible for the highest number of the emergency call. During the data manipulation phase, month, day, hour, and year were extracted from the date. It was found out that most of the 911 calls were placed in the month of January, followed by June and March. The heatmap indicates that the highest number of 911 calls were made in March 2018. It looks like most number of calls were placed between Tuesday - Friday around 5 pm. On investigating the location of the calls, Lower Merion is the town with the highest number of calls.

**-- Deepansh Arora**
