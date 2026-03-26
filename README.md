# Rice Image Classification (PyTorch)

## Overview
This project implements a Convolutional Neural Network (CNN) to classify rice images into multiple classes using PyTorch. It includes a custom dataset loading, data augmentation, model training, and evaluation.

- A custom dataset class (**`ImageFolderCustom`**) is used for loading images and labels.
---
## Data Preprocessing

### Train Transforms
- Resize to 224 × 224 
- Random Horizontal Flip  
- Random Vertical Flip  
- Convert to Tensor  
- Normalization (ImageNet mean & std)

### Test Transforms
- Resize to 224 × 224
- Convert to Tensor  
- Same normalization as training data

---

## Model Architecture
The model (RiceClassifier) consists of:

- 3 Convolutional Blocks
- Conv2D layers  
- LeakyReLU & SiLU activations 
- MaxPooling  
- Dropout  
- **Classifier**
- Flatten layer  
- Fully connected layer for output prediction  

---

## Training Setup
- Loss Function: CrossEntropyLoss  
- Optimizer: AdamW  
- Batch Size: 32  
- Epochs: 50  
- Device: GPU (if available, else CPU)  

---

## Evaluation Metrics
- Training Loss & Accuracy 
- Validation Loss & Accuracy  
- Confusion Matrix  

---

## Results

### Loss & Accuracy Curves
<img width="1214" height="624" alt="image" src="https://github.com/user-attachments/assets/e103000f-2b2e-4148-9589-45a4ed6b2af3" />

the train loss and test loss are pretty much close to eachother so there is no overfitting, there is no underfitting aswell, i am looking for ways to improve it further.

### Confusion Matrix
<img width="675" height="659" alt="image" src="https://github.com/user-attachments/assets/e33f96d3-876f-4513-a60e-680457eb7266" />

the model is making mistakes mainly in seela vs sufaid. it can be clearly seen in the confusion matrix.
---


###Looking for ways (such as transfer learning) to futher improve the model..
