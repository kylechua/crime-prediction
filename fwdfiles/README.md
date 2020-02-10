## cluster_functions.py

Contains primary functions and their helpers for computing clusters.  This includes the functions necessary to perform dilations, compute collisions, and organize crime data in a data frame.

## forecast_LSTM.py

Contains the functions to load a LSTM (Long Short-term Memory) model, make a prediction based on ingested data, and then plot the prediction.

## general_functions.py

Contains general functions needed for computations including finding the Haversine distance between two points, finding area based on latitudes and longitudes.  Also contains functions to manage information such as paramters, predictions, and time series.

## forecast_ARIMA.py

Computes predictions based on an ARIMA (Autoregressive Integrated Moving Average) model, then stores the prediction.

## forecast_MM.py

Computes predictions based on an MM (Moving Mean) model, then stores the prediciton.  Also contains the functionality for dynamic Moving Average predictions over a range of data.

## resourceAllocation_functions.py

Contains various functions for evaluating a prediction and assigning resources accordingly.  This includes functionalty for computing relative stopped crime given a fixed amount of available resources.