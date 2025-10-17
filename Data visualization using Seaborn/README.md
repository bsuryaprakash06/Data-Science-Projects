
## **EXNO6 – Data Visualization using Seaborn**


# 🎨 Data Visualization using Seaborn

## 🎯 Aim
To create advanced visualizations using **Seaborn** for better insights and pattern recognition.



## 🧠 Explanation
Seaborn builds on Matplotlib for statistical plots with less code.  
It helps visualize distributions, relationships, and correlations with aesthetically pleasing plots.

## 🧩 Algorithm
1. Import Seaborn and Pandas.  
2. Load dataset.  
3. Visualize univariate distributions using **distplot** or **histplot**.  
4. Visualize bivariate relationships using **scatterplot**, **boxplot**, and **violinplot**.  
5. Analyze correlations using **heatmaps**.  



## 👨‍💻 Developer Info
**Name:** B. Surya Prakash  
**GitHub:** [bsuryaprakash06](https://github.com/bsuryaprakash06)


## 🖥️ Coding and Output
```python

import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
```
```
x = [1, 2, 3, 4, 5]
y = [3, 6, 2, 7, 1]
sns.lineplot(x=x,y=y)
```
![image](https://github.com/user-attachments/assets/f654d15c-f28b-4a3d-b1a6-a091430b12f1)
```
df = sns.load_dataset("tips")
df
```
![image](https://github.com/user-attachments/assets/5cd1f4fd-68c3-4963-a957-40c92314f04f)
```
sns.lineplot(x="total_bill",y="tip", data=df, hue="sex", linestyle='solid', legend="auto")
```
![image](https://github.com/user-attachments/assets/8cdb2fd3-fc63-48ae-84c8-c46356b3a30d)
```
x=[1, 2, 3, 4, 5]
y1=[3, 5, 2, 6, 1]
y2=[1, 6, 4, 3, 8]
y3=[5, 2, 7, 1, 4]
```
```
sns.lineplot(x=x, y=y1)
sns.lineplot(x=x, y=y2)
sns.lineplot(x=x, y=y3)
plt.title("Multi-Line Plot")
plt.xlabel('X Label')
plt.ylabel("Y Label")
```
![image](https://github.com/user-attachments/assets/74326e23-f6cd-4383-b54d-262c18361e11)
```
tips=sns.load_dataset('tips')
avg_total_bill = tips.groupby('day')['total_bill'].mean()
avg_tip = tips.groupby('day')['tip'].mean()
plt.figure(figsize=(8, 6))
p1 = plt.bar(avg_total_bill.index, avg_total_bill, label='Total Bill')
p2 = plt.bar(avg_tip.index, avg_tip, bottom=avg_total_bill, label='Tip')
plt.xlabel('Day of the Week')
plt.ylabel('Amount')
plt.title('Average Total Bill and Tip by Day')
plt.legend()
```
![image](https://github.com/user-attachments/assets/67727123-28e6-4c39-9b00-95f2f954c5ed)
```
avg_total_bill = tips.groupby('time')['total_bill'].mean()
avg_tip=tips.groupby('time') ['tip'].mean()
p1= plt.bar(avg_total_bill.index, avg_total_bill, label='Total Bill', width=0.4)
p2 = plt.bar(avg_tip.index,avg_tip,bottom=avg_total_bill,label='Tip', width=0.4)
```
![image](https://github.com/user-attachments/assets/e1263036-b99f-4430-b7f6-2aed77b0feda)
```
years=range(2000, 2012)
apples=[0.895, 0.91, 0.919, 0.926, 0.929, 0.931, 0.934, 0.936, 0.937, 0.9375, 0.9372, 0.939]
oranges = [0.962, 0.941, 0.930, 0.923, 0.918, 0.908, 0.907, 0.904, 0.901, 0.898, 0.9, 0.896, ]
```
```
plt.bar(years, apples)
plt.bar(years, oranges, bottom=apples)
```
![image](https://github.com/user-attachments/assets/51050198-fe86-4b3e-a4ef-0e301063d449)
```
import seaborn as sns
dt= sns.load_dataset('tips')
sns.barplot(x='day', y='total_bill', hue='sex', data=dt, palette='Set1')
plt.xlabel('Day of the Week')
plt.ylabel("Total Bill")
plt.title('Total Bill by Day and Gender')
```
![image](https://github.com/user-attachments/assets/d14f9141-ee89-4fe7-a51b-12594e2298a7)
```
import pandas as pd
tit=pd.read_csv("/content/titanic_dataset.csv")
tit
```
![image](https://github.com/user-attachments/assets/01422c49-2a5d-4fb0-9fbb-7c4e0b3842dd)
```
plt.figure(figsize=(8,5))
sns.barplot(x='Embarked', y='Fare', data=tit, palette='rainbow')
plt.title("Fare of Passenger by Embarked Town")
```
![image](https://github.com/user-attachments/assets/1e7c31e2-4167-40a1-beef-a887866d31cb)
```
plt.figure(figsize=(8,5))
sns.barplot(x='Embarked', y='Fare', data=tit, palette='rainbow', hue='Pclass')
plt.title("Fare of Passenger by Embarked Town, Divided by Class")
```
![image](https://github.com/user-attachments/assets/8da214b6-f26f-4a56-8e6f-bf2258332aaa)
```
tips=sns.load_dataset('tips')
sns.scatterplot(x='total_bill', y='tip', hue='sex', data=tips)
plt.xlabel('Total Bill')
plt.ylabel("Tip Amount")
plt.title('Scatter Plot of Total Bill vs. Tip Amount')
```
![image](https://github.com/user-attachments/assets/0439468e-0463-4992-a1ed-eb113cc1c52e)
```
num_var = np.random.randn(1000)
num_var=pd.Series(num_var, name = "Numerical variable")
num_var
```
![image](https://github.com/user-attachments/assets/25a34f2a-0921-4a21-b757-f1ccf9104850)
```
sns.histplot(data = num_var, kde = True)
```
![image](https://github.com/user-attachments/assets/7ed01ceb-dec4-4c22-97af-4c6e04c6d19e)
```
df=pd.read_csv("/content/titanic_dataset.csv")
sns.histplot(data=df,x="Pclass", hue="Survived", kde=True)
```
![image](https://github.com/user-attachments/assets/31452360-c687-4f83-8dc3-40289265c6e8)
```
tips=sns.load_dataset('tips')
sns.boxplot(x=tips['day'], y=tips ['total_bill'], hue=tips['sex'])
```
![image](https://github.com/user-attachments/assets/4c21c519-3c45-4a7d-911e-8ea7baf0fada)
```
sns.boxplot(x="day", y="total_bill", hue="smoker", data=tips, linewidth=2, width=0.6, boxprops={"facecolor": "lightblue", "edgecolor": "darkblue"},
whiskerprops={"color": "black", "linestyle": "--", "linewidth": 1.5}, capprops={"color": "black", "linestyle": "--", "linewidth": 1.5})
```
![image](https://github.com/user-attachments/assets/2f096384-fe80-41aa-8aab-87c45559515b)
```
sns.violinplot(x="day", y="total_bill", hue="smoker", data=tips, linewidth=2, width=0.6, palette="Set3", inner="quartile")
plt.xlabel("Day of the Week")
plt.ylabel("Total Bill")
plt.title("Violin Plot of Total Bill by Day and Smoker Status")
```
![image](https://github.com/user-attachments/assets/43e14a8e-d4db-462d-b39e-b851e19743d1)
```
mart=pd.read_csv("/content/titanic_dataset.csv")
mart
```
![image](https://github.com/user-attachments/assets/604a63e4-a508-4b6c-b326-f7498dfb5fc5)
```
mart=mart[['PassengerId', 'Survived', 'Age', 'Name', 'Ticket', 'Embarked']]
mart.head(10)
```
![image](https://github.com/user-attachments/assets/fc13c0dc-9fbe-4be2-a297-25ebdc7b9c53)
```
sns.kdeplot(data=mart,x='PassengerId')
```
![image](https://github.com/user-attachments/assets/d2b87439-1137-471e-a7a5-c06841372b47)
```
sns.kdeplot(data=mart,x='Age')
```
![image](https://github.com/user-attachments/assets/39dfcc3a-6b04-45c1-baf1-e868f63a7dbf)
```
sns.kdeplot(data=mart)
```
![image](https://github.com/user-attachments/assets/9a8c5f45-4e3a-4921-9489-e5ce79c1b162)
```
sns.kdeplot(data=mart,x='PassengerId',hue='Survived',multiple='stack')
```
![image](https://github.com/user-attachments/assets/1fbf5dfd-a5f6-4a6f-954f-a0cbe2551a2c)
```
sns.kdeplot(data=mart,x='PassengerId',y='Survived')
```
![image](https://github.com/user-attachments/assets/45828de0-2627-4dcc-b842-74413bf35df9)
```
data = np.random.randint(low = 1, high = 100, size = (10,10))
hm=sns.heatmap(data=data,annot=True)
```
![image](https://github.com/user-attachments/assets/ba17a41f-81b2-459a-bfa9-676a66da195d)
```
hm=sns.heatmap(data=data)
```
![image](https://github.com/user-attachments/assets/fa24237c-7805-487a-a1a7-dc2538a0d6fc)

## 🧾Result:
Seaborn visualizations successfully highlighted distributions, relationships, and patterns in the dataset, enabling better insights.
