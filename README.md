# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# Aim:
## TO detect and remove the outliers in the given data set and save the final data.
# Algorithm:
# Step 1:
## Import the required packages(pandas,numpy,scipy)
# Step 2:
## Read the given csv file
# Step 3:
## Convert the file into a dataframe and get information of the data
# Step 4:
## Remove the non numerical data columns using drop() method.
# Step 5:
## Detect the outliers in the data set using z scores method.
# Step 6:
## Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
# Step 7:
## Check if the outliersare removed from data set using graphical methods.
# step 8:
## Save the final data set into the file

# Program:
## 1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
## Program executed by:Dharshini S
## Register number:212221220009
~~~
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
~~~
## (3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
~~~
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
~~~
## (4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
~~~
df3 = pd.read_csv("height_weight.csv/")
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
~~~
## (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
~~~
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
~~~
# Output:
# (1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
# Dataset:
## ![image](https://user-images.githubusercontent.com/113699377/228198948-b5ab9cc4-da68-4450-84ce-4ff46846d876.png)
# Dataset Head:
## ![image](https://user-images.githubusercontent.com/113699377/228199076-7eb42a0e-bb8c-4610-8875-23adefc80bdb.png)
# Dataset Info:
## ![image](https://user-images.githubusercontent.com/113699377/228199205-59ae884e-f861-47f4-a8f5-ab97060c5d72.png)

# Dataset Describe:
## ![image](https://user-images.githubusercontent.com/113699377/228199463-78d51967-da04-4c7c-b8ad-4bcac9ab6549.png)

# Null Values:
## ![image](https://user-images.githubusercontent.com/113699377/228199559-5b42224a-cf96-43b9-97c3-fb37e6c4e903.png)

# Dataset Shape:
## ![image](https://user-images.githubusercontent.com/113699377/228199668-8634584c-fbae-4771-9b2f-ee924f8d5a14.png)

# Box plot of price_per_sqft column with outliers:
## ![image](https://user-images.githubusercontent.com/113699377/228199876-a657603e-6f4d-4ac8-b29b-f97bdf068731.png)

# price_per_sqft - Dataset after removing outliers:
## ![image](https://user-images.githubusercontent.com/113699377/228200123-7fc57b81-0963-49bd-89ff-c76c02b7f55b.png)

# price_per_sqft - Shape of Dataset after removing outliers :
## ![image](https://user-images.githubusercontent.com/113699377/228200233-fe32a903-2a95-44bd-8e85-829f5d1a37b2.png)

# Box Plot of price_per_sqft column without outliers:
## ![image](https://user-images.githubusercontent.com/113699377/228200343-f2f1f2b9-73ad-4c87-b79d-ea36de83195d.png)

# (3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
# Dataset after removal of outlier using z score:
## ![image](https://user-images.githubusercontent.com/113699377/228200582-4f965f6c-17a3-4a50-b8b9-5348b82813a4.png)

# Shape of Dataset after removal of outlier using z score:
## ![image](https://user-images.githubusercontent.com/113699377/228200729-9036fc77-7af9-4974-a35e-f6b0a2877191.png)

# (4) For the data set height_weight.csv detect weight and height outliers using IQR method:
# Dataset:
## ![image](https://user-images.githubusercontent.com/113699377/228200972-d25d0bc3-5a95-4d8c-baec-ef1f92f9668f.png)

# Dataset Head:
## ![image](https://user-images.githubusercontent.com/113699377/228201096-009c7353-4509-4309-a9c4-ce2a7df3c429.png)

# Dataset Info:
## ![image](https://user-images.githubusercontent.com/113699377/228201185-9aee4e02-d7e7-4fac-9a65-e9016aaf8d54.png)

# Datset Describe:
## ![image](https://user-images.githubusercontent.com/113699377/228201277-b99dbb43-610a-4270-9676-0714b3fefab7.png)

# Null Values:
## ![image](https://user-images.githubusercontent.com/113699377/228201397-34ed6d28-47e5-47d6-b2cc-0166bc7ced5e.png)

# Dataset Shape:
## ![image](https://user-images.githubusercontent.com/113699377/228201523-1f7a1922-3069-4fb3-81fa-0ac8a585f777.png)

# Weight -With Outliners:
## ![image](https://user-images.githubusercontent.com/113699377/228201771-c4761bfa-737e-4624-aea8-0c555b62cb45.png)

# Weight - Dataset after removing Outliers using IQR method:
## ![image](https://user-images.githubusercontent.com/113699377/228201863-431143d4-2c27-4e42-98ce-5382fc4026b2.png)

# Weight - Shape of Dataset after removing Outliers using IQR method:
## ![image](https://user-images.githubusercontent.com/113699377/228201960-007d6acf-40f9-4280-8e86-58c972f6a242.png)

# Weight - Without Outliers using IQR method:
## ![image](https://user-images.githubusercontent.com/113699377/228202056-56453f19-c1d0-405c-891e-a142a16c5620.png)

# Height - With outliers:
## ![image](https://user-images.githubusercontent.com/113699377/228202159-a535ff03-291e-4130-91fa-2ce2641f2b5d.png)

# Height - Dataset after removing Outliers using IQR method:
## ![image](https://user-images.githubusercontent.com/113699377/228202373-99cddde2-9b60-42aa-b565-30997ae34e41.png)

# Height - Shape of Dataset after removing Outliers using IQR method:
## ![image](https://user-images.githubusercontent.com/113699377/228202505-5ab00620-efc9-411c-be99-954a032045ac.png)

# Height - Without Outliers using IQR method:
## ![image](https://user-images.githubusercontent.com/113699377/228202604-15e3edbf-2507-4a8e-af1d-1fca5eea33af.png)

# Result:
## Thus the outliers are detected and removed in the given file and the final data set is saved into the file.


