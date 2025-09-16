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
df=pd.read_csv("SAMPLEIDS.csv")
df
```

<img width="751" height="583" alt="image" src="https://github.com/user-attachments/assets/62154624-6aa7-4597-acd5-1a5aad2038e4" />

```
df.head()
```

<img width="732" height="150" alt="image" src="https://github.com/user-attachments/assets/df621fe8-aa89-4a7a-bd8c-2e6c3c26cedd" />

```
df.tail()
```

<img width="775" height="151" alt="image" src="https://github.com/user-attachments/assets/f93e652e-5cde-4d78-8843-18efceea8917" />

```
df.isnull()
```

<img width="627" height="572" alt="image" src="https://github.com/user-attachments/assets/f190ee59-3d58-4c74-ae85-4acf01934acd" />

```
df.isnull().sum()
```

<img width="155" height="227" alt="image" src="https://github.com/user-attachments/assets/0b1ed607-df3d-4256-8389-611c234c2a11" />

```
df.isnull().any()
```

<img width="155" height="222" alt="image" src="https://github.com/user-attachments/assets/db318229-9c12-466c-894b-eeca896687ef" />


```
df.dropna(axis=0)
```

<img width="731" height="367" alt="image" src="https://github.com/user-attachments/assets/46c40d44-4da3-4d95-89d7-b7d879a34d2c" />

```
df.dropna(axis=1)
```

<img width="248" height="568" alt="image" src="https://github.com/user-attachments/assets/bf72efa9-2908-45c1-a843-926ffc81cf97" />

```
df.fillna(2)
```

<img width="746" height="573" alt="image" src="https://github.com/user-attachments/assets/6765d95c-3e0c-4dc4-a672-6d7703d58bc0" />


```
df.fillna(method = 'ffill')
```

<img width="738" height="567" alt="image" src="https://github.com/user-attachments/assets/1fc9c792-1166-4f28-bed6-6cb6cd0cc632" />

```
df.fillna(method = 'bfill')
```

<img width="746" height="565" alt="image" src="https://github.com/user-attachments/assets/33e74a15-ecb7-4146-90b6-d5537e9bda14" />

```
df.fillna({'GENDER':'MALE','NAME':'DONGLY','ADDRESS':'ARNI','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

<img width="732" height="568" alt="image" src="https://github.com/user-attachments/assets/edf798be-3a6a-4826-ac6d-a2b31b2dbfcb" />

```
ir=pd.read_csv('iris.csv')
ir
```

<img width="448" height="347" alt="image" src="https://github.com/user-attachments/assets/e430c999-6ff5-4ef0-90e9-dd1ccc2a7ec3" />

```
ir.describe()
```

<img width="442" height="233" alt="image" src="https://github.com/user-attachments/assets/650b6ec1-452a-4cfb-9d4f-f0bfc2e25f94" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="577" height="460" alt="image" src="https://github.com/user-attachments/assets/ceafe076-07f9-4556-b6b4-17fe6db2c7c9" />


```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
0.5

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

<img width="282" height="92" alt="image" src="https://github.com/user-attachments/assets/6c77f4e6-8fce-4fed-a789-0d6d2f15055d" />


```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```

<img width="442" height="347" alt="image" src="https://github.com/user-attachments/assets/65520cfc-ce7f-483f-9522-072ac455fdb7" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="528" height="460" alt="image" src="https://github.com/user-attachments/assets/6c3334f5-634c-472a-94e7-661d9afa942c" />

```
import numpy as np
import scipy.stats as stats
```
```
z = np.abs(stats.zscore(delid['sepal_width']))
z
```

<img width="382" height="215" alt="image" src="https://github.com/user-attachments/assets/bdd64b75-e1b3-40d3-bb06-6e67e00ba5ef" />


```
df =delid[z<3]
df
```

<img width="456" height="348" alt="image" src="https://github.com/user-attachments/assets/c8b6f9ad-4548-47ae-907f-18da8a1e9113" />

# Result

This is the process to read the given data and perform data cleaning and save the cleaned data to a file.
