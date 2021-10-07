# Backstage
## Modifications to main table
### October 5th. 2021
- Added comments in Column name to understand what it means.
- Filtered to identify blanks (nulls). NO NULLS.
- Added a COUNTIF in Excel to count each sample with acertain age.
- Charted the results as Pie Chart and Histogram with ranges of 29-43, 43-57, 57-71, and 71-85.
- Added a COUNTIF in Excel to count the number of female and male study subjects. MALES ARE OVERREPRESENTED.
- Correlated in RStudio

### October 6th. 2021
- Correlated Sex to other variables in RStudio

## October 7th. 2021 (10/06/21)
Charted Histograms of each variable against age to check if Pearson 's Correlation was a good test to establish correlation.
Coded a multiple linear regression to [predict](https://github.com/JezSarai/Jez_Portfolio/blob/eeed74a44d29abc2c905a8dfc33d9bbe57e7f3a2/Heart%20Attack%20Possibitly_Prediction.md) a heart attack.


## Pearson's Correlations
**Age to Chest Pain Type**

```markdown
cor.test(heart$age, heart$cp, method=c("pearson", "kendall", "spearman"))
```

t = -1.1939, df = 301, p-value = 0.2335
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.17993910  0.04436824
sample estimates:
        cor 
-0.06865302 
NOT SIGNIFICANTLY CORRELATED

**Age to resting Blood Pressure**

```markdown
cor.test(heart$age, heart$trestbps, method=c("pearson", "kendall", "spearman"))
```

t = 5.0475, df = 301, p-value = 7.762e-07
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.1720897 0.3800657
sample estimates:
      cor 
0.2793509 
SIGNIFICANTLY CORRELATED

**Age to Serum Colesterol (mg/dl)**

```markdown
cor.test(heart$age, heart$chol, method=c("pearson", "kendall", "spearman"))
```

t = 3.7948, df = 301, p-value = 0.0001786
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.1034917 0.3186831
sample estimates:
     cor 
0.213678 
SIGNIFICANTLY CORRELATED

**Age to Fasting blood sugar (> 120 mg/dl)**

```markdown
cor.test(heart$age, heart$fbs, method=c("pearson", "kendall", "spearman"))
```

t = 2.1203, df = 301, p-value = 0.0348
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.008749197 0.230830534
sample estimates:
      cor 
0.1213076 
SIGNIFICANTLY CORRELATED

**Age to Resting electrocardiographic results (values 0,1,2)**

```markdown
cor.test(heart$age, heart$restecg, method=c("pearson", "kendall", "spearman"))
```

t = -2.0299, df = 301, p-value = 0.04324
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.225930511 -0.003579731
sample estimates:
       cor 
SIGNIFICANTLY CORRELATED

**Age to  Maximum Heart Rate Achieved**

```markdown
cor.test(heart$age, heart$thalach, method=c("pearson", "kendall", "spearman"))
```

t = -7.5386, df = 301, p-value = 5.628e-13
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.4892312 -0.2992831
sample estimates:
       cor 
-0.3985219 
SIGNIFICANTLY CORRELATED

**Age to  Exercise Induced Angina**

```markdown
cor.test(heart$age, heart$exang, method=c("pearson", "kendall", "spearman"))
```

t = 1.6874, df = 301, p-value = 0.09257
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.0160523  0.2072187
sample estimates:
       cor 
0.09680083 
SIGNIFICANTLY CORRELATED

**Age to Old peak(ST depression induced by exercise relative to rest)**

```markdown
cor.test(heart$age, heart$oldpeak, method=c("pearson", "kendall", "spearman"))
```

t = 3.7267, df = 301, p-value = 0.0002317
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.09969366 0.31523104
sample estimates:
      cor 
0.2100126 
SIGNIFICANTLY CORRELATED

**Age to Slope of the peak exercise ST segment**

```markdown
cor.test(heart$age, heart$slope, method=c("pearson", "kendall", "spearman"))
```

t = -2.9715, df = 301, p-value = 0.003203
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.27623778 -0.05722471
sample estimates:
       cor 
-0.1688142 
SIGNIFICANTLY CORRELATED

**Age to Thal (0 = normal; 1 = fixed defect; 2 = reversable defect)**

```markdown
cor.test(heart$age, heart$thal, method=c("pearson", "kendall", "spearman"))
```

t = 1.1825, df = 301, p-value = 0.2379
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.04502163  0.17930553
sample estimates:
       cor 
0.06800138 
SIGNIFICANTLY CORRELATED

**Age to Target (0= less chance of heart attack 1= more chance of heart attack)**

```markdown

cor.test(heart$age, heart$target, method=c("pearson", "kendall", "spearman"))
```

t = -4.0146, df = 301, p-value = 7.525e-05
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.3297407 -0.1156997
sample estimates:
       cor 
-0.2254387 
SIGNIFICANTLY CORRELATED

**Sex to Chest Pain Type**
```markdown
cor.test(heart$sex, heart$cp, method=c("pearson", "kendall", "spearman"))
```

t = -0.85729, df = 301, p-value = 0.392
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.16113485  0.06367929
sample estimates:
        cor 
-0.04935288 
NOT SIGNIFICANTLY CORRELATED

**Sex to Resting Blood Pressure**
```markdown
cor.test(heart$sex, heart$trestbps, method=c("pearson", "kendall", "spearman"))
```

t = -0.98649, df = 301, p-value = 0.3247
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.16836987  0.05626915
sample estimates:
        cor 
-0.05676882 
NOT SIGNIFICANTLY CORRELATED

**Sex to Serum Cholesterol in mg/dl**
```markdown
cor.test(heart$sex, heart$chol, method=c("pearson", "kendall", "spearman"))
```

t = -3.5029, df = 301, p-value = 0.00053
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.30381503 -0.08717824
sample estimates:
       cor 
-0.1979122 
SIGNIFICANTLY CORRELATED

**Sex to Fasting blood sugar > 120 mg/dl**
```markdown
cor.test(heart$sex, heart$fbs, method=c("pearson", "kendall", "spearman"))
```

t = 0.78207, df = 301, p-value = 0.4348
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.06799125  0.15691364
sample estimates:
       cor 
0.04503179 
NOT SIGNIFICANTLY CORRELATED

**Sex to Resting Electrocardiographic Results (values 0,1,2)**
```markdown
cor.test(heart$sex, heart$restecg, method=c("pearson", "kendall", "spearman"))
```

t = -1.0114, df = 301, p-value = 0.3126
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.16976111  0.05484139
sample estimates:
        cor 
-0.05819627 
NOT SIGNIFICANTLY CORRELATED

**Sex to Maximum heart rate achieved**
```markdown
cor.test(heart$sex, heart$thalach, method=c("pearson", "kendall", "spearman"))
```

t = -0.76446, df = 301, p-value = 0.4452
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.15592455  0.06900038
sample estimates:
        cor 
-0.04401991 
NOT SIGNIFICANTLY CORRELATED

**Sex to Exercise induced angina**
```markdown
cor.test(heart$sex, heart$exang, method=c("pearson", "kendall", "spearman"))
```

t = 2.4828, df = 301, p-value = 0.01358
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.02945596 0.25034573
sample estimates:
      cor 
0.1416638 
SIGNIFICANTLY CORRELATED

**Sex to Oldpeak (ST depression induced by exercise relative to rest)**
```markdown
cor.test(heart$sex, heart$oldpeak, method=c("pearson", "kendall", "spearman"))
```

t = 1.6749, df = 301, p-value = 0.09499
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.01676671  0.20653465
sample estimates:
       cor 
0.09609288 
SIGNIFICANTLY CORRELATED

**Sex to Slope of the peak exercise ST segment**
```markdown
cor.test(heart$sex, heart$slope, method=c("pearson", "kendall", "spearman"))
```

t = -0.53306, df = 301, p-value = 0.5944
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.1428941  0.0822521
sample estimates:
        cor 
-0.03071057 
NOT SIGNIFICANTLY CORRELATED

**Sex to Number of major vessels (0-3) colored by flourosopy**
```markdown
cor.test(heart$sex, heart$ca, method=c("pearson", "kendall", "spearman"))
```

t = 2.0663, df = 301, p-value = 0.03966
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.005658778 0.227902547
sample estimates:
      cor 
0.1182614 
SIGNIFICANTLY CORRELATED

**Sex to Thal (0 = normal; 1 = fixed defect; 2 = reversable defect)**
```markdown
cor.test(heart$sex, heart$thal, method=c("pearson", "kendall", "spearman"))
```

t = 3.7272, df = 301, p-value = 0.0002312
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.09972321 0.31525792
sample estimates:
      cor 
0.2100411 
SIGNIFICANTLY CORRELATED

**Sex to Target (0= less chance of heart attack 1= more chance of heart attack)**
```markdown
cor.test(heart$sex, heart$target, method=c("pearson", "kendall", "spearman"))
```

t = -5.0786, df = 301, p-value = 6.679e-07
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.3815369 -0.1737589
sample estimates:
       cor 
-0.2809366 
SIGNIFICANTLY CORRELATED
