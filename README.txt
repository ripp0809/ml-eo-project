# Land Cover Classification with Sentinel-2

## Overview

This repository contains a machine learning pipeline for land cover classification using Sentinel-2 satellite data and CORINE Land Cover labels.

The goal of this project is to build a complete workflow from raw satellite data to a trained model and to analyze how class imbalance affects the performance of the model.

The project was developed as part of a course on machine learning for Earth observation.

-----------------------------------------

## Repository Structure

The repository contains the following main notebooks:

- Data_preperation.ipynb  
  Used to preprocess the data, align Sentinel-2 with CORINE labels, and create the dataset.

- base_pipeline.ipynb  
  A simple CNN baseline model used as a first reference.

- PipelinePyTorch.ipynb  
  The main pipeline using PyTorch Lightning. This is the model used for the final results.

- TerraTorch_finetuning.ipynb  
  Additional experiment with larger input patches (224x224). This was tested but not used for the final results.

------------------------------------------

## Pipeline Description

The workflow is structured as follows:

1. Data preprocessing  
   Sentinel-2 data is aligned with CORINE Land Cover labels and relevant spectral bands are selected.

2. Dataset creation  
   Small image patches (3x3 pixels) are extracted and assigned a label based on the dominant class.

3. Model training  
   A convolutional neural network (CNN) is trained to classify the patches.

4. Handling class imbalance  
   Different strategies are tested:
   - random sampling  
   - weighted sampling  
   - class-weighted loss  

5. Evaluation  
   The models are evaluated using accuracy, balanced accuracy and macro-F1 score, as well as confusion matrices.

------------------------------------------

## How to Run

1. Open the data preparation notebook:
   - Data_preperation.ipynb

2. Set the correct paths to your dataset (Sentinel-2 and CORINE data).

3. Run all cells to generate the dataset.

4. Open the main pipeline:
   - PipelinePyTorch.ipynb

5. Run all cells to train and evaluate the model.

The baseline pipeline (base_pipeline.ipynb) can also be run for comparison.

----------------------------------------------

## Dataset

The dataset is not included in this repository because of its size.

The pipeline expects:
- Sentinel-2 data (bands B02, B03, B04, B08)
- CORINE Land Cover labels

Make sure to update the paths in the notebooks before running the code.

----------------------------------------------

## Results

The following strategies were compared:

- Random sampling  
- Weighted sampling  
- Class-weighted loss  

The results show that random sampling gives the highest accuracy, but performs poorly on minority classes.

Weighted sampling improves the performance across classes but reduces overall accuracy.

Class-weighted loss provides a compromise between both approaches.

----------------------------------------------

## Notes

- GPU is recommended but not required  
- Results may vary slightly due to randomness  
- The 224x224 experiment was not used for the final analysis because the results were unstable  

----------------------------------------------

## Author

Lukas Ripp