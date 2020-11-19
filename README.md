# Rethink-UX-Internship-Challenge 3rd place solution
 
This repository contains **3rd place** solution to [Rethink UX Internship Challenge](https://dockship.io/challenges/5f7f058c81d83b7c2b93680b/rethink-ux-internship-challenge/overview) organised by [Rethink UX](https://www.linkedin.com/company/rethinkux/) on [Dockship](https://www.dockship.io)

## Problem Statement

### Scene Classification

The dataset contains images of 6 categories from around the world. It contains two directories "TRAIN" and "TEST". The TRAIN directory contains 6 training sub-directories and TEST contains 3409 testing images. The training images are provided in the directory of the specific class itself. The names of the directories are "class labels" to be used for submission. The aim is to classify the "TEST" images into one of the 6 classes.

- buildings
- forest
- glacier
- mountain
- sea
- street

## Evaluation Metric 

  F1 score
  
## Approach

-  Trained 4 models by fine-tuning pretrained ImageNet weights of ResNet50, SeResNext50, DenseNet121 and MobileNet_V2 architectures.

- Each model is trained in 2 stages using progressive resizing : `128x128 -> 256*256` except for SeResNext50 which is trained in 3 stages: `128x128 -> 256*256 -> 299x299`.

- Various combinations of techniques were used like `Data Augmentations(flip left right, random zoom and crop, etc)`, `Mixup` with `Focal Loss` and `FlattenedLoss of CrossEntropyLoss`.
 
- Final Submission was generated using `Final Blending`  notebook. Used weighted average of all the models for final submission as it performed better on the Test Dataset.

## Scores 

|**MODEL**  |**TEST SCORE** |
|---|---|
| ResNet50 | 94.925|
| SeResNeXt50 | 95.043|
| DenseNet121 | 94.720|
| MobileNet_V2 | 94.573|
| Weighted Average of all 4 models | 95.307| 

## Environment Setup

```
fastai==1.0.61

```

## Steps to Reproduce 

   * Run the `ResNet50`, `SeResNext50`, `DenseNet121` and `MobileNet_V2` notebooks from the `src` directory.
   * Run the `Final Blending` notebook on the generated outputs from the three notebooks.
   
Also predicted probabilities of all the models are provided in `output/probabilities` directory which can directly be used.

