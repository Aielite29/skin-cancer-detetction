# skin-cancer-detetction

## Overview
This project focuses on developing AI algorithms to identify histologically confirmed skin cancer cases using single-lesion crops from 3D total body photos (TBP). The dataset consists of images resembling close-up smartphone photos, making it suitable for telehealth and primary care settings. The goal is to improve triage and early detection of skin cancer in underserved populations, where access to specialized care is limited.
This project achieved final scores of 0.16930 (private) and 0.18519 (public) on the competition leaderboard, in the ISIC 2024 Skin Cancer Detection Challenge hosted on Kaggle.

# Background
Skin cancer is one of the most common forms of cancer, and early detection is critical for improving patient outcomes. However, many populations lack access to specialized dermatologic care. This project leverages AI to address this gap by developing algorithms capable of identifying malignant skin lesions from benign ones using images that resemble smartphone photos. These algorithms aim to assist in triaging patients for clinical evaluation.

# Models
This project employs a multi-stage ensemble approach combining various models for robust predictions:
Convolutional Neural Networks (CNNs)
Vision Transformers (ViT)
Gradient Boosting Models
The ensemble model integrates image-based predictions with metadata features to enhance classification accuracy.

# Data
The dataset includes single-lesion crops from 3D total body photos (TBP), resembling close-up smartphone images. The data is highly imbalanced, with only a small fraction of positive cases (malignant lesions). Advanced sampling techniques were used to address this imbalance during training.

# Training
The training pipeline involves:
Preprocessing images and metadata.
Implementing advanced sampling techniques (over-sampling/under-sampling) to handle class imbalance.
Training multiple models (CNNs, Vision Transformers) for image-based predictions.
Using gradient boosting models (e.g., LightGBM, CatBoost) on metadata and image-based features.
Combining predictions through an ensemble strategy.

# Inference
For generating predictions:
Run trained CNNs and Vision Transformers on test images to extract predictions.
Use these predictions as additional features for gradient boosting models.
Apply the ensemble strategy to generate final probabilities for each lesion.

# Configuration
You can modify parameters such as model architecture, learning rate, and sampling techniques in the configuration files (train_config.py and test_config.py) to customize the training and inference pipelines.

# Composite Loss
To optimize model performance, a composite loss function was used:
Binary Cross-Entropy Loss: For classification accuracy.
Focal Loss: To handle class imbalance.
Dice Loss: To improve segmentation quality.

# Evaluation Metric
The competition uses partial Area Under the ROC Curve (pAUC) above an 80% true positive rate (TPR) as the primary metric. This ensures that models are highly sensitive in clinical practice settings where false negatives are unacceptable.

# The final submission achieved:

Private Score: 0.16930
Public Score: 0.18519
These results validate the effectiveness of the ensemble approach and innovative data preprocessing techniques employed in this project.

