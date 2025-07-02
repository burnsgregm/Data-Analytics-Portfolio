# FreeFuse Internship Project: AI/ML Pipeline for a Visual Interaction Engine

This repository contains the code and notebooks from my AI/ML internship project at FreeFuse. The primary goal of this project was to design and build the foundational data pipeline to process raw video content, generate object annotations, and deliver strategic insights for the company's next-generation Visual Interaction Engine.

The project demonstrates an end-to-end workflow, from video ingestion and preprocessing to model evaluation, data analysis, and final deliverable creation.

---

### Project Workflow & Key Components

The project was structured into several key stages, with different notebooks developed to handle each part of the pipeline.

#### 1. Video Ingestion & Preprocessing

This initial stage focused on preparing the raw video data for analysis.

* **Video Frame Extraction:** Scripts were created to process batches of source videos and extract still frames at set intervals for analysis.
* **Face Anonymization:** A standalone utility, **`Video Face Blurring v1.ipynb`**, was developed using the `insightface` library to automatically detect and blur human faces in videos, ensuring privacy and HIPAA compliance for any datasets containing people.

#### 2. Object Detection, Segmentation & Tracking

A significant portion of the project involved researching, implementing, and comparing various state-of-the-art computer vision models to find the optimal solution for object detection and instance segmentation.

* **YOLOv8 + DeepSORT (`Object Detection & Tracking v5.ipynb`):** An implementation using the powerful YOLOv8 model for instance segmentation combined with the DeepSORT algorithm for robust object tracking across multiple video frames.
* **DETR (Hugging Face Transformers) (`Image Extraction, Object Detection, & Labeling.ipynb`):** An implementation using the DETR (DEtection TRansformer) model from Hugging Face for object detection.
* **Faster R-CNN (TensorFlow Hub) (`Object Detection V4.ipynb`):** A pipeline built using Google's pre-trained Faster R-CNN model from TensorFlow Hub, which detects objects from a vocabulary of 600 classes.
* **RoboFlow API Integration (`Image Extraction, Object Detection, & Labeling - RoboFlow.ipynb`):** A workflow that leverages the RoboFlow platform for cloud-based object detection, demonstrating experience with MLOps and third-party AI services.
* **Further Model Research:** Additional experimental notebooks were created to evaluate other leading frameworks, including **Detectron2**, the **TensorFlow Object Detection API**, and **MMDetection/MMTracking**.

#### 3. Data Annotation & Visualization

To verify model outputs and prepare data for further analysis, several processes were established.

* **Structured Annotation Generation:** All detection pipelines were designed to output a standardized CSV file containing detailed object metadata, including bounding boxes, confidence scores, and class names, based on a defined schema.
* **Visual Verification (`Label Stills` & `Image Detection and Visualization Script.ipynb`):** Scripts were developed to automatically draw the predicted bounding boxes and segmentation masks directly onto the extracted still images, providing a clear visual record of the models' performance.

#### 4. Strategic Analysis & Insight Generation

The final stage of the pipeline focused on translating raw detections into actionable business intelligence.

* **Taxonomy Mapping (`Object Detection V4.ipynb`):** A comprehensive taxonomy was created to map over 600 granular object classes from the Open Images V4 model into a manageable set of high-level categories (e.g., 'electronics', 'furniture').
* **Proxy Interaction Score (`Generate Proxy Interaction Scores` notebook):** A custom, rule-based algorithm was developed to generate a proxy "interaction score" for each detected object based on factors like its category, size, and position on the screen.
* **Final Deliverable (`Generate Week 4 Deliverable` notebook):** The project culminated in the creation of an "Object Prioritization Matrix," a data visualization that plots object frequency against the mean interaction score, providing clear, data-driven recommendations for the product MVP roadmap.

---

### Technologies & Libraries Used

* **Programming Language:** Python
* **Core Data Science Libraries:** Pandas, NumPy, Matplotlib, Seaborn
* **Computer Vision:** OpenCV
* **AI / Machine Learning Frameworks:** PyTorch, TensorFlow & TensorFlow Hub, Hugging Face Transformers
* **Object Detection/Segmentation Models:** YOLOv8, DETR, Faster R-CNN, Detectron2, MMDetection
* **Object Tracking:** DeepSORT
* **Facial Recognition:** insightface, onnxruntime
* **MLOps / Third-Party Services:** RoboFlow API
