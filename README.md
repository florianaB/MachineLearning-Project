# Machine Learning Project - How adults are learning to code
Project for Machine Learning subject
Refer to file: How Adults Learn To Code - Algorithms-Final.ipynb

## Dataset related information
More than 31,000 people responded to freeCodeCamp's 2018 New Coder Survey, granting researchers an unprecedented glimpse into how adults are learning to code.
Dataset: https://data.world/freecodecamp/new-coder-survey-2018

## Purpose of the project
Using this dataset we plan on finding interesting patterns and hidden information regarding how and why adults learn to code, on their expectations after learning to code etc. Also we want to group different categories and see for each category how they learn to code.

## Machine Learning techniques to be used:
In this project we will be using Unsupervised Learning techniques. We plan on using Clustering but during our work we might use Association if we find it fit for our project.

### Algorithms to be used
Algorithms used for clustering are: K-Means, DBSCAN.

#### K-Means
K-means algorithm was in 3 different data sets, one with missing values filled with mean, one with missing values filled with median, and one with mode.
Kmeans algorithm requires to provide the K which is number of clusters.
Many number of clusters were tested based on Elbow Method and Silhouette Coefficient, then Calinski-Harabasz Index and Davies-Bouldin index were used to evaluate each of them. 

##### Dataset with mean values

![image](https://user-images.githubusercontent.com/27426101/233844313-92c63a8a-6a17-4754-93e3-187c07d33b00.png)

Data was grouped in 9 to 15 clusters, and the evaluation for each of them was:

![image](https://user-images.githubusercontent.com/27426101/233844365-23c06269-0db6-47f1-ba1e-a8aad2695aa4.png)

##### Dataset with median values

![image](https://user-images.githubusercontent.com/27426101/233844826-3aa8ade3-9967-40cf-9ad3-2523049bdf03.png)


Data was grouped in 8 to 16 clusters, and the evaluation for each of them was:

![image](https://user-images.githubusercontent.com/27426101/233844784-c75beb83-3d8c-4936-a629-b559c57e5397.png)

##### Dataset with mode values

![image](https://user-images.githubusercontent.com/27426101/233846848-b55d3907-1e3e-402a-9568-daa16cdffb22.png)

![image](https://user-images.githubusercontent.com/27426101/233846900-3d06c997-08b1-4cea-a11b-577e6c95f472.png)


#### DBSCAN
DBSCAN diffrent than K_means does not require number of clusters, rether it requires 2 other arguments:

eps: It defines the radius of the neighborhood around a point p. A point q is said to be a neighbor of p if the distance between p and q is less than or equal to eps.

min_samples: It defines the minimum number of points required to form a dense region. A dense region is defined as a cluster of points where each point is within eps distance of at least min_samples other points in the cluster.

An additional column is added in teh dataframe named Cluster, which indicates the cluster a record is grouped on. -1 indicated the data is noise and is not part of a cluster.

An olgorithm was impelemnted to test many combiantion of these 2 paramters and find the best values for the parameters.

##### Dataset with mean values

![image](https://user-images.githubusercontent.com/27426101/233845223-e9df8a89-a1ac-481b-90c1-de3e32240357.png)

Result plotted and the ealuation:

![image](https://user-images.githubusercontent.com/27426101/233845304-3106183e-bf35-4133-9495-4ba97d965449.png)

##### Dataset with median values

![image](https://user-images.githubusercontent.com/27426101/233845365-caa54162-fd6a-4f1c-89a9-106e300350d2.png)

DBSCAN performed better with second dataset which had median values.

##### Dataset with mode values

![image](https://user-images.githubusercontent.com/27426101/233855393-516d5f24-93f2-4538-b3c4-d39e4c6e22fe.png)

![image](https://user-images.githubusercontent.com/27426101/233855453-185dea05-2d4a-49e5-93e6-a46a9c4f63d0.png)


#### Evaluate Accuracy 
Algorithms: Elbow Method, Silhouette Coefficient, Calinski-Harabasz Index, Davies-Bouldin index
Each of these methods were used together with clustering techniques in roder to evaluate number of clusters and quality of the clustering.

##### Silhouette Coefficient
Silhouette score is a metric used to evaluate the quality of clusters in clustering analysis. It measures how similar an object is to its own cluster compared to other clusters. The score ranges from -1 to 1, where a score closer to 1 indicates that the object is well-matched to its own cluster and poorly-matched to neighboring clusters, while a score closer to -1 indicates the opposite. A score of 0 indicates that the object is on the boundary between two clusters. Generally, higher silhouette scores indicate better-defined clusters.silhouette scores indicate better-defined clusters.

##### Elbow Method
The elbow method is a technique used to determine the optimal number of clusters in a clustering algorithm. The method involves plotting the within-cluster sum of squares (WCSS) against the number of clusters used in the algorithm. The WCSS is calculated as the sum of the squared distance between each data point and its assigned cluster centroid.
The plot of the WCSS against the number of clusters often looks like an arm, and the optimal number of clusters is usually found at the "elbow" of the plot, where the rate of decrease in WCSS starts to level off. This point represents the best trade-off between minimizing the WCSS and minimizing the number of clusters used.

##### Calinski-Harabasz Index
The Calinski-Harabasz index is a measure of how well-separated clusters are from each other. A higher value of this index indicates that the clusters are dense and well-separated.

##### Davies-Bouldin index
The Davies-Bouldin index measures the average similarity between each cluster and its most similar cluster. A lower value of this index indicates better clustering, where clusters are compact and well-separated


## Machine Learning steps
Before implementing each of the algorithms some more preprocessing was made:

### Data Preprocessing
As the first phase of our project we analyzed the dataset and the need to preprocess the data on it. 
Currently what we found that needs to be done is:
Handling Missing Data: All columns with more than 50% of missing data were deleted from the dataset.
Removing irrelevant information for our project: Deleted columns that had survey related data, which is not useful for our project.

Before data preprocessing our dataset had: Data columns (total 80 columns)
After preprocessing: Data columns (total 33 columns)

### Converting categorical data into numeric
This type of standardization was done since most of the algorithms applied, work on numeric data.
LabelEncoder class from the sklearn.preprocessing module was used to assign numerical values to categorical data.
Then the old columns with categorical data were removed from the dataframe and left only the new standardized columns.
#### Label encoding 
Is a technique that assigns a unique integer to each category in a categorical variable. For example, if you have a variable called "color" with categories "red", "green", and "blue", you could assign the values 1, 2, and 3 to these categories, respectively.

### Handling missing values, 3 approaches were tested for missing values.
1. Remove the records, this approach was used but since the number of data were reduced drastically (to 5000+ records)
2. Fill missing data with mean value, this approach was used and clustering algorithms were applied in the dataframe and teh results were evaluated againts the other method.
3. Fill missing data with median value
4. Fill missing data with mode value, this approach was applied since quite some columns were the ones standardized from categorical values so it made more sense to use mode.

### Removing some of the features 
Initially, algorithms were applied to the whole set of features in the dataset (33 features), which can be seen in How Adults Learn To Code - Algorithms - Many tries .ipynb file. But since the result was not so good, and taking into account that not all the features were important. The feature set was reduced to 11. Including only columns: 'is_software_dev','expected_earn','hours_learning','months_programming','bootcamp_attend','is_ethnic_minority','has_finance_depends','reasons_to_code_standardized','job_lctn_pref_standardized','curr_emplymnt_standardized','curr_field_standardized','last_yr_income'

### Scaling the data 
Since different features represent different things and values between features can vary a lot, an algorithm was used (scaler.fit_transform(data)) so that input features can be on the same scale and one feature to not have much mroe ipact in teh algorithm than others.

Before scaling

![image](https://user-images.githubusercontent.com/27426101/233843879-838f227d-059a-4931-a314-3606a771efef.png)

After scaling 

![image](https://user-images.githubusercontent.com/27426101/233843912-b2bf0734-df82-4934-a755-341fd769d4fa.png)

### Plotting data as 2D

The pca.fit_transform method was used to plot the data as a 2D plot, since there are 11 features we used this method to transform it in a 2D format.

# Retrain 
For the retrain changes were made: Dataset that was used had null values removed, so the records number was reduced to ~6000 records.
Also dimensionality reduction was done, out of 11 featured only 6 were used. 
Same algorithms were applied, the clustering looks much better than in the previous phase. 

![image](https://github.com/florianaB/MachineLearning-Project/assets/27426101/250c8f43-0d4f-45fe-9b0b-bfbf093aa024)

![image](https://github.com/florianaB/MachineLearning-Project/assets/27426101/8ff52701-1ce3-4f03-80e1-f72dd920c68e)

![image](https://github.com/florianaB/MachineLearning-Project/assets/27426101/1f1a2800-2f92-4dee-bc4e-4aab653b85a6)

Code for this phase is in "How Adults Learn To Code - Retraining" file
