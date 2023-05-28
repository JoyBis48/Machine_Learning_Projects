#	Introduction

In this dissertation, we aim to identify the optimal Wi-Fi channel for a given location, based on several Wi-Fi attributes such as RSSI, frequency, channel, signal quality, and channel width. To achieve this, we will use the K Means clustering algorithm, which is a popular unsupervised machine learning technique for partitioning data into K clusters based on their similarities. 
### 	Justification for the selection of K-Means as our Clustering Algorithm.

•	K-Means Clustering is one of the most widely used and well established clustering algorithm and is mostly preferred in almost all scenarios concerned with clustering of data. K-means is also computationally efficient and relatively easier to implement.

•	This algorithm will also be able to provide a quantitative framework for the comparison and evaluation of different channels based on the assigned clusters. It assigns the data points to clusters in such a way that it minimizes the within cluster sum of squares (WSS), which results in higher similarity within clusters and higher dissimilarity between clusters. By, leveraging this measure, the K-Means Clustering Algorithm is able to identify the most suitable Wifi Channel having the least interference based on the inherent patterns that Wifi attributes exhibits over the channel interference and performance.

•	K-Means also has high interpretability which is a necessity for proper inference. This interpretability enables the users to understand the implications and characteristics of each cluster, which ultimately will facilitate better informed decision regarding the selection of Wifi Channel. 
These were the reasons why K-Means Clustering Technique was deemed to be suitable for this task.

### 	Working of K-Means Clustering Algorithm and its parameters. 
The K-Means Clustering algorithm works by repeatedly assigning data points to the nearest centroids and updating the centroids based on the average of the data points within the cluster. The algorithm starts by choosing K initial centroids (Kodinariya et al.,2013), either randomly or based on prior knowledge of the data. Each data point is then assigned to the cluster with the closest centroid. The algorithm then calculates the average of all assigned data points to update the centroid of each cluster. This process is repeated until the centroids do not change significantly between iterations, or until a certain number of iterations is reached-Means algorithms are most commonly used in applications such as image segmentation, anomaly detection etc. However, there are some limitations to it, such as sensitivity to initial selection of centroids and number of clusters selected. K-Means is also sensitive to the presence of outliers in the data and it can affect the final result. 
The parameter passed to the K-Means Clustering algorithm is just the n_clusters, which determines the number of clusters to be formed and the number of centroids to generate.
Elbow Point Method is a widely used method for getting to know the optimal number of clusters (k) that can be formed. It is more applicable for relatively small k values (Cui, M., 2020). This involves plotting the within-cluster sum of squares (WSS) versus the number of clusters and choosing the value of K at which the WSS begins to level off or "elbow" point. WSS is a measure of cluster compactness or tightness, calculated as the sum of the squared distances between each data point and its assigned centroid within each cluster. WSS decreases as the number of clusters increases as clusters become smaller and more concentrated. The optimal number of clusters is usually chosen as the value of K corresponding to the elbow point. The Silhouette method is another widely used method for the estimation of the optimal cluster number. (O. Arbelaitz, 2013)

##  Data Gathering
For the gathering of the Wi-Fi attribute data, a Wi-Fi Analyser app was downloaded namely WifiInfoView. WifiInfoView is a small utility developed by NirSoft that displays detailed information about wireless networks in any area such as SSID, Signal quality, Frequency, Channel, Encryption type, etc. The application scans for wireless networks in an area, collects information from available networks, and displays it in a simple, easy-to-read interface. 
For this Dissertation purpose, this application was opened and was used to analyse information of the wireless network from 6th Floor to 2nd Floor of the resident building. The analysed data from all these floors was then exported into an HTML report. The report was then converted into csv format. Five sets of csv data were created, which was then merged and sorted in the Google Colab itself running Python 3.9 for the creation of the final csv data named as Wifi_Attributes.csv
 
##  Data Pre-Processing
Before applying the K Means clustering algorithm, we need to first pre-process the data to ensure that it’s suitable for clustering. Following steps were taken: -
Data Cleaning: Since the dataset was created and not taken from online sources, there were no missing values as such. All the columns having any missing data were already removed before the creation of the analysis report itself.
Feature Selection: All the irrelevant features recorded by the Wi-Fi Analyser app such as encryption data, Mac Address were removed from the data set beforehand during report analysis. RSSI, Signal Quality, Average Signal Quality, Frequency, Channel, Channel Width are the features that were finally taken which seemed most relevant for the clustering.
Data Scaling:  Min-max scaling was to standardize the data to a common scale, ensuring that no attribute dominates the clustering process due to its large value range. It works by scaling each feature to a specified range, usually between 0 and 1. This is achieved by subtracting the minimum value of the feature and dividing by the range between the minimum and maximum values. The resulting values will lie between 0 and 1. The scaling can also be done for a different range, by multiplying with a suitable factor then adding the value of the lower range.
 

The formula for min-max scaling is:
scaled_value = (value - min) / (max - min)
Min-max scaling is useful for algorithms that are sensitive to the scale of the input features, such as distance-based algorithms like K-means clustering or SVM (Support Vector Machine). It ensures that all features are treated equally and can have a similar impact on the outcome of the algorithm. (Mohamad, I.B. and Usman, D., 2013)



##  Implementation 
  

K Means Clustering Algorithm was used for establishing relationship among the Wi-Fi attributes. The following were the steps involved in applying the K Means clustering algorithm:
Selecting the number of clusters: The number of clusters (K) was chosen based on the elbow point method, which involves plotting the within-cluster sum of squares (WSS) versus the number of clusters. The point where the WSS stars to level off gives the value of K. It provided the optimal number of clusters that can be formed. 
 

Initializing the centroids: K data points were randomly selected as initial centroids for each cluster.
Assigning data points to clusters: Each data point was assigned to its nearest centroid based on the Euclidean distance between them.
Updating centroids: The centroid of each cluster was updated by taking the mean of all the data points assigned to it.
Repeating steps till convergence: The above steps were repeated until the centroids no longer changed significantly between iterations.
 

##  Plotting of the Cluster Diagrams.
After the clustering is done, we will get a cluster index ranging from 0 to 4, since we intended to have a total of 5 clusters. The cluster index maps each of the column values based on the grouping of data points done using the K-Means Clustering Algorithm. After the index has been concatenated with the main dataframe. It can then be used to plot relevant cluster diagrams, from which based on the underlying patterns and trends, we will be able to provide insight on the channel suffering with the highest interference. We would also be able to infer on the channels that are best suited to be used for a particular region from these results. 
 

The Channel v/s Average Signal Quality cluster plot with the cluster index as the hue, is shown here. It was plotted using the scatter plot that comes with matplotlib. Five separate dataframes were created for the purpose of keeping each of the cluster in a separate dataframe. All these dataframes thus created namely df1, df2 df3, df4 and df5 were assigned a colour, for proper visualisation in the cluster plot as shown below.
It should be noted that in case of clustering, with each run, the cluster index changes, but the overall clusters and the cluster plot will always remain fixed for a given dataset. So, the colour that were coded for a specific cluster index will be subject to change each run. The output shown here may not be the representative of the output that will be shown when the code is run again, in terms of the colour of each cluster. As far as the clusters are concerned, it will remain the same, no matter the times, the code is run.
 

This cluster plot shows the relationship of the Cluster with the respective channel. It is an indication of the channel association with the cluster and helps to provide insight on how good of a representation each cluster is for a specific channel.
 

After that the RSSI v/s Cluster diagram was plotted as well to visualize relationship between each clusters to the received signal strength by the user in a specific location.

##  Evaluation of the Clustering Technique.
Now for the evaluation of this K-Means Clustering that was performed will be done through Silhouette analysis and Silhouette score. Silhouette analysis is a widely used metric to check the quality of the clustering that was performed. It is a measure of the degree of closeness of data points with other data points in a cluster, and how separated all the clusters are from each other. The score is mainly dependent on two parameters namely mean intra-cluster distance and mean nearest-cluster distance. The value of the score ranges from -1 to 1 (Unsupervised Machine Learning: Clustering Algorithms, 2021), where -1 signifies that the cluster are not assigned properly, and is the worst kind of cluster. A score of 0 or near 0 signifies that the clusters are overlapping and that the distance between samples of one cluster to the neighbouring cluster is very low. A score of +1 signifies that the clusters are very compact and well separated from each other, and is the best kind of clusters that can be formed for the given dataset.
¬¬ 

Here we can see that each clusters are plotted against their respective Silhouette coefficient. The thickness owing to each cluster plot determines the size of the cluster, and their corresponding silhouette coefficient signifies the compactness of the cluster. Finally, for the K-Means Clustering in our case, we got a score of 0.6608
We also included a few other metric to evaluate the results that we obtained.  

Silhouette Score	0.6608
Davies Bouldin Score	0.5252
Calinski Harabasz Score	567.9577

The Davies-Bouldin score gave a value of 0.5251, where the score is measured in terms of the average similarity score of every cluster with its most similar cluster (A. A. Vergani and E. Binaghi, 2018). The similarity is just the ratio of within-clusters distances to between-cluster distances. Lower score signifies better clustering.
While the Calinski-Harabasz score gave a score of 567.957 and is based on Variance Ratio Criterion. The score is a ratio of the sum of between-cluster dispersion against the within-cluster dispersion, where the sum of distance squared is referred to as the dispersion (Maulik, U. and Bandyopadhyay, S., 2002). Higher the Calinski-Harabasz score, better is the clustering.
These scores tells us that K-Means Clustering did a good enough job of clustering the data points. It indicates that the clusters are quite compact, having a relatively high cohesion and are well separated from each other.
##  Comparison of Clustering Algorithms
###  Justification for the use of Gaussian Mixture for comparison

•	GaussianMixture has the ability to more accurately capture complex and flexible distribution of data when compared to K-Means. It models data points as a mixture of Gaussian distributions allowing for varying shape and size of cluster, in contrast to spherical cluster assumption of K-Means.

•	It also incorporates probabilistic assignment of data points to clusters which can help capturing non-linear and diverse patterns related to the channel performance. These probabilistic nature allows for accurate representation, which can be beneficial in cases involving uncertain or overlapping boundaries of channel configurations. 

•	Also the fact that this algorithm is quite good in handling data having mixed or continuous attributes, which might be the case with Wi-Fi attribute data.
These reasons made the GaussianMixture a suitable algorithm for comparison with K-Means in order.
###  Comparative Analysis and parameters of GaussianMixture
For the n_components parameter of this algorithm, we set its value to be 5, as we would want the same number of clusters to be formed, based on the Elbow point visualisation done before. init_params was set to ‘kmeans’ 
 Just like we did for the K-Means, we performed the Silhouette Analysis for Gaussian Mixture.
 
Comparing the analysis, with the K-Means Clustering, we can see that the score is exactly the same, which signifies that both the clustering techniques formed the same clusters from the given data points. It should be noted that from previous run of this code, there were times where the silhouette score of GaussianMixture showed a value slightly less than the K-Means Cluster, but on maximum runs, it were exactly the same. Hence, we can infer that K-Means Clustering either performs just as good as GaussianMixture, or can perform slightly better than Gaussian Mixture, in terms of clustering of the datapoints.
From the visualisation of the cluster plot, we utilise the seaborn library this time, for the scatter plots.
 

The Gaussian Mixture’s Channel v’s AVG plot with cluster index as hue is same when compared to the plot we got for the K-Means. It is evident, as we got the Silhouette score of both these clustering techniques to be same as well.
 
										
Similarly, the Channel v/s Cluster plot and the RSSI v/s Cluster plot of the Gaussian Mixture is found to be the same as well. Now to get the similarity index of the labels that were generated by the K-Means Cluster, with other clustering algorithms, we consider the labels of the K-Means Cluster to be the ground truth value, and then compare it to the values generated by all the other clustering techniques for the same dataset. For the measure of the similarity index, we import various metrics for the scoring purpose namely Adjusted Rand Score, V Measure Score, Adjusted Mutual Information Score, Fowlkes-Mallows Score, Homogeneity Score and Completeness Score.

     

The scores thus obtained was later converted into a dataframe named ‘table’ for better visualisation. The scores are then observed using the .head() function . We can see, that the Gaussian Mixture score is 1, which indicates exact matching of the labels. This is the reason why the Silhouette score and the cluster plots for both these clustering techniques were the same. This table essentially shows how similar the labels of the given clustering techniques are, when compared with the labels produced by the K-Means Clustering Technique.           
##  Advantages and limitations of these algorithms used.
Due to high interpretability, easy implementation and efficient computation, K-Means is a great choice, when it comes to clustering data points, but there are some limitations that needs to be considered as well. One of them being that, K-Means assumes the cluster to be spherical in shape, which may not hold true in complex scenarios. This algorithm may struggle to accurately capture irregularly shaped clusters which might lead to suboptimal results. This algorithm is also highly sensitive to outliers, and may require their elimination from the dataset for proper clustering.
GaussianMixture on the other hand is quite suitable in identifying complex or irregularly shaped clusters, but it’s limited by low interpretability. Due to its probabilistic assignments of data points to clusters, it sometimes become difficult to assess the cluster plot. It can also be computationally demanding. Proper pre-processing might be required when dealing with large datasets.
                                               
## 	Discussion

 
In the Channel v/s Average Signal Quality Cluster Plot, we can see that the the red cluster indexed as 3 and the yellow cluster indexed as 2 are a representative of the channel number 11. The yellow cluster is associated with a relatively higher average signal quality (AVG). Similarly, the blue cluster indexed as 2 is also associated with higher AVG. The blue cluster is almost equally associated with channel 1 and 6. It can be seen that black, green and red clusters are all associated with low AVG and are a representative of the channels 1, 6 and 11 respectively. 
The Cluster vs Channel plot essentially confirms the same inference that we gathered from the previous cluster plot which states the corresponding representativeness of each cluster to a specifc channel.
                               

                   
This cluster diagram of RSSI v/s Cluster Plot showing the plot between RSSI (Received Signal Strength Indicator) and Cluster mainly captures the relative association of each cluster to the Signal strength as received by the user. Here, the yellow and blue cluster are shown to be associated with higher signal strength that was received at that time in that region. Thus we get a similar inference from the first cluster plot that was produced. 
Now for the insight on the interference part, it can be visualised that channel 11 has the entirety of the yellow cluster which is a representative of higher signal strength. Channel 1 and 6 both have association with the blue cluster that represents higher AVG, which signifies that both channel 1 and 6 has contributed to this higher AVG and not just by any one entirely. Green, red and black cluster indicating lower signal strength are all present in each of the cluster. From the combined effect of these pattern, it can be concluded that Channel 11 is the most suitable channel that should be used for that region, as it suffers from the least amount of interference based on these results. Channel 1 and 6 likely suffers from comparable level of interference. 
Hence Channel switching from 1 to 6 or vice versa will not show any significant difference in the throughput, but the channel switch from either of these channel to channel 11 may potentially increase the throughput and thus improve the performance.
During the comparison between K-Means and GaussianMixture, the results of the performance evaluation of both these algorithms are as given below:-
Algorithm Used	Silhouette Score
K-Means Clustering	0.6608
GaussianMixture	0.6608

The result we obtained essentially shows that both of the algorithm generated the exact same labels, and thus the same clusters. In previous runs, K-Means did have few instances with a slightly higher score than GaussianMixture, but the scores were shown to be the same for subsequent runs of the code.

The reason for these observation can be summarised as follows.
•	Simplicity of the dataset:  Due to the relative simplicity of the dataset used, the clusters exhibit good separation and has distinct boundaries, in such cases the K-Means assumption of spherical size clusters of equal size align well with the underlying data. Due to which we can observe similar Silhouette scores between K-Means and Gaussian Mixture.

•	Redundancy of GaussianMixture in dataset having insufficient complexity: Due to the Wifi attribute data being not that complex and lacks overlapping patterns, the additional flexibility provided by the GaussianMixture seems to be redundant, which might be the reason why we don’t observe much difference in the score. 

•	Suitability of K-Means: K-Means Clustering being a simpler and more computationally efficient algorithm compared to GaussianMixture, seems best suited for this task, and the lack of substantial improvement from GaussianMixture suggests that the added complexity introduced by this algorithm, may not be necessary for this particular task.

# Conclusion
This dissertation mainly focussed on the ways of increasing the throughput of Wireless Networks, be it by adapting channel width, channel selection based on parameters or through proper placement of access points and minimize delay, latency, pickup loss rate as a result. Here, we mainly focussed on the channel selection aspect for improving performance. The details of the Wi-Fi attributes namely RSSI, frequency, channel, signal quality, and channel width of a given region were all clustered using K-Means Clustering Algorithm and the resulting cluster diagrams were visualised using tools from Seaborn and Matplotlib libraries. Then Silhouette scoring was used for the evaluation of the clusters. Through the insight gathered from the visualisation, it was inferred that Channel 11 suffered from the least amount of interference in that region, and switching from channel 1 or 6 to channel 11 might lead to increased performance.
Comparison of the K-Means Clustering Algorithm with the Gaussian Mixture were also performed and it was found that the K-Means Clustering Algorithm only performed either marginally better than Gaussian Mixture or performed exactly the same as that of the Gaussian Mixture, based on the inference gained from the Silhouette Analysis and Cluster diagrams of both these clustering techniques.
The similarity index of the labels generated by the K-Means Clustering with several other clustering algorithms, was done based on several scoring metrics, where the K-Means Clustering generated labels were considered to be the ground truth labels for the sake of the comparison.
