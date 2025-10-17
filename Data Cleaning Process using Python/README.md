# 🧼 Data Cleaning and Outlier Detection using Python  

## 🎯 Aim  
To read the given dataset, perform data cleaning, handle missing values, and detect outliers using **IQR** and **Z-Score** methods.

---

## 🧠 Explanation  
**Data Cleaning** is the process of preparing raw data for analysis by identifying and correcting inaccurate, incomplete, or irrelevant parts of the dataset.  
It doesn’t simply mean deleting data — instead, it focuses on improving the overall **accuracy and consistency** of the dataset.

Key steps include:
- Handling missing values  
- Removing duplicates  
- Standardizing formats  
- Detecting and removing outliers  

---

## 🧩 Algorithm  
**Step 1:** Read the given dataset.  
**Step 2:** Get information about the dataset (shape, info, etc.).  
**Step 3:** Identify and handle missing values using various techniques.  
**Step 4:** Save the cleaned data to a new file.  
**Step 5:** Remove outliers using the **Interquartile Range (IQR)** method.  
**Step 6:** Detect and remove outliers using the **Z-Score** method.  

---

## 👨‍💻 Developer Info  
**Name:** B. Surya Prakash  
**Email:** suryaprakashb2006@gmail.com  

---

## 🧹 Data Cleaning Process  
```python
import pandas as pd
x=pd.read_csv("/content/Data_set.csv")
x
```
![image](https://github.com/user-attachments/assets/03c9c35e-a60b-4735-b4f0-ae1c1c14801b)

```python
x.head(7)
```
![image](https://github.com/user-attachments/assets/59ae6795-433e-4122-887f-d18541b6434c)

```python
x.tail(5)
```
![image](https://github.com/user-attachments/assets/696fcd74-fad1-4052-93db-9fb402c0d620)

```python
x.isnull()
```
![image](https://github.com/user-attachments/assets/9ee64001-417f-43cb-9743-5c44a74ce4e9)

```python
x.notnull()
```
![image](https://github.com/user-attachments/assets/41b9e847-5bbc-4b11-a5b2-f635d8fa2d7d)

```python
x.fillna(5)
```
![image](https://github.com/user-attachments/assets/47294ee7-3e7a-4ad7-ab47-e4359053b329)

```python
x.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/8cd44836-e3fc-4fb4-92d0-f59739292012)

```python
x.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/d7b9660e-ff4f-49d5-97c5-26909ee65b69)

```python
x.shape
```
![image](https://github.com/user-attachments/assets/ad37fe69-ada4-44dd-989c-28a2d7675f5f)

```python
x.isnull().sum()
```
![image](https://github.com/user-attachments/assets/587677b4-25e3-4784-b64c-707e273aaf58)

```python
x.isnull().any()
```
![image](https://github.com/user-attachments/assets/a36647d3-4b65-46df-96e4-fd7ee536c642)

```python
x.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/539b95ac-066b-44c9-808a-8eb685c9a3e7)

```python
x.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/c55dfd92-7845-413d-a6ee-2d9023d595b6)

# IQR(Inter Quartile Range)
```python
import pandas as pd
x=pd.read_csv('iris.csv')
x
```
![image](https://github.com/user-attachments/assets/5195eba1-638a-4c36-a53c-c8b6187747e6)

```python
x.describe()
```
![image](https://github.com/user-attachments/assets/ecda6844-de3a-489a-86c6-6b2d27ebbe23)

```python
import seaborn as sns
sns.boxplot(x='sepal_width',data=x)
```
![image](https://github.com/user-attachments/assets/85ec522b-392d-4708-a2d9-b2429be2eda2)

```python
c1=x.sepal_width.quantile(0.25)
c3=x.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/2f76c166-ecbc-45a3-9b2d-7caf86fdfbf7)

```python
rid=x[((x.sepal_width<(c1-1.5*iq))|(x.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/5b94eaf5-dbd7-426e-8f9d-527a9b2e3dc2)

```python
delid=x[~((x.sepal_width<(c1-1.5*iq))|(x.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/7bb429bf-b186-4e8e-8ddb-5459079d6a38)

```python
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/d99d6bec-f86a-4c79-bfcf-0b0bcd88fdab)


# Z SCORE

```python
import pandas as pd
import scipy.stats as stats
import numpy as np
hp=pd.read_csv("/content/heights.csv")
hp
```
![image](https://github.com/user-attachments/assets/5a7a1872-8ae2-46ba-b462-701718474fe3)
```python
z=np.abs(stats.zscore(hp["height"]))
z
```
![image](https://github.com/user-attachments/assets/203ab38b-e07a-4c9f-9039-b43268238c81)

```python
hp1=hp[z<3]
hp1
```
![image](https://github.com/user-attachments/assets/dda80ae9-7c99-4754-85b7-114d80ca960d)
```python
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/0d2ab6c9-60d6-48b2-b595-501a9f1e9a9e)
```python
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/88be17ce-6b37-481e-8c26-9c4fc7761df1)
```python
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/28c26dad-d7d1-4eff-a6db-7c997dac06ee)
```python
df1 = df[((df['height'] >=low)& (df['height']<=high))]
df1
```
![image](https://github.com/user-attachments/assets/03523138-fe73-4062-8b92-ceb873b04732)


## 🧾Result

Hence, the dataset was successfully cleaned, and the outliers were detected and handled using IQR and Z-Score methods.

