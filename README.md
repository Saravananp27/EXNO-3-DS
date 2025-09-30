## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

 ```

 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df

```
<img width="467" height="452" alt="image" src="https://github.com/user-attachments/assets/b0e3cd98-411a-4e24-b25a-fc8c2618c44f" />

```

 from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])

```
<img width="242" height="266" alt="image" src="https://github.com/user-attachments/assets/ba5058ae-0129-474c-9b85-034cfd8964cf" />

```

df['bo2']=e1.fit_transform(df[["ord_2"]])
df

```
<img width="465" height="432" alt="image" src="https://github.com/user-attachments/assets/e0c90d4a-1fb0-4ec3-a951-7197a169e029" />

```

 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc

```
<img width="480" height="447" alt="image" src="https://github.com/user-attachments/assets/0f4a62ed-4a2e-450f-af0c-d1cc60102804" />

```

from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))

```

```

df2=pd.concat([df2,enc],axis=1)
df2

```
<img width="520" height="456" alt="image" src="https://github.com/user-attachments/assets/cffc1bf1-a0ee-431c-b6fa-26bfa024eb85" />


```

pd.get_dummies(df2,columns=["nom_0"])

```
<img width="1117" height="463" alt="image" src="https://github.com/user-attachments/assets/73753585-4d8f-4f4c-be0b-6b27536a8cd1" />


```

from category_encoders import BinaryEncoder
df=pd.read_csv("Encoding Data.csv")
df

```
<img width="503" height="441" alt="image" src="https://github.com/user-attachments/assets/1c65e2e5-234a-4d37-a202-43935dd47443" />

```

be=BinaryEncoder()
nd=be.fit_transform(df['ord_2'])
df

```
<img width="462" height="458" alt="image" src="https://github.com/user-attachments/assets/ff37b7e9-b910-4581-a484-9bb7178be580" />

```

pip install --upgrade category-encoders

```
```

from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df

```
<img width="782" height="470" alt="image" src="https://github.com/user-attachments/assets/6e1a00b6-a2ac-4833-9c46-b5acc5e14fce" />

```

 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df

```
<img width="787" height="451" alt="image" src="https://github.com/user-attachments/assets/d8fa0478-3c80-4354-bdf5-a3c86bcb050c" />

```

dfb=pd.concat([df,nd],axis=1)
dfb

```
<img width="1166" height="451" alt="image" src="https://github.com/user-attachments/assets/31e161e8-63c4-4468-b739-9766bb2c9a3f" />

```

from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC

```
<img width="737" height="432" alt="image" src="https://github.com/user-attachments/assets/6b67a955-3bbc-4b9e-bec4-19c09d3b8100" />

```

 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df

```
<img width="725" height="507" alt="image" src="https://github.com/user-attachments/assets/2145c520-5d69-4a2c-8862-a2326be9ec69" />

```

df.skew()

```
<img width="432" height="203" alt="image" src="https://github.com/user-attachments/assets/e318e0ee-0f00-422d-a89d-a86095e41b93" />

```

np.log(df["Highly Positive Skew"])

```
<img width="496" height="558" alt="image" src="https://github.com/user-attachments/assets/439197c0-02d2-4d3d-acca-ed9f5d865efc" />

```

np.reciprocal(df["Moderate Positive Skew"])

```
<img width="476" height="546" alt="image" src="https://github.com/user-attachments/assets/b0cafa73-170e-4ee6-8eed-054d2564b6a9" />


```

np.sqrt(df["Highly Positive Skew"])

```
<img width="519" height="562" alt="image" src="https://github.com/user-attachments/assets/9fcaf05e-84e0-4702-8c1f-ac22804bc82e" />

```

 np.square(df["Highly Positive Skew"])

```
<img width="555" height="582" alt="image" src="https://github.com/user-attachments/assets/7d9ff585-7dff-444c-af9b-9a65b26c5ce4" />

```

df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df

```
<img width="723" height="540" alt="image" src="https://github.com/user-attachments/assets/e9294730-5a73-4feb-9c36-dba001025717" />


```

df.skew()

```
<img width="477" height="256" alt="image" src="https://github.com/user-attachments/assets/87eae043-5c61-4835-9a58-3ecb3b9d56bf" />

```

df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()

```
<img width="536" height="303" alt="image" src="https://github.com/user-attachments/assets/b17ca1e9-257f-4ad8-a5c3-44efdb3671e2" />


```

 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate  Negative Skew"]])
 df

```
<img width="1380" height="589" alt="image" src="https://github.com/user-attachments/assets/dc2fa634-e594-45f8-bee0-9fa96c519cb5" />

```

import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()

```
<img width="786" height="571" alt="image" src="https://github.com/user-attachments/assets/8fa51a81-7ffa-47ed-9b03-0eff8f1110ce" />

```

sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()

```
<img width="829" height="584" alt="image" src="https://github.com/user-attachments/assets/7a844921-bbfb-4066-9fea-2a4c69e07d2d" />

```

 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()

```
<img width="731" height="540" alt="image" src="https://github.com/user-attachments/assets/1c76305a-2354-4905-9507-0a507f41fdfb" />

```

 df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
 sm.qqplot(df["Highly Negative Skew"],line='45')
 plt.show()

```
<img width="788" height="599" alt="image" src="https://github.com/user-attachments/assets/817ee6ae-bd0c-47a2-88fc-c38d4960ac6d" />

```

 dt=pd.read_csv("titanic_dataset.csv")
 dt
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 dt["Age_1"]=qt.fit_transform(dt[["Age"]])
 sm.qqplot(dt['Age'],line='45') 
 plt.show()

```
<img width="805" height="543" alt="image" src="https://github.com/user-attachments/assets/fb0c1b4f-928f-4196-bc35-3a9378742e4b" />


```

 dt=pd.read_csv("titanic_dataset.csv")
 dt

```
```

sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()

```
<img width="796" height="642" alt="image" src="https://github.com/user-attachments/assets/6bd4aea1-b641-4918-bf4b-df07d5b5f858" />


# RESULT:
        Thus the given data, Feature Encoding, Transformation process and save the data to a file
     was performed successfully

       
