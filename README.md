# Deep-learning-resnet (Group: Deep fried AI)
Describtion:
kaggle competition for designing a resnet neural network to do image classificaiton (CIFAR 10 classification).

Team Members:
Qin Huai,
Li Shihao, 
Yin Wufei

Introductor:
Chinmay Hegde (chinmay.h@nyu.edu

## Dataset unpackage and load
The dataset is available for download [here](http://www.cs.toronto.edu/~kriz/cifar.html).

Make sure you unpackage the dataset file and pick all pickle files with Jupyter notes code file in one folder.

## Introduction  
This project implements an optimized ResNet architecture with Squeeze-and-Excitation (SE) blocks to enhance feature learning. The model is trained on the CIFAR-10 dataset, leveraging advanced data augmentation, regularization techniques, and adaptive learning rate schedules to improve generalization and robustness.  

## Model Architecture  

We designed a lightweight SE-ResNet architecture with an optimized channel configuration:  
- **Progressive Channel Design:** {32-64-128-256}, reducing parameters while maintaining hierarchical feature extraction.  
- **Residual Blocks:** Two 3×3 convolutional layers per block with batch normalization and ReLU activation.  
- **SE Attention Mechanism:** Integrated into deeper layers (layer3 and layer4) for dynamic channel recalibration.  
- **Global Average Pooling & Dropout:** Applied before classification for robustness.  

### Final Network Structure  

| Layer | Type | Output Channels | Stride |  
|-------|------|----------------|--------|  
| Input | 3×3 Conv + BN + ReLU | 32 | 1 |  
| Layer 1 | 2 Residual Blocks | 32 | 1 |  
| Layer 2 | 2 Residual Blocks | 64 | 2 |  
| Layer 3 | 2 SE Residual Blocks | 128 | 2 |  
| Layer 4 | 2 SE Residual Blocks | 256 | 2 |  
| Global Pool | Avg Pool + Dropout (p=0.2) | - | - |  
| Fully Connected | FC Layer (256→10) | 10 | - |  

## Training Optimization  

- **Data Augmentation:** Random cropping, horizontal flipping, color jittering, cutout, and mixup.  
- **Regularization Strategies:** Dropout (p=0.2), weight decay (5e-4), and label smoothing (0.08).  
- **Optimizer:** SGD with momentum (0.9).  
- **Learning Rate Scheduling:** Warmup (first 15 epochs) + Cosine Annealing (remaining epochs).  
- **Total Parameters:** 2.82M.  

## Results  

The model achieved **85.57% accuracy** on the CIFAR-10 dataset, demonstrating improved generalization and robustness through feature recalibration, augmentation, and adaptive optimization.  

---  

This project highlights the efficiency of SE-ResNet in classification tasks, focusing on lightweight design, attention mechanisms, and training optimization strategies. 🚀  

