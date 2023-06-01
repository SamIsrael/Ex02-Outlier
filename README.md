# AIM
To detect and remove the outliers in the given data set and save the final data.

# ALGORITHM
## STEP 1  
Import the required packages(pandas,numpy,scipy).
## STEP 2  
Read the given csv file.
## STEP 3  
Convert the file into a dataframe and get information of the data.
## STEP 4  
Remove the non numerical data columns using drop() method.
## STEP 5  
Detect the outliers in the data set using z scores method.
## STEP 6  
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR).
## STEP 7  
Check if the outliersare removed from data set using graphical methods.
## STEP 8
Save the final data set into the file.



# CODE
## bhp.csv
```python
import numpy as np
import pandas as pd
from scipy import stats

a = pd.read_csv('bhp.csv')
df = pd.DataFrame(a['price_per_sqft'])
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]

print(df1)

z = np.abs(stats.zscore(df))
df1 = df1[(z < 3)]
print(df1)

```
## height_weight.csv
```python
import numpy as np
import pandas as pd
from scipy import stats

a = pd.read_csv('height_weight.csv')
df = pd.DataFrame(a['height'])
print(df)
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
df2 = pd.DataFrame(a['weight'])
print(df2)
q1 = df2.quantile(0.25)
q3 = df2.quantile(0.75)
IQR = q3 - q1
df2_new = df2[((df2 >= q1 - 1.5 * IQR) & (df2 <= q3 + 1.5 * IQR))]
print(df2_new)

```

# OUTPUT

## bhp.csv
![image](./Screenshot%20from%202023-03-24%2012-45-27.png)

## height_weight.csv
![image](./Screenshot%20from%202023-03-24%2012-58-06.png)
![image](./Screenshot%20from%202023-03-24%2012-58-10.png)

# RESULT

Thus, the outliers are removed successfully.

