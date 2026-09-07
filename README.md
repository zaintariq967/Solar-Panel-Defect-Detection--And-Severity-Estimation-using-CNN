# Solar Panel Defect Detection and Severity Estimation

Deep learning-based detection of defects in photovoltaic (PV) cells using **transfer learning** with pretrained **VGG16** and **ResNet50** architectures.

## Overview

Defects in solar panels, such as cracks, hotspots, and broken cells, can reduce power output and accelerate module degradation. Manual inspection of large solar installations is time-consuming, expensive, and prone to human error.

This project develops an automated deep learning system for **solar panel defect detection and severity estimation** using electroluminescence (EL) images. 

## Objectives

* Develop an automated binary defect classification model.
* Estimate defect severity using regression.
* Compare **VGG16** and **ResNet50** transfer learning architectures.
* Build an end-to-end pipeline for preprocessing, training, evaluation, and prediction. 

## Dataset

The project uses the **ELPV (Electroluminescence Photovoltaic) dataset**, containing:

* **2,624 grayscale images**
* Image resolution: **300 × 300 pixels**
* Mono- and polycrystalline solar cells
* Defect probability labels ranging from **0 to 1** 

## System Pipeline

```text
ELPV Dataset
     ↓
Preprocessing & Augmentation
     ↓
Transfer Learning
(VGG16 / ResNet50)
     ↓
Classification + Severity Estimation
     ↓
Evaluation & Prediction
```

The images are resized to **224 × 224** pixels and normalized by dividing pixel values by 255. 

## Preprocessing & Augmentation

The preprocessing pipeline includes:

* Image resizing to 224 × 224
* Pixel normalization
* Binary label generation
* Data augmentation

Augmentation includes:

* Rotation
* Width and height shifting
* Shearing
* Zooming
* Horizontal flipping

These transformations help improve model generalization. 

## Models

### VGG16

VGG16 pretrained on **ImageNet** is used as a feature extractor. Its original fully connected layers are removed and replaced with a custom prediction head. The pretrained layers are frozen during training. 

### ResNet50

ResNet50 pretrained on **ImageNet** is also used as a transfer learning backbone. A custom head containing global average pooling, dense layers, batch normalization, dropout, and an output layer is added for prediction. 

## Training

The models were trained using:

* **Optimizer:** Adam
* **Loss:** Binary Cross-Entropy
* **Early Stopping**
* **Transfer Learning**



## Results

| Model    | Accuracy | Precision | Recall | F1-Score |
| -------- | -------: | --------: | -----: | -------: |
| VGG16    |     0.72 |      0.74 |   0.72 |     0.70 |
| ResNet50 |     0.52 |      0.62 |   0.52 |     0.48 |

VGG16 achieved the better overall classification performance on the ELPV dataset. The report gives approximately **71.8% accuracy for VGG16** compared with **52.1% for ResNet50**.  

## Prediction

The trained system can evaluate unseen electroluminescence images and provide:

* Functional / defective classification
* Prediction confidence
* Estimated defect severity

The project includes a prediction pipeline for loading an image, preprocessing it, passing it through the trained model, and displaying the prediction. 

## Future Work

Possible improvements include:

* Multi-class defect classification for cracks, hotspots, and micro-defects
* Real-time defect localization using YOLO or Faster R-CNN
* Drone-based inspection for large solar farms
* Web deployment using Streamlit or Gradio
* IoT-enabled continuous monitoring
* Predictive maintenance
* Fine-tuning ResNet50 using larger datasets 

## Technologies

* Python
* TensorFlow / Keras
* OpenCV
* NumPy
* Matplotlib
* VGG16
* ResNet50
* Transfer Learning
* ELPV Dataset

## Suggested Project Structure

```text
solar-panel-defect-detection/
│
├── models/
│   ├── best_model.h5
│   ├── best_resnet50_model.h5
│   └── best_vgg16_model.h5
│
├── notebooks/
│   ├── SolarPanelDefectDetection.ipynb
│   ├── SolarPanelDefectDetection (2).ipynb
│   └── SolarPanelDefectDetectionWITHAugmentation.ipynb
│
├── src/
│   └── solarpaneldefectdetection.py
│
├── results/
│   ├── download-RESNET50latest.png
│   ├── download-VGG16latest.png
│   ├── epochsgeneralmodeltraining-output.png
│   ├── REG-NET16Trained.png
│   └── VGG-NET16Trained.png
│
├── report/
│   └── SOLAR_PANEL_PROJECT.pdf
│
├── requirements.txt
├── README.md
└── .gitignore
```

## Project

**Solar Panel Defect Detection and Defect Severity Estimation Using Deep Transfer Learning**

Department of Computer Engineering
International Islamic University Islamabad

### References

1. Simonyan, K. & Zisserman, A. *Very Deep Convolutional Networks for Large-Scale Image Recognition*, 2015.
2. He, K., Zhang, X., Ren, S. & Sun, J. *Deep Residual Learning for Image Recognition*, CVPR 2016.
3. Deitsch, S. et al. *Automatic Classification of Defective Photovoltaic Module Cells in Electroluminescence Images*, Solar Energy, 2019. 

If you want, I can also make the README **more professional/portfolio-style**, with badges, screenshots/results sections, installation commands, and a cleaner GitHub layout.
