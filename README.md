# Ecs171Final 
## Group members: Wesley Judy, Yingchen Gu, Andrew Song, YingYu Gu
https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset?resource=download

### Dataset Attributes Information:
* Pregnancies: The number of pregnancies  (int64)
* Glucose: Glucose level in the blood (int64)
* BloodPressure: To express the Blood pressure measurement (int64)
* SkinThickness: To express the thickness of the skin (int64)
* Insulin: To express the Insulin level in the blood (int64)
* BMI: To express the Body mass index (float64)
* DiabetesPedigreeFunction: To express the Diabetes percentage (float64)
* Age: To express the age (int64)
* Outcome: A boolean variable to indicate whether the person is diabetic (1) or not diabetic (0) (boolean)

## Introduction
The topic we chose to do our project on is Diabetes. We chose this topic because it's a chronic illness that a large population of the US suffers from. Using machine learning, we would be able to analyze larger datasets and add on to the model, making it more precise and accurate in determining whether someone has diabetes or not. Having a good predictive mode for this dataset is very important because it will help people get the treatment they need before it's too late. 

![Alt text](https://cdn.discordapp.com/attachments/272048987295580171/1049100940852072568/image.png)
![Alt text](https://cdn.discordapp.com/attachments/272048987295580171/1049100954248683591/image.png)

The above images shows scatter plots of various attributes compared to each other (Features vs. Age). The colors on the plot shows whether the patient has diabetes or not. These scatter plots show how one attribute relate to another and how this relation could correlate to diabetes. 
## Observations on our data
*  We have 768 patient observations
*  By running the shapiro wilk test we can observe that all of our data is most likely not normally distributed
*  We will pre process our data using the min max scaler as this method is the most efficient since all of our data is not normally distributed

## Methods
### Data Exploration
Before talking about the methods, we first ran the Shapiro-Wilk test on the dataset with every column. We continued to explore the dataset by creating a heatmap to see the correlations of each attributes. 
### Preprocessing
To preprocess our data, we scaled our data with the MinMaxScaler because our data was normalized. 

### Model 1
For model 1 we trained our model with a ratio of 80:20 using Logistic Regression and predicted the "Outcome" (probability of having diabetes)

### Model 2
The second model was created using the Gaussian Naïve Bayes. 

## Preprocessing & First Model Building and Evaluation Milestone
* Finish Major preprocessing
    * scaling/transforming data (We used MinMaxScaler because our data is not normally distributed)
    * imputing data (We did not find any imputed data)
    * encoding data (Since our dataset values are all numberical, we do not need to encode)
    * feature expansion (taking features and generating new features by transforming via polynomial, log multiplication of features)
* Train model
* Evaluate model (compare traning vs testing error)
The accuracy of our training and testing models are very similar with a slight bias to the training data which is reasonable. This means that it is likely our model is not underfitting or overfitting the data
* Where does it fit in the fitting graph?
Graphing the fitting graph, we can see that the feeding the model more data results in a better result for the testing error while the training error seems to stay relatively stable. Thus it is reasonable to conclude that the model is neither overfitting or underfitting.

[link to Jupyter Notebook](./diabetes.ipynb).
