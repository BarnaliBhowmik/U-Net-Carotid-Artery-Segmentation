# Common Carotid Artery Segmentation using U-Net
<p align="center">
  <img src="https://github.com/user-attachments/assets/1c39bd52-29ca-4ed7-bc65-d0dd7426af94"
       alt="Carotid Artery Segmentation Result"
       width="500">
</p>

This project uses a **U-Net deep learning architecture** to automatically identify and segment the **Common Carotid Artery (CCA)** in ultrasound images. The goal is to accurately detect the artery boundaries in **B-mode ultrasound scans**, reducing the need for manual annotation and making vascular image analysis faster and more efficient.

The project covers the complete workflow from dataset verification and preprocessing to model training, evaluation, and visualization of segmentation results.

---

## Project Objectives

- Develop an automated carotid artery segmentation system.
- Understand medical image preprocessing techniques.
- Implement a U-Net model for semantic segmentation.
- Train and evaluate the model using expert-annotated masks.
- Analyze segmentation performance using standard metrics.
- Gain practical experience in biomedical image analysis using deep learning.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1ef35825-53a8-4559-8759-6ad6858adb30"
       alt="image"
       width="600">
</p>

---

## Dataset

The dataset consists of:

- **Ultrasound Images (US Images)**
- **Expert-Annotated Binary Masks**

Each ultrasound image has a corresponding expert segmentation mask representing the carotid artery region.

### Dataset Structure

```
Common Carotid Artery Ultrasound Images/
│
├── US_Images/
│   ├── image1.png
│   ├── image2.png
│   └── ...
│
└── Expert_mask_images/
    ├── image1.png
    ├── image2.png
    └── ...
```

---

## Methodology

### 1. Data Verification

- Verify image-mask correspondence.
- Detect missing or mismatched files.
- Visualize sample image-mask pairs.

### 2. Data Preprocessing

#### Images

- Resize to 256×256 pixels
- Normalize pixel values to [0,1]

#### Masks

- Convert to grayscale
- Resize to 256×256 pixels
- Normalize to binary values

### 3. Train-Test Split

- 80% Training Data
- 20% Testing Data

---

## U-Net Architecture

The segmentation model follows the standard U-Net encoder-decoder architecture.
<img width="1842" height="7122" alt="U-Net Architecture" src="https://github.com/user-attachments/assets/bb9b4448-32b3-4339-86cd-2a0b04e6814c" />


### Encoder

- Convolution Layers
- ReLU Activations
- Max Pooling

Feature Channels:

- 16
- 32
- 64
- 128

### Bottleneck

Captures high-level semantic representations of vessel structures.

### Decoder

- Upsampling Layers
- Skip Connections
- Feature Concatenation
- Segmentation Reconstruction

---

## Training Configuration

| Parameter | Value |
|------------|---------|
| Optimizer | Adam |
| Loss Function | Binary Cross-Entropy |
| Batch Size | 32 |
| Epochs | 5 |
| Validation | Test Set |

### Training Callbacks

- EarlyStopping
- ReduceLROnPlateau

These techniques improve convergence and help prevent overfitting.

---

## Evaluation Metrics

### Model Compilation

<img width="917" height="197" alt="Screenshot 2026-06-25 172905" src="https://github.com/user-attachments/assets/5486593f-4fd1-446a-a6fc-7600ae103f48" />

### Model Accuracy vs Model loss

<img width="1189" height="490" alt="Model Accuracy vs Model Loss" src="https://github.com/user-attachments/assets/e9dca0e6-3dd7-4aaa-9406-1b6956923f1a" />

### Intersection over Union (IoU)

Measures overlap between predicted and ground-truth masks.

\[
IoU = {Intersection}/{Union}
\]
> **IoU:** 0.7099716959427285
### Dice Similarity Coefficient (DSC)

Measures segmentation similarity.

\[
Dice = {2 * Intersection}/{Prediction + GroundTruth}
\]
> **Dice:** 0.8303899972464893

### Model Summary
- **Total params:** 5,887,877 (22.46 MB)
- **Trainable params:** 1,962,625 (7.49 MB)
- **Non-trainable params:** 0 (0.00 B)
- **Optimizer params:** 3,925,252 (14.97 MB)

---

## Results

The trained U-Net model successfully learns vessel boundaries from ultrasound images and generates segmentation masks for unseen test samples.

Visual comparisons include:

- Original Ultrasound Image
- Ground Truth Mask
- Predicted Segmentation Mask

### Real Input Image & Predicted Mask
<img width="955" height="506" alt="real image test" src="https://github.com/user-attachments/assets/02528430-c5fb-4986-bbdf-51018a74283a" />

---

## Technologies Used

- Python
- TensorFlow
- Keras
- NumPy
- OpenCV
- Matplotlib
- Scikit-Learn

---

## Project Workflow

```text
Ultrasound Images
        │
        ▼
Data Verification
        │
        ▼
Preprocessing
        │
        ▼
Train-Test Split
        │
        ▼
U-Net Training
        │
        ▼
Model Evaluation
        │
        ▼
Segmentation Prediction
        │
        ▼
Visualization
```

## Learning Report

Project completed as part of a **medical image analysis** and deep learning learning initiative focused on biomedical imaging and AI-assisted healthcare technologies.
