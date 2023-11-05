# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Choose the number of clusters (K).
2. Initialize cluster centroids.
3. Assign data points to clusters.
4. Update cluster centroids.
5. Repeat steps 3 and 4.
6. Evaluate the clustering results.
7. Select the best clustering solution.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Barath S
RegisterNumber:  212222230018
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
## data.head()
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/4a29395c-3666-4b87-9806-aba984b4cece)

## data.info()
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/c2d32fb2-5c2e-4886-905e-f8fa2259ecf9)


## data.isnull().sum()
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/2def77e8-365f-4cf4-b39b-16d7d55d7688)


## Elbow method graph
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/83b152fb-6757-4988-b303-b6bf38f2f39e)


## K means clusters
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/5b5fd28b-b22d-48ec-b392-4a9e283ea137)
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/587f4daa-b629-4869-8e3c-b8cae5654fea)


## Customer Segments graph
![image](https://github.com/barathsubramani/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118542617/0ed6f847-04cc-4994-9eca-53bc777fef31)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
