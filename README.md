# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```py
import pandas as pd
df = pd.read_csv('SAMPLEIDS.csv')
print(df)
```

<img width="785" height="896" alt="image" src="https://github.com/user-attachments/assets/49fb8a31-3eef-4dad-8616-6870b8c617ee" />

```py
df['GENDER'].value_counts()
```

<img width="186" height="167" alt="image" src="https://github.com/user-attachments/assets/c658a3f3-bbd9-4a35-b781-cf6dfbdab743" />

```py
x1 = df.dropna(how='any')
print(x1)
```
<img width="776" height="573" alt="image" src="https://github.com/user-attachments/assets/c370e7c8-6783-4fb1-a1c7-0e5defb451ed" />

```py
res = df.dropna(subset=['M1','M2','M3','M4'],how='any')
print(res)
```
<img width="696" height="582" alt="image" src="https://github.com/user-attachments/assets/d0e97042-02ff-400b-bdf8-e33ed01316f6" />


```py
df=pd.read_csv('heights.csv')
print(df)
```
<img width="200" height="304" alt="image" src="https://github.com/user-attachments/assets/045c8233-c6f9-4f10-b0c6-7e1773d6f719" />

```py
import seaborn as sns
import matplotlib.pyplot as plt

sns.boxplot(data=df)
plt.show()
```
<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/8293ac06-bbf8-42ec-ae86-b2dc2f28c672" />

```py
sns.scatterplot(data=df)
```
<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/8a4be5f4-b219-4b0d-80b5-8f2a3f273ab4" />

```py
q3 = df["height"].quantile(0.75)
q1 = df["height"].quantile(0.25)
iqr = q3 - q1
print(iqr)
```
<img width="192" height="28" alt="image" src="https://github.com/user-attachments/assets/7c3c8440-09b7-4bdd-9e78-d25c4867d749" />

```py
q1, q3 = df["height"].quantile([0.25, 0.75])
iqr = q3 - q1
lb, ub = q1 - 1.5*iqr, q3 + 1.5*iqr
outliers = df[(df["height"] < lb) | (df["height"] > ub)]

print(f"Lower bound: {lb}\nUpper bound: {ub}\nOutliers:\n{outliers}")
```
<img width="297" height="129" alt="image" src="https://github.com/user-attachments/assets/165bf9ab-9b68-482e-be42-58bdfdc3d985" />

```py
import numpy as np
from scipy import stats

z = np.abs(stats.zscore(df["height"]))
z = pd.Series(z, name="height")   # make it a Series with name
print(z)
```
<img width="283" height="301" alt="image" src="https://github.com/user-attachments/assets/e5f3e9d9-ea9f-4ff5-99c6-b954a7853423" />

```py
df1 = df[z<3]
print(df1)
```
<img width="224" height="291" alt="image" src="https://github.com/user-attachments/assets/472d07c1-b603-42a5-931e-ce67c542e31a" />


```py
import pandas as pd
df = pd.read_csv("Data_set.csv")
print(df)
```
<img width="760" height="789" alt="image" src="https://github.com/user-attachments/assets/fbefde4b-895d-48fb-92ca-d418b7714f02" />

```py
df.describe()
```
<img width="872" height="328" alt="image" src="https://github.com/user-attachments/assets/0ef25d36-ba84-4b70-be77-631ff4ab920e" />

```py
df.info()
```
<img width="496" height="335" alt="image" src="https://github.com/user-attachments/assets/f468da99-3220-4f25-a36f-ea127d52cc44" />

```py
df.head()
```
<img width="1347" height="233" alt="image" src="https://github.com/user-attachments/assets/31e4da2c-727c-4bfa-b43b-8066c19c11e2" />

```py
df.tail()
```
<img width="1328" height="218" alt="image" src="https://github.com/user-attachments/assets/2427b3f8-292f-4642-bbc9-5537035c7aea" />

```py
df.isnull()
```
<img width="1151" height="457" alt="image" src="https://github.com/user-attachments/assets/dbba61e2-120c-4c86-b832-b6ecb5ff5e2b" />

```py
df.notnull()
```
<img width="1151" height="465" alt="image" src="https://github.com/user-attachments/assets/976f5188-6394-46f9-9174-69c1f98aa1a5" />

```py
df.shape
```
<img width="73" height="25" alt="image" src="https://github.com/user-attachments/assets/2801d486-f844-4af2-a40c-0d258aede7b7" />

```py
df[df['rating'] > 8]
```
<img width="1385" height="460" alt="image" src="https://github.com/user-attachments/assets/585b1734-818f-4ecc-b4ad-e676a2bd2e31" />

```py
df[df['num_episodes'] > 20]
```
<img width="1599" height="578" alt="image" src="https://github.com/user-attachments/assets/a252f387-5f64-43be-8fa2-db8308b80378" />

```py
df.iloc[2:5 , :-3]
```
<img width="849" height="159" alt="image" src="https://github.com/user-attachments/assets/d9897763-a92b-4313-8ac1-6d42d9f0c234" />

```py
df.iloc[[6,7,8],[1,2,3]]
```
<img width="431" height="155" alt="image" src="https://github.com/user-attachments/assets/68935232-ea24-4e51-b57e-72b13e7b34c6" />

```py
df.loc[3:5 , ['country' , 'num_episodes']]
```
<img width="264" height="154" alt="image" src="https://github.com/user-attachments/assets/34d982fa-6830-47ac-a672-f9f263ded579" />

```py
df['country'].value_counts()
```
<img width="195" height="209" alt="image" src="https://github.com/user-attachments/assets/d8ebfc72-23b4-4e6f-b1c7-ce6f5004a351" />

```py
df.count()
```
<img width="271" height="391" alt="image" src="https://github.com/user-attachments/assets/5d52e3b4-4a37-4c0a-9995-bcd727c385c0" />

```py
df.dropna(axis = 1)
```
<img width="499" height="458" alt="image" src="https://github.com/user-attachments/assets/1629b6b4-b2c6-4fdd-ba29-5be9207edea5" />

```py
df.fillna(0)
```
<img width="1363" height="468" alt="image" src="https://github.com/user-attachments/assets/1bae0d54-d1be-4e34-a847-11ff31f1b3d1" />
```py
df.fillna(method = 'bfill')
```
<img width="1367" height="458" alt="image" src="https://github.com/user-attachments/assets/0a454443-2184-4e9c-9642-a5f11f9e5544" />

```py
df.interpolate()
```
<img width="1378" height="464" alt="image" src="https://github.com/user-attachments/assets/a94aabcc-b341-4da6-9f5f-615cd66163f3" />

```py
ffil = df.fillna(method = 'ffill')
print(ffil)
```
<img width="707" height="795" alt="image" src="https://github.com/user-attachments/assets/bb5344d4-f423-4aa2-b764-982edc365a4c" />

```py
bfil = df.fillna(method = 'bfill')
print(bfil)
```
<img width="700" height="780" alt="image" src="https://github.com/user-attachments/assets/e6bc2abf-c999-4b95-834c-f5be67ad1309" />

```py
m = df.num_episodes.mean()
print(m)
```
<img width="53" height="34" alt="image" src="https://github.com/user-attachments/assets/a46b441d-e679-4720-8388-65d91d5915b2" />

```py
m = df.fillna(df['num_episodes'].mean())
print(m)
```
<img width="702" height="802" alt="image" src="https://github.com/user-attachments/assets/696c2444-7a06-4550-bebb-65465d8a88ac" />

```py
fmean = df['lifetime_popularity_rank'].fillna(value=df['lifetime_popularity_rank'].mean())
print(fmean)
```
<img width="512" height="246" alt="image" src="https://github.com/user-attachments/assets/d2f3fcf4-c43c-4a64-912d-94f5684b663b" />


# Result

Thus, we have read the given data and performed data cleaning and saved the cleaned data to a file successfully.

# Summary
By displaying the dataset it helps to analyse data
Outliers are found using by using IQR and Z Score methods
Also NULL values can be tackled by fill it with ffill ,mean,median and various methods. Choice of the method depends on the dataset
By cleaning the data in efficient way we can clearly understand about the dataset.
