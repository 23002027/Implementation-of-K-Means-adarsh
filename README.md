# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1)Choose the number of clusters (K): 
Decide how many clusters you want to identify in your data. This is a hyperparameter that you need to set in advance.

2)Initialize cluster centroids: 
Randomly select K data points from your dataset as the initial centroids of the clusters.

3)Assign data points to clusters: 
Calculate the distance between each data point and each centroid. Assign each data point to the cluster with the closest centroid. This step is typically  done using Euclidean distance, but other distance metrics can also be used.

4)Update cluster centroids: 
Recalculate the centroid of each cluster by taking the mean of all the data points assigned to that cluster.

5)Repeat steps 3 and 4: 
Iterate steps 3 and 4 until convergence. Convergence occurs when the assignments of data points to clusters no longer change or change very minimally.

6)Evaluate the clustering results: 
Once convergence is reached, evaluate the quality of the clustering results. This can be done using various metrics such as the within-cluster sum of squares (WCSS), silhouette coefficient, or domain-specific evaluation criteria.

7)Select the best clustering solution: 
If the evaluation metrics allow for it, you can compare the results of multiple clustering runs with different K values and select the one that best suits your requirements


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: KAMESH RR
RegisterNumber: 212223230095
*/
```

```python

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:

### data.head():

![image](https://github.com/user-attachments/assets/845cc9e0-610b-4306-9051-ed4653e5b256)


### data.info():

![image](https://github.com/user-attachments/assets/65383537-0ac6-4170-942b-2b2ca648d2ef)


### NULL VALUES:

![image](https://github.com/user-attachments/assets/1b62501f-8c4b-4b86-b103-9bda9fb34f83)



### ELBOW GRAPH:

![image](https://github.com/user-attachments/assets/bc7cd5fd-5ca4-4ea5-8c8c-e6da8b70a15f)


### CLUSTER FORMATION:

![image](https://github.com/user-attachments/assets/4991a675-ae76-4526-bfd5-50fab1a3a86c)


### PREDICICTED VALUE:

![image](https://github.com/user-attachments/assets/7e2270a7-bb7c-4c7b-9fc1-ff0666ca2684)


### FINAL GRAPH(D/O):

![image](https://github.com/user-attachments/assets/c8f7a335-2c85-4e47-b8ac-170b010cc4b4)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
