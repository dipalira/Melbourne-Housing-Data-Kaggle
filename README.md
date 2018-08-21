# Melbourne-Housing-Data-Kaggle
For detailed report check final report in repo.
## EDA 
The entire dataset is comprised of 21 variables with 8 variables as characters or strings. Before moving onto the effect on the target variable (Price) by those 8 variables, the following table gives a summary statistic of some numeric variables. Every row in the dataset denotes information about property (house, townhouse etc) , price it is sold for, seller information and more characteristics such as number of bedrooms, location (latitude, longitude etc).
## Clustering of houses
The next step would be to treat every row of the data as vectors in pursuit of finding properties which are similar to each other. The algorithm used to achieve this feat is K means Clustering. For each cluster, you will place a point(a centroid) in space and the vectors are grouped based on their proximity to their nearest centroid. The following steps are used in clustering- 
1. **Cleaning Data**: For clustering, your data must be indeed integers. Moreover, since k-means is using Euclidean distance, having categorical column is not a good idea. I normalized my dataset which would have a certain set of variables chosen. All the none values were either imputed or removed in the previous step. The variable ‘Date’ in its standard format will not be fed well in the model so I made a new column which encodes the month of the date present and dropped the former. 
2. **Choose Number of Clusters and Standardize Data** - For choosing the number of clusters k, I use the Elbow method. Elbow method tries different values of k and plot the average distance of data points from their respective centroid (average within-cluster sum of squares) as a function of k. We look for the “elbow” point where increasing the k value drastically lowers the average distance of each data point to its respective centroid, but as you continue increasing k the improvements begin to decrease asymptotically. The ideal k value is found at the elbow of such a plot. I have also standardized the data to counter the high influence by variables having unusual scales then the rest.


Sample Results - 

|Features Observed – Property Count and Rooms             |  Latitude/Longitude|
|--------------------------|-----------------------------| 
|![](https://github.com/dipalira/Melbourne-Housing-Data-Kaggle/blob/master/Images/cluster_!.png )  |  ![](https://github.com/dipalira/Melbourne-Housing-Data-Kaggle/blob/master/Images/cluster_5.png)|

## Prediction of Prices
### Penalized Linear Regression model:
I used Ridge and LASSO regression with the following pre-processing.
Following pre-processing steps were performed for all the models
• No scaling has been performed on the dataset. The RMSE values reported are of original scale.
• We selected Room, Price, Distance, Bathroom, Car, Landsize, Lattitude, Longtitude,
Propertycount, CouncilArea, Month, Method, Type, RegionName as features
• Some of the categorical variables like Month, Method, Type, RegionName was one hot encoded.
• Train/Test set split is 80%/20%
### Non - Parametric Methods- 
I used Random Foreset Regressor and Gradient Boosting Machine. Further to improve the model, I used a stacked model of the two previous models. 
Random forest is a meta estimator that fits a number of classifying decision trees on various sub-samples of the dataset and use averaging to improve the predictive accuracy and control over-fitting. Some of the constant paramters throught are 0.
GB builds an additive model in a forward stage-wise fashion; it allows for the optimization of arbitrary differentiable loss functions. In each stage a regression tree is fit on the negative gradient of the given loss function. Parameters which are constant throughout the model.

![https://github.com/dipalira/Melbourne-Housing-Data-Kaggle/blob/master/Images/comparasion.png]
