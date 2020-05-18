# clusteringcustomers

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA

df = pd.read_csv('iris.csv', usecols=[0,1,2,3], names=[1,2,3,4])

kmeans = KMeans(n_clusters=3)
kmeans.fit(df)
c = kmeans.cluster_centers_
kmeans.labels_

pca = PCA(n_components=2)
pca.fit_transform(df)
pca.fit_transform(c)

df.plot(kind='scatter',x=1,y=2,c=kmeans.labels_, edgecolors='b')
plt.scatter(c[:,0],c[:,1], c='r', s=50)
plt.show()
