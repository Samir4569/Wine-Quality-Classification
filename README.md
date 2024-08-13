# Wine Quality Classification: Project Overview 
* Created a tool that estimates data science salaries (MAE ~ $ 11K) to help data scientists negotiate their income when they get a job.
* Scraped over 1000 job descriptions from glassdoor using python and selenium
* Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark. 
* Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model. 
* Built a client facing API using flask 

## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn  
**For Web Framework Requirements:**    
**Kaggle Dataset:** https://www.kaggle.com/datasets/nareshbhat/wine-quality-binary-classification

## Data Preprocessing And Feature Engineering 
After getting the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	In order to get rid of null values, I created a method that fills null values with the mean of the column. 
*	Selected numerical and categorical variables. 
*	The `quality` variable was of type `int`, so I converted it into a categorical variable.
*	Encoded them based on whether they were nominal or ordinal.
*	Added the encoded data and removed the original columns.
*	Adjusted data distributions using `StandardScaler`.

  
## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/Samir4569/Wine-Quality-Classification/blob/main/assets/graph.png)
![alt text](https://github.com/Samir4569/Wine-Quality-Classification/blob/main/assets/graph2.png)

## Model Building 

I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I used accuracy_score and classification_report because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I two different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : accuracy_score =  0.8276923076923077

**Classification Report:**

|               | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|---------|
| 0             | 0.69      | 0.67   | 0.68     | 492     |
| 1             | 0.80      | 0.81   | 0.81     | 808     |
| **Accuracy**  |           |        | 0.76     | 1300    |
| **Macro Avg** | 0.74      | 0.74   | 0.74     | 1300    |
| **Weighted Avg** | 0.76   | 0.76   | 0.76     | 1300    |

*	**k-nearest neighbor**: accuracy_score =  0.76

**Classification Report:**

|               | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|---------|
| 0             | 0.80      | 0.73   | 0.76     | 492     |
| 1             | 0.84      | 0.89   | 0.87     | 808     |
| **Accuracy**  |           |        | 0.83     | 1300    |
| **Macro Avg** | 0.82      | 0.81   | 0.81     | 1300    |
| **Weighted Avg** | 0.83   | 0.83   | 0.83     | 1300    |




