# MachineLearning-Project
Project for Machine Learning subject

## Dataset related information
More than 31,000 people responded to freeCodeCamp's 2018 New Coder Survey, granting researchers an unprecedented glimpse into how adults are learning to code.
Dataset: https://data.world/freecodecamp/new-coder-survey-2018

## Purpose of the project
Using this dataset we plan on finding interesting patters and hidden information regarding on how and why adults learn to code, on their expectations after learning to code etc. Also we want to group different categories and see for each category how they learn to code.

## Machine Learning techniques to be used:
In this project we will be using Unsupervised Learning techniques. We plan on using Clustering but during our work we might use Association if we find it fit for our project.

### Algirithms to be used
We intend to use K-means algorithm for clustering

#### Evaluate Accuracy 
Algorithms: V-Measure, Silhouette Coefficient, Calinski-Harabasz Index


## Machine Learning steps

### Data Preprocesing
As the first phase of our project we analyzed the dataset and the need to preprocess the data on it. 
Currently what we found that needs to be done is:
Handling Missing Data: All columns with more than 50% of missing data were deleted from the dataset.
Removing irrelevant information for our project: Deleted columns that had survey related data, which is not useful for our project.
No data standardization was needed to be done.

Before data preprocesing our dataset had: Data columns (total 80 columns)
After preprocessing: Data columns (total 33 columns)
