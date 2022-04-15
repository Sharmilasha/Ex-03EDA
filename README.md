# Ex-03EDA

## AIM
To perform EDA on the given data set. 

# Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and 
anomalies to direct specific testing of your hypothesis.
 

### ALGORITHM

### STEP 1

Import the required packages(pandas,numpy,seaborn).

### STEP 2

Read and Load the Dataset

### STEP 3

Remove the null values from the data and remove the outliers.

### STEP 4

Remove the non numerical data columns using drop() method.

### STEP 5:

returns object containing counts of unique values using (value_counts()).

### STEP 6:

Plot the counts in the form of Histogram or Bar Graph.

### STEP 7:

find the pairwise correlation of all columns in the dataframe(.corr()).

### STEP 8:

Save the final data set into the file.


### CODE
```
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df= pd.read_csv('titanic_dataset.csv')
df.head()
df.info()
df.isnull().sum()
df['Cabin']=df['Cabin'].fillna(df['Cabin'].mode()[0])
df['Age']=df['Age'].fillna(df['Age'].mean())
df['Embarked']=df['Embarked'].fillna(df['Embarked'].mode()[0])
df.isnull().sum()
df.boxplot()
cols = ['Age', 'Fare','SibSp','Parch','Fare']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
survived_count = df.groupby('Survived')['Survived'].count()
survived_count
plt.title('Grouped by survival')
sns.countplot(x="Survived",data=df)
df["Pclass"].value_counts()
plt.title('Grouped by pclass')
sns.countplot(x="Pclass",data=df)
df["Sex"].value_counts()
plt.title('Grouped by gender')
sns.countplot(x="Sex",data=df)
df["Embarked"].value_counts()
plt.title('Grouped by embarkation')
sns.countplot(x="Embarked",data=df)
sns.displot(df["Fare"])
plt.title('Survived female and male')
sns.countplot(x="Sex",hue="Survived",data=df)
sns.countplot(x="Pclass",hue="Survived",data=df)
sns.countplot(x="Sex",hue="Survived",data=df)
sns.displot(df[df["Survived"]==0]["Age"])
sns.displot(df[df["Survived"]==1]["Age"])
pd.crosstab(df["Pclass"],df["Survived"])
pd.crosstab(df["Sex"],df["Survived"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```
### OUPUT

![output](.//aa1.png)
![output](.//aa2.png)
![output](.//aa3.png)
![output](.//aa4.png)
![output](.//aa5.png)
![output](.//aa6.png)
![output](.//aa7.png)
![output](.//aa8.png)
![output](.//aa9.png)
![output](.//aa10.png)
![output](.//aa11.png)
![output](.//aa12.png)
![output](.//aa13.png)
![output](.//aa14.png)
![output](.//aa15.png)
