# A crime prediction tool based on Heterogeneous Clustering and an original evaluation metric

![sample-result](sample-result.png)

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)


## Introduction

This tool implements a crime prediction algorithm in a geological space using heterogeneous clustering and an evaluation metric. The algorithm and the metric is proposed by the Data Science Lab at USC (http://dslab.usc.edu/).


## Getting Started

1. Install [Python]()
2. Install [Jupyter Notebook](http://jupyter.org/install) (only if you want to visualize the results)
3. Install all the packages listed in packages.txt. If you have [pip](https://pypi.org/project/pip/) installed, you could run `pip install -r packages.txt` to install all the packages.
4. Edit config.py for parameter settings:
    
    `ignoreFirst` - int: Minimum amount of training periods

    `periodsAhead_list` - List of ints: Periods ahead to forecast

    `ug_gridshapes` - List of tuples: # of cells along latitude & longitude (for uniform grid method)

    `ug_maxDist` - Leave at 0 (for uniform grid method)

    `ug_threshold` - Leave at 0 (for uniform grid method)

    `ug_methods` - List of str: Any of ["mm", "ar", "harmonic]. Forecasting algorithms to use (for uniform grid method)

    `c_gridshape` - Tuple: # of cells along latitude & longitude (for cluster method)

    `c_thresholds` - int: Threshold of clustering (for cluster method)

    `c_maxDist` - int: Neighborhood distance of clustering (for cluster method)

    `c_methods` - List of str: Any of ["mm", "ar", "harmonic]. Forecasting algorithms to use (for cluster method)

    `resource_indexes` - List of int: List of amount of  resources to use for evaluation (RA calculation)

    `cell_coverage_units` - int: Number of resources needed to cover each cell (RA calculation)

5. Sample usage for forecasting & evaluation (using `LAdata.pkl`):

    ```
    python parse_data.py DPSdata.pkl DPSUSC.pkl
    python make_predictions.py LAdata.pkl
    python calculate_resource_allocation.py
    python plot_allocations.py
    ````

# Per-File Developer Docs

## aggregate_plots.py

Contains functionality for aggregating the various plots produced by different prediction algorithms, and saves them to one mathplotlib figure.

## fwdfiles folder

Contains the backend code for making predictions, separated by algorithm.

## plot_allocations.py

Contains the code to plot resource allocations based on crimes avoided.  Uses results from calculate_resource_allocation.py in the results directory.

## calculate_resource_allocation.py

Calculates resource allocation based on chosen method, prediction model, and places results in the results directory.  Uses functions defined in fwdfiles/resourceAllocation_functions.py.

## make_predictions.py

Forms predictions based on the functions in fwdfiles directory (forecast_LSTM.py, forecast_ARIMA.py etc.).  Manages the choice of prediction method.

## plot_predictions.py

Plots predictions made in make_predictions.  Separates code according to grid based vs. cluster based.

## config.py

Stores the settings as variables for prediction method, grid vs. cluster, etc.

## plotPredictions.py

Duplicates plot_predictions,py

## parse_data.py

Parses data stored in a csv and saves them in pickle format.