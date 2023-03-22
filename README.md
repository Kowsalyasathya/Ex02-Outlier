# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
## Aim:
To detect and remove the outliers in the given data set and save the final data.
## Algorithm:
## Step 1

Import the required packages(pandas,numpy,scipy)
## Step 2

Read the given csv file
## Step 3

Convert the file into a dataframe and get information of the data.
## Step 4

Remove the non numerical data columns using drop() method.
## Step 5

Detect the outliers in the data set using z scores method.
## Step 6

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
## Step 7

Check if the outliersare removed from data set using graphical methods.
## Step 8

Save the final data set into the file.

## Program:

## 1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

Program developed by : Kowsalya M

Register number : 212222230069

import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/bhp.csv")

df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]

df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)

## (3)Examine price_per_sqft column and use zscore of 3 to remove outliers.

from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)


## (4)(i) For the data set height_weight.csv detect weight outliers using IQR method.

df3 = pd.read_csv("height_weight.csv")

df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25)

q3 = df3['weight'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))]

df4

df4.shape

sns.boxplot(x="weight",data=df4)

## (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.

sns.boxplot(x="height",data=df3)

q1 = df3['height'].quantile(0.25)

q3 = df3['height'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))]

df5

df5.shape

sns.boxplot(x="height",data=df5)

## Output:

![ass1 1](https://user-images.githubusercontent.com/118671457/227022839-fa1a02a6-86ea-4860-95fa-5cf73898c103.png)

![ass2](https://user-images.githubusercontent.com/118671457/227022920-a7e4c0cc-6902-49a8-bf05-9253c7059751.png)

![ass3](https://user-images.githubusercontent.com/118671457/227023455-fba44eb0-9ab3-4850-9d33-891f3f39381d.png)

![ass4](https://user-images.githubusercontent.com/118671457/227023039-c6c62365-13b4-402f-8fdc-34cde2ffc468.png)

![ass5](https://user-images.githubusercontent.com/118671457/227023541-d5176c85-3283-4189-b639-8c7508958166.png)

![ass6](https://user-images.githubusercontent.com/118671457/227023676-28352463-11e4-40ac-bf37-315372c96b19.png)

![ass7](https://user-images.githubusercontent.com/118671457/227023717-b6d3922a-daea-400b-b4a2-1703a9c1eb91.png)

![ass8](https://user-images.githubusercontent.com/118671457/227024015-1de25e56-d56f-47cf-b233-a318f57599f9.png)

![ass9](https://user-images.githubusercontent.com/118671457/227024077-0685f7ef-936c-44a1-9fd8-30f8fca17bc1.png)

![ass10](https://user-images.githubusercontent.com/118671457/227024130-81190b29-8d20-4527-b7b6-21eb471cf832.png)

![ass11](https://user-images.githubusercontent.com/118671457/227024225-824cf016-c496-4f9a-845c-279e04a521ce.png)

## Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.


