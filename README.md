# EXNO2DS
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

# CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("titanic_dataset.csv")
df
```
![image](https://github.com/user-attachments/assets/3c66ec6d-134a-4e0d-a94b-eb9dea4f43b2)
```
df.info()
```
![image](https://github.com/user-attachments/assets/fb4cf6f4-c35a-4b62-b2c1-9104f4202c05)
```
df.shape
```
![image](https://github.com/user-attachments/assets/9a9e5874-ad91-414b-881e-b8d07f139590)
```
df.set_index("PassengerId",inplace=True)
df.nunique()
```
![image](https://github.com/user-attachments/assets/1bb2d857-04ae-4eb8-a0f1-8ed24716d040)

```
df["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/e2543846-bd5a-40b5-b784-ad5689f40296)
```
per = (df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/user-attachments/assets/85a175e1-d224-4255-913b-5911f12c0568)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/e2293b35-61d9-416f-9ced-96e5bfadbfe5)
```
sns.countplot(data=df,x="Survived")
```
![image](https://github.com/user-attachments/assets/6bbdf269-7ce1-4fdf-a904-00dc5b4c43a8)
```
df.Pclass.unique()
```
![image](https://github.com/user-attachments/assets/644f2a7a-d19c-4642-a34b-cd038203b1ef)
```
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```
![image](https://github.com/user-attachments/assets/fdf41756-2cc6-48cf-a58d-afc519068b07)
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![image](https://github.com/user-attachments/assets/d393e3c2-0c25-4e39-a5a2-578da857059f)
```
sns.catplot(x='Survived',hue="Gender",data=df,kind="count")
```
![image](https://github.com/user-attachments/assets/c4efbc88-19f2-44e8-8e11-d6f44c42d67c)
```
df.boxplot(column="Age",by="Survived")
```
![image](https://github.com/user-attachments/assets/9049e7e7-0fe3-4bc7-927d-321dfb43a683)
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![image](https://github.com/user-attachments/assets/583e8977-68e4-496f-9baa-edc3cc0eff55)
```
sns.jointplot(x="Age",y="Fare",data=df)
```
![image](https://github.com/user-attachments/assets/a6b61a4c-a5f9-4bdb-92ec-b72efc07fb2e)
```
fig,ax1 = plt.subplots(figsize=(8,5))
pt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
```
![image](https://github.com/user-attachments/assets/82814afe-4561-4839-8398-f6d8f7e88271)
```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/user-attachments/assets/2a77e6cd-cf3e-4db2-bf6e-a3fc6c30e44a)
```
numeric_dt = df.select_dtypes(include=['number'])
corr = numeric_dt.corr()
sns.heatmap(corr,annot=True)
```
![Screenshot 2024-09-03 100630](https://github.com/user-attachments/assets/902bcf8f-2a1b-4b8d-b6ad-42ce366b454a)

```
sns.pairplot(df)
```
![Screenshot 2024-09-01 113054](https://github.com/user-attachments/assets/e2cc50ce-51fe-447d-82cf-30043bbb9fd5)
![Screenshot 2024-09-01 113147](https://github.com/user-attachments/assets/c0770c1a-2d92-481e-b5d3-7b5dd3204115)

# RESULT
Thus the data analysis has been implemented succesfully.
