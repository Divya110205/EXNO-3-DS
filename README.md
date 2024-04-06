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
## FEATURE ENCODING:
### 1.Ordinal Encoding
```
import pandas as pd
df=pd.read_csv('/content/Encoding Data.csv')
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Blue','Green','Red']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["nom_0"]])
df['bo2']=e1.fit_transform(df[["nom_0"]])
df
```
### 2.Label Encoding
```
le=LabelEncoder()
dfc=df.copy()
dfc['nom_0']=le.fit_transform(dfc['nom_0'])
dfc
```
### 3.Binary Encoding
```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_1'])
df1=pd.concat([df,nd],axis=1)
df2=df.copy()
df1
```
### 4.One Hot Encoding
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=dfc.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['ord_2']]))
df2=pd.concat([df2,enc],axis=1)
pd.get_dummies(df2,columns=["ord_2"])
df2
```
## Feature Transformation
### Log Transformation
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df.skew()
np.log(df["Highly Negative Skew"])
```
### Reciprocal Transformation
```
np.reciprocal(df["Moderate Negative Skew"])
```
### Square Root Transformation
```
np.sqrt(df["Highly Negative Skew"])
```
### Square Transformation
```
np.square(df["Highly Negative Skew"])
```
### Boxcox method
```
df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
### Yeojohnson method
```
df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
df.skew()
```
# RESULT:
  Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.    

       
