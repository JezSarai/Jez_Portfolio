# Backstage

Here you will find what I did in Excel, SQL and Rstudio to analyze the data

## CASE to categorize users' weight using the BMI
```markdown
SELECT
CASE
	WHEN BMI<=18.5 THEN 'Underweight'
	WHEN BMI<=24.9 THEN 'Healthy'
	WHEN BMI<=29.9 THEN 'Overweight'
	ELSE 'Obese'
END AS WeightStatus
FROM [Bellabeat].[dbo].[weightLogInfo_merged]

```

## CASE AND DATEPART to identify the weekday of a given date
```markdown
SELECT *,
 CASE WHEN DATEPART(dw,ActivityMinute) = 2 THEN 'Monday' 
   WHEN DATEPART(dw,ActivityMinute) = 3 THEN 'Tuesday'
   WHEN DATEPART(dw,ActivityMinute) = 4 THEN 'Wednesday' 
   WHEN DATEPART(dw,ActivityMinute) = 5 THEN 'Thursday'
   WHEN DATEPART(dw,ActivityMinute) = 6 THEN 'Friday'
   WHEN DATEPART(dw,ActivityMinute) = 7 THEN 'Saturday' 
ELSE 'Sunday'
END AS Weekday
FROM minuteMETsNarrow_merged
```

## DECLARE TABLE, DATEPART and CONCAT for Date and Time
```markdown
DECLARE @Table TABLE (Id bigint, ActivityMinute DATETIME, METs INT, TimeHour VARCHAR(10), Weekday VARCHAR(10), DayTime VARCHAR(20))

INSERT INTO @Table(Id, ActivityMinute, METs, Weekday, TimeHour)
SELECT Id, ActivityMinute, METs,
CASE WHEN DATEPART(dw,ActivityMinute) = 2 THEN 'Monday' 
  WHEN DATEPART(dw,ActivityMinute) = 3 THEN 'Tuesday'
  WHEN DATEPART(dw,ActivityMinute) = 4 THEN 'Wednesday' 
  WHEN DATEPART(dw,ActivityMinute) = 5 THEN 'Thursday'
  WHEN DATEPART(dw,ActivityMinute) = 6 THEN 'Friday'
  WHEN DATEPART(dw,ActivityMinute) = 7 THEN 'Saturday' 
ELSE 'Sunday' END,
dbo.ReturnHour(DATEPART(hh,ActivityMinute))
FROM minuteMETsNarrow_merged

UPDATE @Table
SET DayTime=CONCAT(Weekday,' ',TimeHour)
SELECT * FROM @Table
```
At the end I didn't use this query but it was my first aproach to declare a table and concatenate in SQL.

## Another DECLARE TABLE and DATEPART
```markdown
DECLARE @Table TABLE (Id bigint, ActivityDate DATETIME, TotalSteps INT, TotalDistance DECIMAL(18,10), TrackerDistance DECIMAL(18,10), LoggedActivitiesDistance DECIMAL(18,10), VeryActiveDistance DECIMAL(18,10), ModeratelyActiveDistance DECIMAL(18,10), LightActiveDistance DECIMAL(18,10), SedentaryActiveDistance DECIMAL(18,10), VeryActiveMinutes INT, FairlyActiveMinutes INT, LightlyActiveMinutes INT, SedentaryMinutes INT, Calories INT, Weekday VARCHAR(10))

INSERT INTO @Table(Id, ActivityDate, TotalSteps, TotalDistance, TrackerDistance, LoggedActivitiesDistance, VeryActiveDistance, ModeratelyActiveDistance, LightActiveDistance, SedentaryActiveDistance, VeryActiveMinutes, FairlyActiveMinutes, LightlyActiveMinutes, SedentaryMinutes, Calories, Weekday)
SELECT Id, ActivityDate, TotalSteps, TotalDistance, TrackerDistance, LoggedActivitiesDistance, VeryActiveDistance, ModeratelyActiveDistance, LightActiveDistance, SedentaryActiveDistance, VeryActiveMinutes, FairlyActiveMinutes, LightlyActiveMinutes, SedentaryMinutes, Calories,
CASE WHEN DATEPART(dw,ActivityDate) = 2 THEN 'Monday' 
  WHEN DATEPART(dw,ActivityDate) = 3 THEN 'Tuesday'
  WHEN DATEPART(dw,ActivityDate) = 4 THEN 'Wednesday' 
  WHEN DATEPART(dw,ActivityDate) = 5 THEN 'Thursday'
  WHEN DATEPART(dw,ActivityDate) = 6 THEN 'Friday'
  WHEN DATEPART(dw,ActivityDate) = 7 THEN 'Saturday' 
ELSE 'Sunday' END
FROM dailyActivity_merged

SELECT * FROM @Table
```

## Daily Calories
```markdown
DECLARE @Table TABLE (Id bigint, ActivityDay DATETIME, Calories INT, Weekday VARCHAR(10))

INSERT INTO @Table(Id, ActivityDay, Calories, Weekday)
SELECT Id, ActivityDay, Calories,
CASE WHEN DATEPART(dw,ActivityDay) = 2 THEN 'Monday' 
  WHEN DATEPART(dw,ActivityDay) = 3 THEN 'Tuesday'
  WHEN DATEPART(dw,ActivityDay) = 4 THEN 'Wednesday' 
  WHEN DATEPART(dw,ActivityDay) = 5 THEN 'Thursday'
  WHEN DATEPART(dw,ActivityDay) = 6 THEN 'Friday'
  WHEN DATEPART(dw,ActivityDay) = 7 THEN 'Saturday' 
ELSE 'Sunday' END
FROM dailyCalories_merged

SELECT * FROM @Table
```

## Daily Steps
```markdown
DECLARE @Table TABLE (Id bigint, ActivityDay DATETIME, StepTotal INT, Weekday VARCHAR(10))

INSERT INTO @Table(Id, ActivityDay, StepTotal, Weekday)
SELECT Id, ActivityDay, StepTotal,
CASE WHEN DATEPART(dw,ActivityDay) = 2 THEN 'Monday' 
  WHEN DATEPART(dw,ActivityDay) = 3 THEN 'Tuesday'
  WHEN DATEPART(dw,ActivityDay) = 4 THEN 'Wednesday' 
  WHEN DATEPART(dw,ActivityDay) = 5 THEN 'Thursday'
  WHEN DATEPART(dw,ActivityDay) = 6 THEN 'Friday'
  WHEN DATEPART(dw,ActivityDay) = 7 THEN 'Saturday' 
ELSE 'Sunday' END
FROM dailySteps_merged

SELECT * FROM @Table
```

## Daily intensities
```markdown
DECLARE @Table TABLE (Id bigint, ActivityDay DATETIME, SedentaryMinutes INT, LightlyActiveMinutes INT, FairlyActiveMinutes INT, VeryActiveMinutes INT, SedentaryActiveDistance DECIMAL(18,10), LightActiveDistance DECIMAL(18,10), ModeratelyActiveDistance DECIMAL(18,10), VeryActiveDistance DECIMAL(18,10), Weekday VARCHAR(10))

INSERT INTO @Table(Id, ActivityDay, SedentaryMinutes, LightlyActiveMinutes, FairlyActiveMinutes, VeryActiveMinutes, SedentaryActiveDistance, LightActiveDistance, ModeratelyActiveDistance, VeryActiveDistance, Weekday)
SELECT Id, ActivityDay, SedentaryMinutes, LightlyActiveMinutes, FairlyActiveMinutes, VeryActiveMinutes, SedentaryActiveDistance, LightActiveDistance, ModeratelyActiveDistance, VeryActiveDistance,
CASE WHEN DATEPART(dw,ActivityDay) = 2 THEN 'Monday' 
  WHEN DATEPART(dw,ActivityDay) = 3 THEN 'Tuesday'
  WHEN DATEPART(dw,ActivityDay) = 4 THEN 'Wednesday' 
  WHEN DATEPART(dw,ActivityDay) = 5 THEN 'Thursday'
  WHEN DATEPART(dw,ActivityDay) = 6 THEN 'Friday'
  WHEN DATEPART(dw,ActivityDay) = 7 THEN 'Saturday' 
ELSE 'Sunday' END
FROM dailyIntensities_merged

SELECT * FROM @Table
```

## To check if calories in Daily Activity are the same as the ones in Daily Calories
```markdown
SELECT dam.Id, dcm.id, dam.ActivityDate, dam.Calories, dcm.ActivityDay, dcm.Calories
FROM dailyActivity_merged dam
INNER JOIN dailyCalories_merged dcm
ON dam.Id = dcm.Id AND dam.ActivityDate = dcm.ActivityDay
```

## Renaming
```markdown
SELECT DATA_TYPE 
FROM INFORMATION_SCHEMA.COLUMNS
WHERE 
     TABLE_NAME = 'yourTableName' AND 
     COLUMN_NAME = 'yourColumnName'
```

## Another DATEPART
```markdown
DECLARE @Table TABLE (Id bigint, HrtRate INT, DHMS datetime, TimeHr varchar(10), TimeMin varchar(10), HrMin VARCHAR(10))

INSERT INTO @Table(Id, HrtRate, DHMS, TimeHr, TimeMin)
SELECT TOP (10) Id, HrtRate, DHMS, 
DATEPART(hh,DHMS) AS TimeHr,
DATEPART(mm,DHMS) AS TimeMin
FROM HeartRate_Secs


UPDATE @Table
SET HrMin = CONCAT(TimeHr,':',TimeMin) FROM @Table
SELECT * FROM @Table
```

## DATEADD to get the average heartrate each minute instead of second
```markdown
SELECT Id, DATEADD(mi,DATEDIFF(mi,0,[Time]),0) AS [Time], AVG([Value]) AS AvgValue
FROM heartrate_seconds_merged

GROUP BY Id, DATEADD(mi,DATEDIFF(mi,0,[Time]),0)
ORDER BY Id DESC
```

## INNER JOIN of calories and sedentary minutes
```markdown
SELECT cast(dailyCalories_merged.ActivityDay as date) as ActivityDay, dailyCalories_merged.Calories, dailyIntensities_merged.SedentaryMinutes
FROM dailyCalories_merged
JOIN dailyIntensities_merged ON dailyCalories_merged.ActivityDay = dailyIntensities_merged.ActivityDay
```

## INNER JOIN of steps and METs
```markdown
SELECT dailySteps_NoDuplicates.ActivityDay, dailySteps_NoDuplicates.StepTotal, minuteMETsNarrow_merged.METs
FROM dailySteps_NoDuplicates
JOIN minuteMETsNarrow_merged ON minuteMETsNarrow_merged.ActivityMinute = dailySteps_NoDuplicates.ActivityDay
```

## CORRELATION of calories and sedentary minutes
```markdown
read.csv("~/Google Data Analytics/CaloriesSedentary2.csv", header = TRUE, sep = ",")

CalSedCorr = read.csv("~/Google Data Analytics/CaloriesSedentary2.csv", header = TRUE, sep = ",")

ggscatter(CalSedCorr, x = "Calories", y = "SedentaryMinutes", 
          add = "reg.line", conf.int = TRUE, 
          cor.coef = TRUE, cor.method = "pearson",
          xlab = "Calories", ylab = "Sedentary Minutes")


cor.test(CalSedCorr$Calories, CalSedCorr$SedentaryMinutes, method=c("pearson", "kendall", "spearman"))
```

## CORRELATION of steps and METs
```markdown
read.csv("~/Google Data Analytics/StepsMets.csv", header = TRUE, sep = ",")
SteMetCorr = read.csv("~/Google Data Analytics/StepsMets.csv", header = TRUE, sep = ",")

ggscatter(SteMetCorr, x = "StepTotal", y = "METs", 
          add = "reg.line", conf.int = TRUE, 
          cor.coef = TRUE, cor.method = "pearson",
          xlab = "Steps", ylab = "METs")


cor.test(SteMetCorr$StepsTotal, SteMetCorr$METs, method=c("pearson", "kendall", "spearman"))
```


