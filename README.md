# energy_neural
# README: Neural Network Model for Pollution Severity Classification

## Overview
This project implements a neural network model using TensorFlow and Keras to classify pollution severity based on environmental pollution indices.

## Dataset and Features
The dataset includes:
- **Air_Pollution_Index**
- **Water_Pollution_Index**
- **Soil_Pollution_Index**
- **Industrial_Waste (in tons)**

A new feature `total` is computed as:
```
data["total"] = data["Air_Pollution_Index"] + data["Water_Pollution_Index"] + data["Soil_Pollution_Index"] + data["Industrial_Waste (in tons)"]
```
The `total` feature is label-encoded before training.

## Data Preprocessing
1. **Train-Test Split**: 80% training, 20% testing
2. **Feature Scaling**: StandardScaler is used to normalize `total` values.

## Model Architecture
- **Input Layer**: 16 neurons, ReLU activation
- **Hidden Layer**: 8 neurons, ReLU activation
- **Output Layer**: 1 neuron, Sigmoid activation

## Training Configuration
- **Optimizer**: Adam
- **Loss Function**: Binary Crossentropy
- **Batch Size**: 2
- **Epochs**: 50

## Model Evaluation
The model is evaluated using a test set:
- **Loss**: Binary crossentropy
- **Metric**: Accuracy

## Results
### Confusion Matrix:
```
[[ 0 10  0]
 [ 0 23  0]
 [ 0  7  0]]
```
### Classification Report:
```
              precision    recall  f1-score   support

          -1       0.00      0.00      0.00        10
           0       0.57      1.00      0.73        23
           1       0.00      0.00      0.00         7

    accuracy                           0.57        40
   macro avg       0.19      0.33      0.24        40
weighted avg       0.33      0.57      0.42        40
```

## Key Observations
- The model achieved an accuracy of **57%**.
- Class `0` (Moderate Pollution) had the highest recall of **100%**.
- The model failed to predict classes `-1` (Low Pollution) and `1` (High Pollution).

## Future Improvements
- Improve class balance to enhance prediction for underrepresented classes.
- Tune hyperparameters and experiment with different activation functions.
- Increase dataset size for better generalization.

