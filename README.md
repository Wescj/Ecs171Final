# Ecs171Final 
## Group members: Wesley Judy, Yingchen Gu, Andrew Song, YingYu Gu
https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset?resource=download

## Collaboration

Yingyu Gu: All-rounder
* Participated in coding portion
* Participated in final write-up
* Discussed with members about when to meet up 

Yingchen Gu: All-rounder
* Participated in coding portion
* Participated in final write-up
* Discussed with members about when to meet up

Wesley Judy: All-rounder
* Participated in coding portion
* Participated in final write-up
* Discussed with members about when to meet up

Andrew Song: All-rounder
* Participated in coding portion
* Participated in final write-up
* Discussed with members about when to meet up

We all worked as a team to complete the assignment. Although we didn't really have a team leader, we discussed possible ideas for our project and organized a timeline for the milestones and meetups. We managed our project by dividing some parts and talking about how we could analyze our dataset. All of us took part in writing parts of the code and in the write-up.

## Dataset Attributes Information:
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
### Observations on our data
*  We have 768 patient observations
*  By running the shapiro wilk test we can observe that all of our data is most likely not normally distributed
*  We will pre process our data using the min max scaler as this method is the most efficient since all of our data is not normally distributed
## Methods
### Data Exploration
Before talking about the methods, we first ran the Shapiro-Wilk test on the dataset with every column. We continued to explore the dataset by creating a heatmap to see the correlations of each attributes. 

Heatmap:

![Alt text](https://cdn.discordapp.com/attachments/272048987295580171/1049107942009491537/image.png)

### Preprocessing
We used a MinMaxScaler method to transform our data after checking for possible NULL values. Then we worked to expand the features using polynomial transformation and trained the model.

### Model 1 (Logistic Regression)
For model 1 we trained our model with a ratio of 80:20 using Logistic Regression and predicted the "Outcome" (probability of having diabetes)
```
train, test = train_test_split(scaledData, test_size=0.2, random_state=21)
X_train, y_train = train.drop(['Outcome'], axis = 1), train['Outcome']
X_test, y_test = test.drop(['Outcome'], axis = 1), test['Outcome']

#Logistic Regression Model
training_model = LogisticRegression(solver='liblinear', random_state=2)
training_model.fit(X_train, y_train)
print("Logistic Regression")
print("---------------- Training Data ----------------")
print(classification_report(y_train, training_model.predict(X_train)), '\n')
print("---------------- Testing Data ----------------")
print(classification_report(y_test, training_model.predict(X_test)), '\n')
```
### Model 2 (Gaussian NB)
The second model was created using the Gaussian Na??ve Bayes. We also trained our model with a ratio of 80:20 and predicted the "Outcome" (probability of having diabetes)

```
#We used the same scaled data from the previous step
NB = GaussianNB()
NB.fit(X_train, y_train)
print("Gaussian NB")
print("---------------- Training Data ----------------")
print(classification_report(y_train, NB.predict(X_train)))
print("---------------- Testing Data ----------------")
print(classification_report(y_test, NB.predict(X_test)))
```

## Discussion
### Thought Process
One of the first steps we took when doing data exploration was to run the Shapiro-Wilk test because this can tell us whether the data is normalized. By determining this, we can proceed with the MinMaxScaler or the StandardScaler depending on the results. As you can see, we found that our data was not normally distributed. Thus, we decided to use the MinMaxScaler to scale our data since StandardScaler is usually used on normalized data. Along with the Shapiro-Wilk test, we created several graphs to show the count distribution (number of people) of each attributes. These bar graphs tell us the spread of our data, so we have a better visualization of what we are working with. Furthermore, we created scatterplots and a heatmap to see the correlation between the attributes and the outcome. The heatmap reveals how correlated the attributes are. The scatterplot is also color coded so that we can see whether the patient has Diabetes or not, while also seeing how the attributes (i.e. Age, Glucose) are correlated to each other and the outcome. 
For our data preprocessing we chose the Min Max Scaler as we found from our shapiro-wilk tests that our data is most likely not normally distributed. We also checked for any missing or NULL values to avoid any issues. We chose not to encode our data as we have no fields that needed encoding as every single field was a numeric value. Thus there was no real reason to encode our data. To increase the scope of our data set we also added a polynomial transformation for every field except for the ???Outcome??? field.
Afterwards, we decided to use Logistic Regression and Gaussian Naive Bayes Classification to model our dataset. We chose Logistic because our dataset is categorical and we can use it to predict the probability of someone having diabetes using the included attributes. We chose the Gaussian naive bayes classification as our second model because it's a probabilistic classification algorithm that can be used to compute probability of likelihood when features are assumed to have normal distribution.

### Shortcomings
Some shortcomings of our analysis include the fitting of the graphs and the errors from the prediction. Looking at our graph, we can see that the logistic regression graph goes down in error as the dataset increases. This tells us that our model does better when more data is being fed to it. However if we look at the Gaussian Naive Bayes model, we see that our test error and and train error seems to be slighting increasing. Though for our current dataset, we can see that both models about about a 70% average accuracy and precision, this may not be the case with more data. Changing the ratio of the test and train set might also affect the accuracy of our model, which is something that we believe could be worked on for better results. 

## Conclusion
One approach we could've tried is to see which 2 aspects are one of the defining reasons that lead to diabetes. Looking at some of the graphs we plotted, we believed that glucose and blood pressure might be one of the main factors. We can also test to see if the two we chose is one of the defining reasons by removing it and seeing if that will make a more negative correlation in our data. Another area we could've improved is to adjust the training and testing ratios to see if it affected the results positively or negatively. Our accuracy for the probability of diabetes is already at 73%, which is fairly reasonable to warn people about their health. With more data, our accuracy will most likely increase and give people a better prediction that will help them get the help they need.

## Results
During our preprocessing stage, we found zero missing values and found that our data was most likely not normally distributed using the shapiro-wilk test. Thus we chose the MinMax Scaling method to scale our data before training.

Our Logistic Regression Model and Gaussian NB Model performed very similarly, with both having an average accuracy of 73% on the testing data. On the other hand, the Logistic Regression Model was slightly more accurate on the training data with an accuracy of 79% compared to the Gaussian NB Model???s 76% accuracy (shown below in classification report). However, if we look at the fitting graphs for the two models we can see that they performed very differently as the size of the data set increased.

![Alt text](https://cdn.discordapp.com/attachments/272048987295580171/1049142649094934608/image.png) ![Alt text](https://cdn.discordapp.com/attachments/272048987295580171/1049142621806805032/image.png)

### Classification Report

```
Logistic Regression
---------------- Training Data ----------------
              precision    recall  f1-score   support

           0       0.79      0.92      0.85       406
           1       0.77      0.53      0.63       208

    accuracy                           0.79       614
   macro avg       0.78      0.73      0.74       614
weighted avg       0.79      0.79      0.78       614
 

---------------- Testing Data ----------------
              precision    recall  f1-score   support

           0       0.73      0.89      0.80        94
           1       0.74      0.48      0.59        60

    accuracy                           0.73       154
   macro avg       0.74      0.69      0.69       154
weighted avg       0.74      0.73      0.72       154
```

```
Gaussian NB 
---------------- Training Data ----------------
              precision    recall  f1-score   support

           0       0.80      0.84      0.82       406
           1       0.65      0.59      0.62       208

    accuracy                           0.76       614
   macro avg       0.73      0.72      0.72       614
weighted avg       0.75      0.76      0.75       614

---------------- Testing Data ----------------
              precision    recall  f1-score   support

           0       0.75      0.84      0.79        94
           1       0.69      0.57      0.62        60

    accuracy                           0.73       154
   macro avg       0.72      0.70      0.71       154
weighted avg       0.73      0.73      0.73       154
```



[link to Jupyter Notebook](./diabetes.ipynb).
