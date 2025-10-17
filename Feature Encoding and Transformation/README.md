# 🔢 Feature Encoding and Transformation using Python

## 🎯 Aim
To perform feature encoding and transformation on the given dataset to convert categorical variables into numerical format suitable for machine learning models.

---

## 🧠 Explanation
Feature encoding converts categorical data into numerical values for modeling.  
Transformation may also include scaling, normalization, or applying mathematical functions to improve model performance.

---

## 🧩 Algorithm
1. Import required libraries (Pandas, NumPy, Scikit-learn).  
2. Load the dataset.  
3. Identify categorical features.  
4. Apply encoding methods:
   - **Label Encoding** for ordinal categories  
   - **One-Hot Encoding** for nominal categories  
5. Transform features as needed (log transform, scaling, etc.).  
6. Save the processed dataset.

---

## 👨‍💻 Developer Info
**Name:** B. Surya Prakash  
**GitHub:** [bsuryaprakash06](https://github.com/bsuryaprakash06)

---
## 🖥️ Coding and Output
```python
Name: Surya Prakash B
Reg No: 212224230281
```
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/user-attachments/assets/f2ce930a-fb66-4c51-a283-9c4e6cc2b73f)
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/user-attachments/assets/3ca97cd9-9637-4ab3-9484-f1afbb815c42)
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
![image](https://github.com/user-attachments/assets/57fc56e4-e0ec-4402-9497-e04b476eec86)
```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![image](https://github.com/user-attachments/assets/40cdf150-91c3-405f-8735-c8166ef44d05)
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2
```
![image](https://github.com/user-attachments/assets/572a5f11-9606-42f3-bec3-1245db698154)
```
pip install --upgrade category_encoders
```
![image](https://github.com/user-attachments/assets/c84d3b73-a3b5-41dd-8f05-9e860394b268)
```
from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df
```
![image](https://github.com/user-attachments/assets/cf5c2713-a0d3-4617-8228-1e5a2e5ff536)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb
```
![image](https://github.com/user-attachments/assets/ccf3431e-0310-4522-887d-c51dfb530dfa)
```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
![image](https://github.com/user-attachments/assets/ab6697b5-e849-48f9-8e0d-3d172645f50f)
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```
![image](https://github.com/user-attachments/assets/c2f56b16-7c0a-4947-a223-9c74166bb9cd)
```
df.skew()
```
![image](https://github.com/user-attachments/assets/6f5b6b86-55e8-414c-ada7-2ae779e38743)
```
np.log(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/ef33eda8-d0a1-41c5-97de-39d14b17b14b)
```
np.reciprocal(df["Moderate Positive Skew"])
```
![image](https://github.com/user-attachments/assets/ec34f248-c828-46f0-9b2d-d0b72f95456f)
```
np.sqrt(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/d577cccd-aefc-4b53-9cb7-5e99233ef9cf)
```
np.square(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/b7d2d028-c9f4-4c03-a854-b57454d7516a)
```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![image](https://github.com/user-attachments/assets/8f645d34-dcd0-4cdf-a702-f1a2b74724a7)
```
df.skew()
```
![image](https://github.com/user-attachments/assets/2f737125-9b94-4a84-ad9a-0da1e4be2811)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```
![image](https://github.com/user-attachments/assets/73bdc368-84d1-41f9-b6fc-e947c8f4d486)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/be600bef-7072-4e6b-b45e-7e13baf9731b)
```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/2b14c245-9e22-42d3-9fc9-47b8d968d1f6)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/945b8b66-5bfa-468a-a5b2-044ad0d468f2)
```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/c67266fb-0e79-48f5-a61d-80458965c572)
```
dt=pd.read_csv("/content/titanic_dataset.csv")
dt
```
![image](https://github.com/user-attachments/assets/215d0864-8562-448c-a5ab-23a96e511723)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/11b078fc-a6ea-4390-9249-0762463d60a6)

## 🧾RESULT:
The dataset was successfully transformed, with all categorical variables converted into numerical formats suitable for modeling.

       
