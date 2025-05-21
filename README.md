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
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/18dd7b78-e77e-42a2-b10d-100d416258be)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/de697e13-1672-43e7-97b6-e91b7ca48254)

```
df.isnull().any()<br>
```
![image](https://github.com/user-attachments/assets/2ea2b4b2-ad93-4196-af0c-74f2757ed4bb)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/d1ccfeeb-ce5b-4274-ae08-b15a5dff8acf)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/2f054b82-3469-4c84-8477-9609ef35f871)

```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/146279ff-0acc-4ef1-bce7-dd2b04469719)

```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/7b3f8688-66cf-41da-b64c-0292ff2654e2)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/55154611-cacb-42e6-a50f-9c4ad981ba07)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/afbd30f6-f931-4d5a-a836-d03228e4fcc8)

```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/806d113c-8a66-4f89-9952-90cd21c3477c)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/885ab6ed-8880-4ffb-8328-0aa0de8e483d)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/d46c4b97-70cd-451e-945f-1cfcc4e4fa0d)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```
![image](https://github.com/user-attachments/assets/f40bdb15-690a-4910-a858-56aa3491eb2d)

```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/c0c0be80-2585-43a1-833f-95c582bd015e)

```
 delid=ir[~((ir.sepal_width<(q1-1.5iq))|(ir.sepal_width>(q3+1.5iq)))] delid
```
![image](https://github.com/user-attachments/assets/f732124f-8c61-402d-aad1-02639e992923)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/63a980f7-d93a-4fc0-8cd6-a3996b754829)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats


dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/93df8017-c780-49b4-a543-740586d797d7)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
``

iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/da734777-3c5d-4551-86ce-62b1042689c3)

```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/f1968b3f-1808-4eeb-ac6d-11e6696e17f2)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/f2856cdb-ca8b-4173-9c08-3e60ccfceb78)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![419089910-378d4ceb-f673-42fd-a4a0-0fc4c510cd7e](https://github.com/user-attachments/assets/1b883ca9-8c97-4664-8b5c-b7c3acf78691)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/57a3315e-fc8d-410e-a7c7-8b207edf5570)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/7dd352c0-a73a-40cf-9310-f01fb1edcb81)

# Result
Hence the data was cleaned , outliers were detected and removed.
