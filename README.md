# Histopathology-Thyroid-Cancer-Detection-A-Triple-Class-YOLO26-Approach

**Overview**

In this study, we explore the use of a deep learning model, YOLO26, to detect thyroid cancer as well as abnormal tissue in histopathological images. The Model achieved moderate overall performance (mAP50 = 0.497, recall = 0.534), with strong detection of abnormal tissue (mAP50 = 0.684, recall = 0.742). 

This project evaluates the effectiveness of YOLO26 for detetcing and localizing thyroid cancer tissue in histopathology images. The goal was to investigate whether deep learning could support clinicians by improving diagnostic efficiency and identifying abnormal tissue regions for further review.

**Project Goals**

Our goals for this study included:
1) Evaulate YOLO26's ability to detect thyroid cancer and abnormal tissue in histopathological images
2) Explore whether AI-assisted image anyalysis can support thyroid cancer diagnosis and reduce clinican workload

**Dataset**

The dataset used in this project comes from the [Roboflow Univerese repository](https://universe.roboflow.com/thesis-yczhj/thyroid-cancer-detection-j8r8b) and contains 533 annotated histopathology images of thyroid tissue with bounding box annotated histopathology images of thyroid tissue with bounding box annotations for object detection tasks.

The original dataset contained 9 classes:
- TC (thyroid cancer)
- Abnormal
- Fibrocollagenous Tissue
- Fibromuscular Tissue
- Inflamitory Cell
- Lymphoid
- Normal
- RBC (red blood cells)
- Stroma
To address class imbalance and improve model performance, biologically similar classes were merged into a simplified triple-class dataset.

Final classes included:
- TC = Malignant thyroid tissue
- Normal = Healthy thyroid tissue
- Abnormal = Non-cancerous but atypical tissue including inflammatory and fibrous components

The dataset was split:
- Training: 364 images
- Validation: 117 images
- Testing: 52 images

**Methods**

This project used YOLO26, the newest version in the YOLO model series, for object detection on thyroid histopathological images.

YOLO26 was selected because of:
- Fast inference speed
- Real-time object detection capability
- Strong perfromance on image localization tasks
- Improved efficiency compared to earlier YOLO versions

**Data Preprocessing**

To determine the best classification structure, the mdoel was traine dunder several configuarations:
1) 9-class model
2) 5-class merged model
3) Binary model (TC vs Normal)
4) Triple-class model (TC, Abnormal, Normal)

The triple-class configuration produced the best overall detection performance and became the final model used in this study.

**Data Agumnetation**

Data augmentation strategies were applied to improve model generalization and reduce class imbalance. These stategies included standard agumentations and mixed scene augmentation.

**Hyperparameter Tuning**

YOLO's built-in turning framework was used with:
- AdamW optimizer
- Cosine learning rate decay
- 20 tuning iterations
- Label smoothing
- Mosaic augmentation
- Rotation augmentation

**Results**

**Final Triple-Class Model Performance**

| Metric | Score |
| ------ | ----- |
| mAP50  | 0.497 |
| Recall | 0.534 |
| Precision|0.473 |
| mAP50-95 | 0.194|

**Class Performance**

|Class|Percision|Recall|mAP50|
|-----|---------|------|-----|
|TC|0.346|0.387|0.343|
|Abnormal|0.684|0.742|0.684|
|Normal|0.558|0.472|Moderate|

The model performed best on the **Abnormal** class but struggled with reliable thyroid cancer detection due to severe class imbalance and limited TC samples.

**Key Findings**

- YOLO26 shoed strong potential for detecting abnormal thyroid tissue
- Thyroid cancer detection performance remained limited
- Dataset imbalance significantly affected TC accuracy
- AI-based pathology tools may be useful as **pre-screenign assistants** rather than standalone diagnostic systems

**Limitations**

- Small satset size
- Severe class imbalance
- Limited thyroid cancer samples
- Inconsistent image magnification across classes
- Moderate overall accuracy (~50%)

Because of these limitations, the model is **not suitable for standalone clinical diagnosis**

**Conclusion**

YOLO26 demonstrates potential as a supportive AI tool for thyroid histopathology analysis. While the model is not accurate enough to replace pathologists, it may help:
- Identify abnormal tissue regions
- Prioritize cases for review
- Improve workflow efficiency in clinical settings

Future work should focus on:
- Expanding labled thyroid cancer datasets
- Improving class balance
- Training on larger histopathological datsets
- Fine-tuning on thyroid-specific data
