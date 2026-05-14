# Drone Human Detection & Counting System
Candidate: MD Ali Hider
Role: AI/ML Internship Assessment - ANTS
Objective: Build an end-to-end computer vision pipeline to detect and count humans and cars in aerial drone imagery using the VisDrone dataset.
Project Overview
This project implements a real-time object detection system specifically optimized for drone-view perspectives. The goal is to automate the detection of pedestrians and vehicles, providing an accurate human count for B2B drone inspection and surveillance applications.
Tech Stack
Core AI: YOLOv8 (Ultralytics) - Nano version for Edge AI optimization.
Language: Python 3.x
Image Processing: OpenCV, Matplotlib
Data Management: Pandas, KaggleHub
Environment: Google Colab (T4 GPU Acceleration)
Pipeline Workflow
The system follows a structured engineering pipeline:
Dataset Analysis 
→
→
 Preprocessing 
→
→
 Model Training 
→
→
 Inference 
→
→
 Counting Logic 
→
→
 Evaluation
 Task-01: Dataset Understanding & Preprocessing
1. Dataset Analysis
I utilized the VisDrone Dataset, which contains high-resolution aerial images.
Structure: The dataset is split into Training, Validation, and Testing sets with corresponding YOLO-format .txt labels.
Target Classes: While the dataset contains 10 classes, this system is optimized for:
Humans: Aggregation of pedestrian (Class 0) and people (Class 1).
Cars: car (Class 3).
2. Preprocessing & Augmentations
To ensure the model is robust to aerial perspective shifts, I implemented the following:
Resizing: All images are resized to 
640
×
640
640×640
 pixels to balance detection accuracy and inference speed.
Normalization: Pixel values are scaled to 
[
0
,
1
]
[0,1]
.
Dynamic Augmentation: Utilizing YOLOv8's internal pipeline for Mosaic Augmentation, Horizontal Flipping, and Rotation/Scaling to prevent overfitting.
3. Engineering Challenges Identified
During the initial analysis, I identified three critical challenges:
The Small Object Problem: Due to high altitude, targets (especially humans) occupy very few pixels, increasing the risk of False Negatives.
High Aspect Ratio: Aerial images often have extreme widths, which can cause distortion during square resizing.
Class Imbalance: A higher frequency of vehicle detections compared to pedestrians in urban scenes.
4. Visualizations
(Note: I have included a /visualizations folder in this repository containing:)
Raw Data Visualization: Bounding boxes on original images to verify label accuracy.
Filtered Visualization: Demonstration of the class filter isolating only Humans and Cars.
Preprocessing Proof: A grid showing the original image 
→
→
 resized 
→
→
 flipped 
→
→
 brightness adjusted.
