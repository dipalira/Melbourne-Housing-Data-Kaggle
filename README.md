# Melbourne-Housing-Data-Kaggle
For detailed report check final report in repo.
## EDA 
The entire dataset is comprised of 21 variables with 8 variables as characters or strings. Before moving onto the effect on the target variable (Price) by those 8 variables, the following table gives a summary statistic of some numeric variables. Every row in the dataset denotes information about property (house, townhouse etc) , price it is sold for, seller information and more characteristics such as number of bedrooms, location (latitude, longitude etc).
## Clustering of houses
The next step would be to treat every row of the data as vectors in pursuit of finding properties which are similar to each other. The algorithm used to achieve this feat is K means Clustering. For each cluster, you will place a point(a centroid) in space and the vectors are grouped based on their proximity to their nearest centroid. The following steps are used in clustering- 
1. **Cleaning Data**: For clustering, your data must be indeed integers. Moreover, since k-means is using Euclidean distance, having categorical column is not a good idea. I normalized my dataset which would have a certain set of variables chosen. All the none values were either imputed or removed in the previous step. The variable ‘Date’ in its standard format will not be fed well in the model so I made a new column which encodes the month of the date present and dropped the former. 
2. **Choose Number of Clusters and Standardize Data** - For choosing the number of clusters k, I use the Elbow method. Elbow method tries different values of k and plot the average distance of data points from their respective centroid (average within-cluster sum of squares) as a function of k. We look for the “elbow” point where increasing the k value drastically lowers the average distance of each data point to its respective centroid, but as you continue increasing k the improvements begin to decrease asymptotically. The ideal k value is found at the elbow of such a plot. I have also standardized the data to counter the high influence by variables having unusual scales then the rest.
Sample Results - 
1.	Features Observed – Property Count and Rooms

![alt text](https://github.com/dipalira/Melbourne-Housing-Data-Kaggle/blob/master/Images/cluster_!.png )

