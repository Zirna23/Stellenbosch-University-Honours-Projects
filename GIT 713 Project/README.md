# Fire Danger Index Project - Jonkershoek Nature Reserve

This repository contains the complete workflow and outputs for a machine learning-based Fire Danger Index (FDI) prediction system developed for the Jonkershoek Nature Reserve in South Africa. The project uses Random Forest, XGBoost, and Support Vector Machine models to predict wildfire risk based on environmental, climatic, and satellite-derived data.

## Project Overview

The study developed predictive models using historical fire data (2015-2023) combined with weather variables, topographic features, and vegetation indices to create fire danger maps. The Random Forest model was selected as the final implementation due to its robust performance.

## Folder Structure

### 01. Raw Data
Contains the original, unprocessed datasets used in the analysis:
- **Jonkershoek shapefile**: Study area boundary vector data for the Nature Reserve
- **DEM**: Digital Elevation Model raster data for topographic analysis
- **Fire data**: Historical fire occurrence points and locations
- **ARC weather data**: Swartboskloof weather station data including rainfall, temperature, humidity, and windspeed measurements

### 02. Processed Data
Contains cleaned and preprocessed datasets ready for machine learning:
- **NDVI rasters**: Processed vegetation index data from satellite imagery
- **Random non-fire and fire points**: Balanced point datasets for model training
- **Slope rasters**: Derived topographic slope data from DEM
- **Training dataset**: Combined fire/non-fire dataset with environmental variables
- **Weather data**: Processed meteorological data aligned with fire occurrence dates

### 03. Scripts and Code
Contains all analysis code and processing scripts:
- **Machine learning models**: Python code for Random Forest, XGBoost, and SVM implementations
- **Raster alignment code**: Scripts for spatial data alignment and coordinate system standardization
- **Interpolation and resampling code**: Processing routines for raster data harmonization
- **Data wrangling code**: Data cleaning, preprocessing, and feature extraction scripts

### 04. Results
Contains model outputs and performance assessments:
- **Fire danger maps**: Spatial fire risk predictions from all 3 different models (Random Forest, XGBoost, SVM)

### 05. Metadata
Contains documentation and data descriptions:
- **Dataset specifications**: Source, resolution, temporal coverage, and format details
- **Coordinate system information**: Spatial reference system documentation
- **Data acquisition dates**: Temporal metadata for all input datasets
- **Processing parameters**: Model hyperparameters and configuration settings

### 06. Output Map(s)
Contains the final fire danger prediction maps and analysis:
- **Time-series models**: Temporal analysis and visualization of environmental variables
- **Random Forest FDI maps**: Fire Danger Index maps showing no fire, people-caused fire areas
- **Risk visualization outputs**: Spatial fire danger predictions and probability surfaces

### 07. Project Management
Contains project documentation and reports:
- **Gantt chart**: Project timeline and milestone tracking
- **Project outline**: Initial project scope and planning documents
- **Project reports**: Complete collection including data wrangling, metadata, scoping, and final product reports
- **Presentation materials**: Project slides, group logo, and presentation template

### 08. Back-ups
Contains archived versions and backup files:
- **Previous versions**: Earlier iterations of code, documents, and images that were modified or removed during project development
- **Version control**: Historical snapshots of project files for recovery and reference

## How to Run the Python Models

To train and run the machine learning models, you will need the following input data:

### Required Raster Inputs:
- **Slope raster**: Topographic slope data derived from DEM
- **Elevation raster**: Digital elevation model for the study area
- **NDVI raster**: Normalized Difference Vegetation Index data

### Required Weather Data:
- **Max temperature**: Day-specific maximum temperature values
- **Max and Min Humidity**: Day-specific humidity measurements  
- **Daily and Monthly Rainfall**: Precipitation data
- **Windspeed**: Day-specific wind measurements

### Required Boundary Data:
- **Study area raster**: Raster defining the study area

### Setup Instructions:

1. **Configure raster paths**: In the main function of the Python code, update the following variables with your specific file paths:
  ```python
  ndvi_raster = "path/to/your/ndvi/raster"
  res_raster = "path/to/raster/with/finest/resolution" 
  size_raster = "path/to/study/area/boundary/raster"

Prepare training data: Ensure the cleaned fire dataset Excel document is placed in the same folder as the Python script. This file can be found in the training dataset folder under 02. Processed Data.

Run the model: Execute the Python script to train the models and generate fire danger predictions.

The code will process the input rasters, align spatial data, and train the Random Forest, XGBoost, and SVM models using the prepared training dataset.
