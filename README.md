# Rice Image Classification (PyTorch)
1508:
![1508_0_2721](https://github.com/user-attachments/assets/e94210f7-811b-4982-811e-3905f3738e27) 
Ari:
![ari_0_3129](https://github.com/user-attachments/assets/08a2f1d0-3843-45ba-a1ac-0ab1b2f6df3a)
Kachi:
![kachi_0_3005](https://github.com/user-attachments/assets/2a5f67e4-1948-4cd7-a5d3-4585762779ab)
Kachi_Kainat:
![k_k_0_3050](https://github.com/user-attachments/assets/7399eaf6-e465-4569-8821-583b5d041032)
Seela:
![Seela_0_2991](https://github.com/user-attachments/assets/2ad2de3b-d27b-46e5-b05b-497374f98514)


## Overview
This project implements a Convolutional Neural Network (CNN) to classify rice images into multiple classes using PyTorch. It includes a custom dataset loading, data augmentation, model training, and evaluation.
Initially i tried a simple tinyVgg model but the results were horrible and then i tried some fine tuning by:
- changing number of layers
- changing hidden units
- changing augmentations
- changing learning rate and adding schedular
- changing number of epochs
- changing activation function
- adding drop out layers.

But nothing improved much, there were both overfitting (gap between train and loss curves) and underfitting (train and test loss were high). then i asked for help in discussions of one of the repository of my youtube instructor and @LuluW8071 helped me by adding SqueezeExcitation block and used leakyrelu and silu instead of relu, adamW instead of adam. making these changes improved the model alot and allowed me to learn new things in  my computer vision journey.

- A custom dataset class (**`ImageFolderCustom`**) is used for loading images and labels.
- Dataset was taken form kaggle: https://www.kaggle.com/datasets/ishaqedu/rice-seed-image-dataset-from-pakistan
  

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
