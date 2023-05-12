# CloudPhysician: The Vital Extraction Challenge

This repository contains the solution for the "CloudPhysician: The Vital Extraction Challenge" as part of the Inter IIT Tech Meet.

## Problem Statement
The objective of this challenge is to extract vital data such as Heart Rate, SPO2, RR, SBP, DBP, and MAP from the monitor screen of patients. The problem is divided into three main tasks: monitor screen extraction, feature extraction, and text recognition. We were provided with three types of datasets: Monitor Dataset, Classification Dataset, and Unlabelled Dataset.

#### Monitor Dataset
The Monitor Dataset consists of 2000 images along with the coordinates of the monitor screens. The task is to accurately detect the screen from the given image using the Yolov7 object detection framework. This forms the basis for the next stage of the pipeline.

#### Classification Dataset
The Classification Dataset consists of four folders, each containing 250 images, and four data files with coordinates for features. The goal is to perform object detection using the Yolov7 model to extract bounding box coordinates and confidence scores for each feature on the screen. Additionally, text recognition techniques such as EasyOCR are applied to extract vital information from the feature images. The graph features on the monitor are also digitized using k-means clustering, thresholding, masking, and DBSCAN clustering.

#### Unlabelled Dataset
The Unlabelled Dataset consists of 7000 images of monitors without any coordinates for screen or features. The task is to extract vital data from these images using the models trained on the other datasets.

## Pipeline
The solution to this problem involves a pipeline consisting of two models and additional steps for text recognition and graph digitization.

#### 1. Model M1 - Monitor Screen Extraction
Model M1 is trained on 1800 monitor images with corresponding coordinates. It utilizes the Yolov7 object detection framework to accurately detect the screen from the given image. The output of this model is a tensor containing bounding box coordinates and confidence scores.

#### 2. Model M2 - Feature Extraction
Model M2 is trained on 800 images with label files containing coordinates for bounding boxes. It also uses the Yolov7 model for object detection. The output of this model is a tensor containing bounding box coordinates and confidence scores for each feature on the screen. Text recognition techniques, specifically EasyOCR, are then applied to extract vital information from the cropped feature images. Graph digitization techniques, including k-means clustering, thresholding, masking, and DBSCAN clustering, are used to extract insights from the graphs on the monitor.

#### 3. Text Recognition
Based on the dataframe containing bounding box coordinates, feature images are cropped and text is extracted using EasyOCR. Non-numeric characters are removed from the predicted values for vitals using string cleaning techniques.

#### 4. Graph Digitization
Insights from the graph features on the monitor are obtained using techniques such as k-means clustering, thresholding, masking, and DBSCAN clustering.

## Results:
The solution achieves the following results:

#### 1. Inference Time: 
The pipeline, including preprocessing for images, feature extraction, and prediction, has a total inference time of approximately 3.5 seconds. The solution was implemented and tested on Google Colab Notebooks.

#### 2. Model M1: 
The monitor screen extraction model achieves an F1 score approaching 1 at a confidence threshold of 0.912.

#### 3. Model M2: 
The feature extraction model achieves an F1 score of about 0.93 at a confidence threshold of 0.702.




For more details, please refer to the Code and the Report in this repository.
