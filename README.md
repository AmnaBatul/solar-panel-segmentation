# Solar Panel Segmentation with U-Net (EfficentNet Backbone)

This project aims to perform binary segmentation of photovoltaic (PV) panels in aerial imagery using a U-Net architecture with an EfficientNet encoder. The goal is to accurately distinguish solar panels from the background, enabling further analysis like panel counting, area estimation, and solar farm monitoring.

## Implementation Details:

### Dataset
This implementation was performed on a [photovoltaic (PV) dataset from satellite and aerial imagery](https://www.kaggle.com/datasets/salimhammadi07/solar-panel-detection-and-identification). 

### Architecture
The U-Net architecture is used for semantic segmentation, with encoder EfficientNet-B0 pretrained on ImageNet. The model outputs a binary mask for each input image, classifying each pixel as panel or background.

### Preprocessing
All input images and masks are resized to 256x256. Data augmentations such as horizontal/vertical flips, random rotations, and brightness/contrast adjustments are applied during training using Albumentations.

### Training Details
- Loss: Dice + BCEWithLogits
- Optimizer: Adam (lr=1e-4)
- Batch Size: 8
- Epochs: 40 (with early stopping)
- Split: 80% Train, 10% Val, 10% Test

### Evaluation Metrics
The model is evaluated using:
- Precision
- Recall
- F1-Score
- Accuracy
- Confusion Matrix

## Results:
Classification Report:
              precision    recall  f1-score   support

           0     0.9852    0.9858    0.9855  22284202
           1     0.9604    0.9588    0.9596   7993430

    accuracy                         0.9787  30277632
   macro avg     0.9728    0.9723    0.9726  30277632
weighted avg     0.9787    0.9787    0.9787  30277632

