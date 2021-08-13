# Predictive anaysis using breast cancer data 
In this kernel, I will walk you through analyzing the dataset from the  University of Wisconsin, which has 569 instances (rows = samples) and 32 attributes (features = columns), building the model, and finally evaluating it. This project aims to train a classifier model on the cancer cells characteristics dataset to predict whether the cell is B = benign or M = malignant.

# About dataset
Data Set Attribute Information:
1) Id number
2) Diagnosis (M = malignant, B = benign)
3) till 32) Ten real-valued features are computed for each cell nucleus:

a) radius (mean of distances from center to points on the perimeter)
b) texture (standard deviation of gray-scale values)
c) perimeter
d) area
e) smoothness (local variation in radius lengths)
f) compactness (perimeter^2 / area - 1.0)
g) concavity (severity of concave portions of the contour)
h) concave points (number of concave portions of the contour)
i) symmetry
j) fractal dimension ("coastline approximation" - 1)

“The mean, standard error, and “worst” or largest (mean of the three largest values) of these features were computed for each image, resulting in 30 features. For instance, field 3 is Mean Radius, field 13 is Radius SE, field 23 is Worst Radius.”

Python Version: 3.7
Packages: pandas, numpy, sklearn, matplotlib, seaborn, selenium, flask, json, pickle
For Web Framework Requirements: pip install -r requirements.txt
Enviroment: Google collaboratory

# Data wrangling 
In this step, I dropped the ‘ID’ column, standard error, and worst values of each attribute to check how the classifier will perform with the central mean values.
Checked for any missing value and find out the data type to do any connversion if required

# Data exploration and visualization 
First bar plotting for the label column and view B vs. M ratio in the data set (1:11).
M= 1
B= 0

Second Histogram plotting were done to visual the data frequency and density plotting for overall data distribution. 
 ![image](https://user-images.githubusercontent.com/87844891/129323911-b234ffc0-6806-4c01-9a4b-f8dbfe8f6cbc.png)

Observations for the histogram plotted

The mean values of cell radius, perimeter, area, compactness, concavity and concave points can be used in classification of the cancer to be malignant or benign. Larger values of these parameters tends to show a correlation with malignant tumors
Next the mean values of texture, smoothness, symmetry or fractual dimension does not show a particular preference of one diagnosis over the other.
In any of the histograms there are no noticeable large outliers that warrants further cleanup.

Then, feature disturbation were done using box plot to view the normal disturbation among the variables.
![image](https://user-images.githubusercontent.com/87844891/129325191-f77f3ff1-541b-4e30-9de4-6b5d17c5319f.png)


Lastly correlation between the columns were computed to show the relationship between them
![image](https://user-images.githubusercontent.com/87844891/129325279-5def970d-248c-4326-9e48-f81fbfc13509.png)

# Data transformation for modeling
Assigned the feature columns into x and the label column ‘Diagnosis’ into y
Next, splitted 25% of the data to be my test input and output to score the classifier model later. The remaining is assigned to the training data set (X_train and y_train)
Feature scalled the x train, x test data to normalize the dataset for building modelling.

# Creating model for prediction
7 classification algorithms were on the train data and scored the model with test data to see how they perform. 
The model were evaluated with Confusion matrix, accuracy score, F1 SCORE, precision and recall score. 
The accuracy of different models as follows:

Logistic regression -94.7%

KNeighbours classfier - 94.7%

Decision tree - 94.7%

Random forest - 97.3%

Naive bayes - 94.7%

XG Boost classifier - 93.8%

ADA Boost classifier - 95.6%

Random Forest has the highest score among the other models (97.3%).

With the test dataset (20% of the test data), the Random forest classifier was able to detect 66 correct prediction (true negative) for the benign cells and 1 wrong prediction (true postive), whereas for predicting malignant cells there is 2 false negative and 45 true positives.

