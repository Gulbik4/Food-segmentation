# Food Segmentation Using DeepLabV3+

This project implements a semantic segmentation pipeline for food image analysis using a DeepLabV3+ model with an ImageNet-pretrained ResNet101 backbone. The aim is to identify and segment individual food components within an image.

## Introduction

The DeepLabV3+ architecture was chosen for its strength in semantic segmentation tasks, while the ResNet101 backbone offers robust feature extraction. The model was trained and evaluated on a food image dataset and demonstrated promising performance on larger food components, although smaller and overlapping regions remained challenging.

## Algorithm Overview

- The model uses a custom dataset class to handle food images and their corresponding masks.
- Images were resized to 256x256 and normalized using ImageNet statistics.
- Data augmentation included flips, rotations, affine transformations, color jittering, and Gaussian blur.
- Initially, 20 training epochs yielded low accuracy due to class imbalance and lack of validation.
- Improvements included:
  - Adding a validation set
  - Using a combined Dice + Cross-Entropy loss
  - Increasing training to 50 epochs
  - Employing AdamW optimizer and mixed precision training
  - Adopting a Cosine Annealing Learning Rate Scheduler

## Results and Analysis

- Initial model (20 epochs) reached a test mIoU of **0.1622**.
- After improvements:
  - Best validation mIoU: **0.3834**
  - Final test mIoU: **0.3193**
  - Sample image mIoU: **0.4524**

These improvements highlight better generalization and segmentation accuracy. However, performance on smaller or overlapping food items remains an area for future work.

## Dataset

The dataset consists of food images and segmentation masks. It is not included in this repository due to size and distribution constraints.

## Requirements

This notebook was developed in Google Colab using:

- PyTorch
- torchvision
- albumentations
- scikit-learn
- matplotlib
- OpenCV

## Acknowledgements

The model architecture was adapted from:
https://github.com/VainF/DeepLabV3Plus-Pytorch

---

This project was developed as part of my academic coursework and individual learning in deep learning and computer vision.
