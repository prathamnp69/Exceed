# Muffin vs Chihuahua Classifier (Data-Centric AI Hackathon)

Binary image classification project built during a Data-Centric AI Hackathon using the 3LC platform.

The objective was to train a ResNet-18 model to classify:
- Chihuahua (0)
- Muffin (1)

The challenge focused on improving model performance by improving the dataset using 3LC tools instead of modifying the model architecture.

---

## Project Overview

This project demonstrates a data-centric machine learning workflow.

1. Train a model on a small labeled dataset.
2. Use the 3LC dashboard to analyze embeddings and predictions.
3. Label useful samples from the unlabeled dataset.
4. Adjust sample weights.
5. Retrain the model with improved data.

Repeating this process improves accuracy on the hidden test dataset.

---

## Dataset

### Train Dataset
- 100 labeled images
  - 50 Chihuahua
  - 50 Muffin
- 3579 unlabeled images

### Validation Dataset
- 1000 images
- Balanced dataset
  - 500 Chihuahua
  - 500 Muffin

### Test Dataset
- 1184 images
- Labels are hidden
- Predictions submitted to Kaggle

---

## Model

Model used: **ResNet-18**

Competition rules:
- No pretrained weights
- Train from scratch
- Only provided dataset allowed

---

## Workflow

### Step 1: Register dataset

python register_tables.py

### Step 2: Initial training

python train.py

### Step 3: Start 3LC dashboard

3lc service

Open the dashboard in browser:

https://dashboard.3lc.ai

### Step 4: Label undefined samples

Use embeddings to:
- identify clusters
- label samples
- set sample weight = 1

### Step 5: Retrain model

python train.py

### Step 6: Generate predictions

python predict.py

This creates:

submission.csv

---

## Submission Format

image_id,prediction,confidence  
test_00001,0,0.92  
test_00002,1,0.88  

prediction:
- 0 = Chihuahua
- 1 = Muffin

confidence:
- value between 0 and 1

---

## Project Structure

project/

data/  
 ├── train/  
 ├── val/  
 └── test/  

register_tables.py  
train.py  
predict.py  
config.yaml  
sample_submission.csv  

submission.csv  
README.md  

---

## Tools Used

- Python
- PyTorch
- 3LC Data-Centric AI Platform
- UMAP embeddings
- Kaggle

---

## What We Learned

- Data-centric AI methodology
- Active learning using embeddings
- Dataset curation and labeling
- Experiment tracking using 3LC
- Improving models through better data instead of architecture changes

---

## Acknowledgments

- 3LC platform for providing the data-centric AI workflow
- Sphere Hive for organizing the hackathon
