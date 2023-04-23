# Machine Learning Project - How adults are learning to code
Project for Machine Learning subject

## Dataset related information
More than 31,000 people responded to freeCodeCamp's 2018 New Coder Survey, granting researchers an unprecedented glimpse into how adults are learning to code.
Dataset: https://data.world/freecodecamp/new-coder-survey-2018

## Purpose of the project
Using this dataset we plan on finding interesting patterns and hidden information regarding how and why adults learn to code, on their expectations after learning to code etc. Also we want to group different categories and see for each category how they learn to code.

## Machine Learning techniques to be used:
In this project we will be using Unsupervised Learning techniques. We plan on using Clustering but during our work we might use Association if we find it fit for our project.

### Algorithms to be used
Algorithms used for clustering are: K-Means, DBSCAN. Hierarchical Clustering.

#### K-Means

#### DBSCAN

#### Hierarchical Clustering


#### Evaluate Accuracy 
Algorithms: Elbow Method, Silhouette Coefficient, Calinski-Harabasz Index, Davies-Bouldin index
Each of these methods were used together with clustering techniques in roder to evaluate number of clusters and quality of the clustering.


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
3. Fill missing data with median value, this approach was applied since quite some columns were the ones standardized from categorical values so it made more sense to use median instead of mean.

### Removing some of the features 
Initially, algorithms were applied to the whole set of features in the dataset (33 features), which can be seen in How Adults Learn To Code - Algorithms - Many tries .ipynb file. But since the result was not so good, and taking into account that not all the features were important. The feature set was reduced to 11. Including only columns: 'is_software_dev','expected_earn','hours_learning','months_programming','bootcamp_attend','is_ethnic_minority','has_finance_depends','reasons_to_code_standardized','job_lctn_pref_standardized','curr_emplymnt_standardized','curr_field_standardized','last_yr_income'

### Scaling the data 
Since different features represent different things and values between features can vary a lot, an algorithm was used (scaler.fit_transform(data)) so that input features can be on the same scale and one feature to not have much mroe ipact in teh algorithm than others.

Before scaling

![image](https://user-images.githubusercontent.com/27426101/233843879-838f227d-059a-4931-a314-3606a771efef.png)

After scaling 

![image](https://user-images.githubusercontent.com/27426101/233843912-b2bf0734-df82-4934-a755-341fd769d4fa.png)


