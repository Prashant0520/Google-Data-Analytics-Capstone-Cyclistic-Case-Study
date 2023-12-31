# Google-Data-Analytics-Capstone-Cyclistic-Case-Study
Course: [Google Data Analytics Capstone: Complete a Case Study](https://www.coursera.org/learn/google-data-analytics-capstone)
## Background
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geo-tracked and locked into a network of 692 stations across Chicago.
Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.
## Scenario
I am assuming to be a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve our recommendations, so they must be backed up with compelling data insights and professional data visualizations.
## Stakeholders
This report also seeks to identify the important stakeholders that are involved in the overall analysis. This includes:
- cyclistic users,
- director of marketing,
- Cyclistic marketing team
- Cyclistic executive team
## Data Source
I will analyze Cyclistic's historical trip data from Jan 2022 to Dec 2022, available at [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html), provided by Motivate International Inc. for public use.
We'll explore customer usage trends, but won't access personally identifiable information due to data-privacy restrictions. Thus, we can't link pass purchases to credit card details or determine casual riders' location or pass history.

## 1. Ask 

### Business Task
To maximize the number of annual memberships by converting casual riders to annual members.

#### Analysis Questions
Three questions will guide the future marketing program:
- How do annual members and casual riders use Cyclistic bikes differently?
- Why would casual riders buy Cyclistic annual memberships?
- How can Cyclistic use digital media to influence casual riders to become members?
##### Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

## 2. Prepare

### Data Organization
There are 12 files with naming convention of YYYYMM-divvy-tripdata and each file includes information for one month,such as the
- ride id >>>>  [ ride_id ]
- bike type >>>>  [ rideable_type ] 
- start time >>>>  [ started_at ]
- end time >>>>  [ ended_at ] 
- start station >>>>  [ start_station_name ] & [ start_station_id ]
- end station  >>>>  [ end_station_name ] & [ end_station_id ]
- start location >>>>  [ start_lat ] & [ start_lng ]
- end location >>>>  [ end_lat ] & [ end_lng ]
- and whether the rider is a member or not >>>>  [ member_casual ]

## 3. Process

Python is used to combine the various datasets into one dataset and clean it.
##### Reason:
A worksheet can only have 1,048,576 rows in Microsoft Excel because of its inability to manage large amounts of data. Because the Cyclistic dataset has more than 5.6 million rows, it is essential to use a platform other than MS Excel that supports huge volumes of data.
#### 1. Combining Dataset
12 csv files are uploaded as tables in the dataset '2022_tripdata'. Another table named "case_file_5000" is created, containing 5,667,717 rows of data for the entire year.
#### 2. Handling Null Value:
some columns have same number of missing values. This may be due to missing information in the same row i.e. station's name and id for the same station and latitude and longitude for the same ending station.
1. Total of 833064 rows have both start_station_name and start_station_id missing which needs to be removed.
2. Total of 892742 rows have both end_station_name and end_station_id missing which needs to be removed.
3. Total of 5858 rows have both end_lat and end_lng missing which needs to be remov
#### 3. Handling Duplicate Entries
There are no duplicate rows in the dataset
#### 4. Created Columns
1. New Column ride_length can be created to find the total trip duration.
2. New Column days_of_week and month can be created for analysis.
#### 5. Data Type Correction
To convert object data type of start_time & end_time columns into datetime data type
To convert object data type of ride_length into timedelta data type
#### 6. Handling Invalid Entries
ride_length with duration less than a minute and longer than a day are excluded

## 4. Analysis & Share
- First of all, member and casual riders are compared by the type of bikes they are using. 
![download (2)](https://github.com/Prashant0520/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/assets/120619315/5702f71c-aef1-4709-a80c-e259481539b4)
The members make 59.7% of the total while remaining 40.3% constitutes casual riders. Each bike type chart shows percentage from the total.

- The Bikes types used by riders
![download (4)](https://github.com/Prashant0520/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/assets/120619315/933ad7c7-5d91-49ef-bae6-f16abb0b542c)
Most used bike is classic bike followed by the electric bike. Docked bikes are used the least by only casual riders. 

- Next the number of trips distributed by the months and days of the week are examined.
![download (7)](https://github.com/Prashant0520/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/assets/120619315/6a1e0a6e-c97f-47ff-91ea-eee12450cca7)
![download (8)](https://github.com/Prashant0520/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/assets/120619315/5c95f202-a6e0-495a-a501-7db5021fc9d9)
__Months:__ When it comes to monthly trips, both casual and members exhibit comparable behavior, with more trips in the spring and summer and fewer in the winter. The gap between casuals and members is closest in the month of july in summmer.   
__Days of Week:__ When the days of the week are compared, it is discovered that casual riders make more journeys on the weekends while members show a decline over the weekend in contrast to the other days of the week. 
- The high frequency of ride-on days for all types of users is Saturday
- The high frequency of ride on days_of_week for member types of users is Thursday
- The high frequency of ride on days_of_week for casual types of users is Satuday

for more
https://github.com/Prashant0520/Google-Data-Analytics-Capstone-Cyclistic-Case-Study/blob/main/Cyclistic-Bikesharing-Case-Study.ipynb

#### Summary:

|Casual|Member|
|------|------|
|Prefer using bikes throughout the day, more frequently over the weekends in summer and spring for leisure activities.|Prefer riding bikes on week days during commute hours (8 am / 5pm) in summer and spring.|
|Travel 2 times longer but less frequently than members.|Travel more frequently but shorter rides (approximately half of casual riders' trip duration).|

## 5. Act

After identifying the differences between casual and member riders, marketing strategies to target casual riders can be developed to persuade them to become members.
##### Recommendations:
- Marketing campaigns might be conducted in spring and summer at tourist/recreational locations popular among casual riders.
- Casual riders are most active on weekends and during the summer and spring, thus they may be offered seasonal or weekend-only memberships.
- Casual riders use their bikes for longer durations than members. Offering discounts for longer rides may incentivize casual riders and entice members to ride for longer periods of time.
- We have observed that approximately more than half of the casual members use classic_bike for travelling, so we can offer special incentives in order to increase conversion from casual to annual.
