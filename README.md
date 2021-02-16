# Machine-Learning
Machine Learning- Exoplanet Exploration

![exponants](Images/exoplanets.jpg)

## Table of contents
* [Exoplanet Exploration](#exoplanet-exploration)
* [Technologies](#technologies)
* [EDA](#eda)
* [Models](#models)
* [Accuracy](#accuracy)
* [Resources](#resources)
* [Contact](#contact)

## Exoplanet Exploration

Over a period of nine years in deep space, the NASA Kepler space telescope has been on a planet-hunting mission to discover hidden planets outside of our solar system. To help process this data, I have created a machine learning model capable of classifying candidate exoplanets from the raw dataset.

## Technologies
* Machine Learning 
* Jupyter Notebook / Pandas
* SkLearn

## EDA

Exploratory Data Analysis & data cleaning

I imported the [exponent data](https://github.com/RutgersCodingBootcamp/RUT-SOM-DATA-PT-09-2020-U-C/blob/master/02-Homework/21-Machine-Learning/Instructions/starter_code/exoplanet_data.csv) into a jupyter notebook to clean and test the data. After importing the data, I needed to refer to the [Data Dictionary](https://exoplanetarchive.ipac.caltech.edu/docs/API_kepcandidate_columns.html) from NASA to understand the column meanings and what data I needed for my machine learning models.

I printed the column names to find that ½ of the column data was “margin of error” denoted by “err” in the name. I removed these columns by using the function `.drop(columns )` . 

![clean columns](Images/clean_columns.JPG)

Then I used ` df.info() ` to view the data type. From this view, I could see that all data was in integer/float form except for ‘koi_disposition’ which was an object. I dropped it for my X value: `X = df.drop(columns=["koi_disposition"])`

![df info](Images/df_info.JPG)

I then used a `RandomForestClassifier` to see the importance of the balance of the columns to see what was needed for the models. 

![random forest](Images/random_forest.JPG)

I decided to keep columns with an importance value of higher than 0.04. This left 8 columns of important data to fit in my model. 

I performed a test/split on my data. 

![test split](Images/test_split.JPG)

Then I scaled the data using a `StandardScaler()` 

![scaler](Images/scaler.JPG)

## Models

My first model is a Neural Network. First, I `one-hot` coded the data into categorical data.

![one-hot](Images/one_hot.JPG) 

I used `from tensorflow.keras.layers import Dense` to create the model and added 8 inputs, 10 hidden layers and 3 outputs for Candidate, False Positive & Confirmed. 

![model 1](Images/model1.JPG)

I then fit the train model. 

![model 1.2](Images/model1_2.JPG)

For my second model, I used a `GridSearchSCV`.  I tested a linear and rbf kernel: `'kernel': ('linear', 'rbf')}` . I then fit the model. 

![model2](Images/model2.JPG)

## Accuracy 

The Neural Network is a more accurate network with a accuracy rating of 88%. The Grid Search model is slightly less accurate with a rating of 80%. 

Model 1 Neural Network

![model1 accuracy](Images/model1_accuracy.JPG)

Model 2- Grid Search

![model2 accuracy](Images/model2_accuracy.JPG)

## Resources

[Exponent Data](https://github.com/RutgersCodingBootcamp/RUT-SOM-DATA-PT-09-2020-U-C/blob/master/02-Homework/21-Machine-Learning/Instructions/starter_code/exoplanet_data.csv)

[NASA Data Dictionary](https://exoplanetarchive.ipac.caltech.edu/docs/API_kepcandidate_columns.html)

## Contact

[Sara Simoes](https://github.com/Ssimoes48)
