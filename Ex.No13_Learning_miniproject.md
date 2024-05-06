# Ex.No: 10 Learning – Use Supervised Learning  
### DATE:                                                                            
### REGISTER NUMBER : 212221220058
### AIM: 
To write a program to train the classifier for Credit Card Fraud Detection.
###  Algorithm:

### Program:
```
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
```

```
# loading the dataset to a Pandas DataFrame
credit_card_data = pd.read_csv('/content/credit_data.csv')
```
```
# first 5 rows of the dataset
credit_card_data.head()
![image](https://github.com/srvasanthan33/AI_Lab_2023-24/assets/102546622/a1bc6acf-f559-4cc2-b2ef-1ad39803ea12)

```
```
credit_card_data.tail()
# dataset informations
credit_card_data.info()
# checking the number of missing values in each column
credit_card_data.isnull().sum()
```

```
# distribution of legit transactions & fraudulent transactions
credit_card_data['Class'].value_counts()
![image](https://github.com/srvasanthan33/AI_Lab_2023-24/assets/102546622/cdca4406-2b7b-4864-9791-e00afbf1d1e0)

```

This Dataset is highly unblanced

0 --> Normal Transaction

1 --> fraudulent transaction
```
# separating the data for analysis
legit = credit_card_data[credit_card_data.Class == 0]
fraud = credit_card_data[credit_card_data.Class == 1]
print(legit.shape)
print(fraud.shape)
```
(284315, 31)
(492, 31)
```
legit.Amount.describe()
fraud.Amount.describe()
# compare the values for both transactions
credit_card_data.groupby('Class').mean()
```
Under-Sampling

Build a sample dataset containing similar distribution of normal transactions and Fraudulent Transactions

Number of Fraudulent Transactions --> 492
```
legit_sample = legit.sample(n=492)
new_dataset = pd.concat([legit_sample, fraud], axis=0)
new_dataset.head()
new_dataset.tail()
new_dataset['Class'].value_counts()
![image](https://github.com/srvasanthan33/AI_Lab_2023-24/assets/102546622/36f48fcd-eba5-424f-aa66-50154cb27415)

new_dataset.groupby('Class').mean()
![image](https://github.com/srvasanthan33/AI_Lab_2023-24/assets/102546622/581f68fb-1008-400d-976f-8ca8e3d43bdc)


```
Splitting the data into Features & Targets
```
X = new_dataset.drop(columns='Class', axis=1)
Y = new_dataset['Class']
```



### Output:


### Result:
Thus the system was trained successfully and the prediction was carried out.
