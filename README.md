
# Lab description

## Objective
The objective of this lab is to learn how to use a feature store to build a serverless AI system that predicts air quality for a location.

The lab is divided into 4 different notebooks which implement the air quality prediction service.

## Notebook 1: Air quality feature backfill
The first notebook is responsible for downloading historical weather data from a csv file, as well as  historical air quality data. The data is then registered as 2 feature groups with Hopsworks so that it can be used in the training pipeline.

The reason for using feature groups is to store the data in a way that it can be easily reused over many models, and that it makes the project more structured and easier to understand, debug, and maintain.

## Notebook 2: Air quality feature pipeline
The second notebook is responsible for downloading yesterday’s weather data and air quality data, as well as the weather prediction for the next 7-10 days. The data is then updated in the feature groups in Hopsworks so that it can be used in the training pipeline.


## Notebook 3: Air quality training pipeline
The third notebook is responsible for selecting the features for use in a feature view, reading the training data with the feature view, training an XGBoost regression model based to predict air quality (pm25), and registering the model with Hopsworks.

The features that are used in the model are the weather features (e.g. percepitation, temperature, wind speed, etc.) and the air quality from previous days (since particles in the air can take some time to settle) that were stored in the feature groups in the previous notebooks.


## Notebook 4: Air quality batch inference pipeline
The fourth notebook is responsible for creating a dashboard that predicts the air quality for the next 7-10 days. The program downloads the model from Hopsworks and plots a dashboard that shows the predictions of the air quality for the next few days. The dashboard is used to monitor the accuracy of the predictions by plotting a hindcast graph showing the predictions vs outcomes (measured air quality).


## Dashboard
https://isaknordg.github.io/ID2223-SML/air-quality/

The dashboard shows the predictions of the air quality for the next 7-10 days. The predictions are uploaded every morning by a GitHub action that runs Air Quality Feature and Air Quality Batch Inference notebooks. The dashboard is updated with the new predictions every day.

## Aimed grade
The aimed grade for this lab is A, as the dashboard is up and running and the predictions are uploaded every day. The predictions are also based on the lagged air quality for the previous 3 days, which is a feature that was added to the model.
