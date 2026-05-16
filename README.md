# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Step1: Import the necessary packages using import statement.
Step2: Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
Step3: Import KMeans and use for loop to cluster the data.
Step4: Predict the cluster and plot data graphs.
Step5: Print the outputs and end the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: VEDARANJAN S
RegisterNumber: 212225220119
*/

import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv(r"C:\Users\acer\Downloads\Mall_Customers.csv")
data.head()
```
<img width="1105" height="321" alt="image" src="https://github.com/user-attachments/assets/ede4ac4b-7b4d-48d8-b430-db986ede667f" />

```
data.info()
```
<img width="1037" height="401" alt="image" src="https://github.com/user-attachments/assets/e5585068-c1b8-43a0-9bb1-51af81cc9c81" />

```
data.isnull()
```
<img width="1188" height="617" alt="image" src="https://github.com/user-attachments/assets/1718465e-d347-4e39-8f94-675789669d23" />

```
data.isnull().sum()
```
<img width="722" height="207" alt="image" src="https://github.com/user-attachments/assets/2dcc8306-7f95-47f0-80b6-c39cf08553ad" />

```
from sklearn.cluster import KMeans
wcss= [] 
for i in range(1,11):
    kmeans=KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
<img width="1062" height="717" alt="image" src="https://github.com/user-attachments/assets/195d87c4-a0d6-426d-9e91-0d90d83b758c" />

```
km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
<img width="1257" height="353" alt="image" src="https://github.com/user-attachments/assets/7750bed5-3af9-4430-8baf-43d0e6c4e781" />

```
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="black",label="cluster")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="cyan",label="cluster")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="yellow",label="cluster")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="green",label="cluster")
plt.legend()
plt.title("Customer Segments")
```
<img width="1191" height="811" alt="image" src="https://github.com/user-attachments/assets/5b64f304-c7e4-4c40-8c5d-ea8002cac717" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
