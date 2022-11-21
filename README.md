# Ecs171Final
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

## Observations on our data
*  We have 768 patient observations
*  By running the shapiro wilk test we can observe that all of our data is most likely not normally distributed
*  We will pre process our data using the min max scaler as this method is the most efficient since all of our data is not normally distributed


[link to Jupyter Notebook](./diabetes.ipynb).