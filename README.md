### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 15-10-2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
```python
import pandas as pd
df=pd.read_csv("/content/clustervisitor.csv")
df

cluster={
    'Young': (df['Age']<=30),
    'Middle_aged': ((df['Age']>30)&(df['Age']<=50)),
    'Elderly': (df['Age']>50)
}
print(cluster)

count=[]
for g,c in cluster.items():
  visitor=df[c]
  count.append(len(visitor))
  print(f"Visitors in {g} group")
  print(visitor)
  print(count)


import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='cyan')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()

```
### Output:

<img width="342" height="797" alt="image" src="https://github.com/user-attachments/assets/5a7cfb23-50c9-4ec0-92a7-e3bbc055060b" />

<img width="516" height="817" alt="image" src="https://github.com/user-attachments/assets/85b8b885-5b19-4378-9253-95a2112d27fb" />

<img width="892" height="668" alt="image" src="https://github.com/user-attachments/assets/df0f2483-b62b-4528-9dec-312b586ceeb1" />


### Program 2:
```python
import pandas as pd
import matplotlib.pyplot as plt

df=pd.read_csv('clustervisitor (Salary).csv')
df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
df3

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

kmeans=KMeans(n_clusters=3,random_state=32)
df3['cluster']=kmeans.fit_predict(df3)
print(df3)

plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary in thousands')
plt.title('Kmeans Cluster')
plt.show()
```
### Output:

<img width="453" height="800" alt="image" src="https://github.com/user-attachments/assets/ce0cf0f8-bf76-471d-af7c-2761094f193a" />


<img width="882" height="678" alt="image" src="https://github.com/user-attachments/assets/a4b1c79a-b2a6-479d-90ef-4f9d6ef7bed3" />

### Result:
Thus, cluster and Visitor Segmentation for Navigation patterns have been implemented successfully.
