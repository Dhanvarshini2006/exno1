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

# Coding and Output:

```
import pandas as pd
df=pd.read_csv("/iris.csv")
df
```
<img width="739" height="510" alt="image" src="https://github.com/user-attachments/assets/ac310d39-2f88-4ac2-9278-eb27a4df8e0a" />

```
df.head()
```
<img width="641" height="260" alt="image" src="https://github.com/user-attachments/assets/373b4b35-f756-4096-a2b8-5ccb67fb11a1" />

```
df.tail()
```
<img width="642" height="247" alt="image" src="https://github.com/user-attachments/assets/67c84913-c3c6-42dd-b1b0-3783d7564c37" />

```
df.isnull()
```
<img width="655" height="478" alt="image" src="https://github.com/user-attachments/assets/10ea1caf-2a7a-445d-99c5-abe0a25ee94d" />

```
df.dropna(axis=0)
```
<img width="651" height="472" alt="image" src="https://github.com/user-attachments/assets/a172c194-9b07-4f8e-a9aa-4020b578f759" />

```
df.dropna(axis=1)
```
<img width="651" height="462" alt="image" src="https://github.com/user-attachments/assets/aec88c3d-ed3f-447a-98d3-eadb08151ab2" />

```
df.fillna(0)
```
<img width="664" height="491" alt="image" src="https://github.com/user-attachments/assets/2057a97c-e2ac-4215-973a-468a7b874d69" />

```
df_dropped=df.dropna()
df_dropped
```
<img width="656" height="483" alt="image" src="https://github.com/user-attachments/assets/c552919d-037b-4249-ae62-a67195288ece" />

```
import seaborn as sns
suren=pd.read_csv("/iris.csv")
df
```
<img width="652" height="479" alt="image" src="https://github.com/user-attachments/assets/b3a6e653-48a4-4058-a8d6-6fc35868e7ac" />

```
df.describe()
```
<img width="589" height="378" alt="image" src="https://github.com/user-attachments/assets/767bbc6a-bb45-42f4-a1d5-430e161482e6" />

```
sns.boxplot(x='sepal_width',data=df)

```
<img width="695" height="570" alt="image" src="https://github.com/user-attachments/assets/aeed1f59-8218-4048-9d56-4500651ffee4" />

```
q1=df.sepal_width.quantile(0.25)
q3=df.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="169" height="46" alt="image" src="https://github.com/user-attachments/assets/01e7745b-bc3e-4623-92b6-83a952530e4e" />

```
rid=df[((df.sepal_width<(q1-1.5*iqr))|(df.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="174" height="266" alt="image" src="https://github.com/user-attachments/assets/01692d86-7874-414e-9b32-91127c063eeb" />

```
delid=df[~((df.sepal_width<(q1-1.5*iqr))|(df.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="649" height="490" alt="image" src="https://github.com/user-attachments/assets/06ed7b5c-c68f-47a4-af5d-abd080703a21" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="668" height="566" alt="image" src="https://github.com/user-attachments/assets/374b66f8-8e8b-42ac-b5a2-23dcf63e6c14" />

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("/heights.csv")
dataset
```
<img width="203" height="606" alt="image" src="https://github.com/user-attachments/assets/e4fb2310-5e9a-4159-8a1a-9987f15c5f26" />

```
df=pd.read_csv("/heights.csv")
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)
```
```
iqr=q3-q1
iqr
```
<img width="303" height="24" alt="image" src="https://github.com/user-attachments/assets/9c096cac-55ca-45ee-967b-00955677b847" />

```
low=q1-1.5*iqr
low
```
<img width="301" height="51" alt="image" src="https://github.com/user-attachments/assets/c0594572-9cc4-4412-961a-b5ee0fd260ee" />

```
high=q3+1.5*iqr
high
```
<img width="189" height="41" alt="image" src="https://github.com/user-attachments/assets/b6b32d54-cea3-4dfb-b7b0-26723d97fb46" />

```
z=np.abs(stats.zscore(suren['sepal_length']))
z
```
<img width="660" height="666" alt="image" src="https://github.com/user-attachments/assets/a021e646-f697-426a-ae50-cd421ec1a1af" />

```
suren1=suren[z<3]
suren1
```
<img width="660" height="504" alt="image" src="https://github.com/user-attachments/assets/d91711bb-83d8-41b1-b451-6ed17b953bca" />

# Result

Thus we have cleaned the data and recover the outliers by detection using IQR and Z-score method.
         
