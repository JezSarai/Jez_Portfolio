# Bellabeat Case Study

## Introduction
Bellabeat is a small but successful high-tech manufacturer of health products for women. The company has offices around the world and many products, such as an app, a wellness tracker, a smartwatch, a water bottle tracker, and a subscription-based membership. Their [webpage](https://bellabeat.com/) show more information about their products. Bellabeat uses traditional advertising media (radio, billboards, print, and television), it also uses mostly digital marketing in google search, social media pages such as: Facebook, Instagram, Twitter; it also runs ads on Youtube and Google Display Network for campaigns in marketing dates.
The main stakeholders are Urška Sršen (co-founder and Chief Creative Officer), Sando Mur (co-founder, key member of the executive team and mathematician), and the Bellabeat marketing analytics team.
Their objective is to become a larger company by applying insights of smart devices use to improve their products such as Time, a wellness watch.  To accomplish this, [Fitness Tracker Data](https://www.kaggle.com/arashnic/fitbit) was explored to observe users' daily habits. Thirty smartwatch users consented to share their personal tracker data (minute-level output for physical activity, heart rate, and sleep monitoring, among others).


## Problems
### Objective
The objective is to identify how consumers use non-Bellabeat smart devices in order to apply these insights in at least one of Bellabeat products. To accomplish this, the next tasks are going to be completed.
- Identify trends in consumer device usage
- Discover how to apply these to Bellabeat customers
- How to influence the marketing strategy using these

### About the data
The data involves 18 csv files (Fitness Tracker Data) with information such as minute-level output for physical activity, heart rate, sleep monitoring, weight, fat, BMI, among others. Thirty Fitbit users' information was recorded in these files. Thirty is the minimum sample size for any analysis to be significant. All files have an Id column that helps relate all of them.  The data comes from Amazon Mechanical Turk from December 3 to December 5, 2016.

The data might be outdated, but for the sake of the case study, it will be used. Also, usually, there is one table (weightLogInfo_merged.csv) with incomplete data implies the need to get more data from users or from other public databases, again, many assumptions will be made since this case study is made as a data analysis exercise. Most tables used were those with daily data, since it was more useful to know the daily and hourly average of variables rather than their average per minute or second.


A short description of each file, analysis, facts, assumptions, and major problems, can be found here. 

### Results
Most users:
- Are either healthy or overweight.
- Sleep an average of 7 hours a day, takes half an hour to fall asleep. Do not have enough sleep for an adult.
- Walk an average of 8319 steps per day. Which implies low activity, close to a sedentary life.
- Do an average of 102.8 MET minutes per week, not enough for optimal cardiovascular health.

### Weight and Health
Most users have a healthy weight, but a lot of them are overweight.
Underweight 0%
Healthy 50%
Overweight 37.5%
Obese 12.5%

### Counting Sheep: How long it takes users to fall asleep?
Users spend an average of 7.6 hours in bed. It takes them only 39.2 minutes (8.5%) to fall asleep.
It seems users go to sleep on time to get 8 hours of sleep without counting the time it takes them to fall asleep. That time does not even count the quality of sleep. Hence, users do not sleep enough, for an adult. 

### Step by Step: What is a healthy amount of steps?
According to the CDC, around 4,400 steps per day lowers mortality rate, this trend continues until the 7,500 spd. Also, 7,000-8,000 spd are sufficient to see results, however, adults should aim for 10,000 spd.
Users do more steps on Tuesday and Saturday. Also, they walk an average of 8319 steps a day, which is good, but can be better.

## The Heart of the Problem: METs and calories after an intensity session
Around 500 MET minutes per week must be reached for optimal cardiovascular health.  METs are also important to calculate calories burned per minute. Users do 102.8 average MET minutes a week, way too far from the goal. Also, users intake an average of 2,304 daily calories, which is a healthy amount. However, other factors influence on the amount of the optimal daily intake, for a person.

## Be Still My Beating Heart: Heart Rate
A normal heart rate for an adult is between 60-100 beats per minute while resting. The average maximum heart rate at 100 percent exertion must be between 150 and 200 bpm. The maximum heart rate was  80.52 beats per minute.  The minimum is 58.84 bpm. For an adult, a normal h.r. is between 60 to 100 bpm. At 4 a.m. some users, present a h.r. a little below the normal rate. Users have a mostly sedentary life, spending an average of 20 hours a day with sedentary activity. Note that, even on weekends, sedentary activity is high.

## Are they related?
Calories and Sedentary Minutes are significantly correlated. (p-value = 5.093x10^-8) While it seems like, the number of steps and METs are not correlated.
(p-value = 0.58)

## Review
Tuesday is the day with more calorie intake and more sedentary minutes.  Saturday is the day with more steps and more MET. The day with more steps and more METs. However, these are not related.


## Solutions

Slides [presentation](https://docs.google.com/presentation/d/1RpI9FruQ30nTynJisbiWwfcVvknLacR8COnLISjaBTY/edit?usp=sharing) of project.

## Conclusions
### The Game Plan
**STORE AND MONITOR**: Daily steps, METs, sleeping and bedtime, heart rate each minute, and monthly BMI.

**CALCULATE**: Height, monthly BMI, health status based on heart rate, BMI, steps, and METs.  

**NOTIFY**: MET minutes for optimal cardiovascular health, calories deficit, and calories burned, the optimal time to go to bed, and abnormal heart rates.

### Let's investigate
- Why are Tuesdays the day with less activity and more calorie intake?
- Why are Saturday the days with more steps and MET minutes?
- Why not Sundays? Are users taking a break?


## Next Steps...
We recommend in the future to add the next features:
- Medication reminders
- Keep a record of mindful minutes
- Menstrual cycle tracker
- Notify if the user is developing:
  - Sleep apnea
  - Atrial fibrillation
  - Respiratory issues
  - Stress


## Backstage
Check codes in [here](https://github.com/JezSarai/Jez_Portfolio/blob/b358a955c7f4da837ec7e42bb1de142cd28e980c/Backstage.md)
