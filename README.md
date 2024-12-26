# Activity Estimation Based on Heart Rate

This project focuses on developing robust methods for accurately estimating daily activities from PPG (Photoplethysmography) signals while accounting for motion artifacts. The project processes 8-second windows of PPG signal data and uses accelerometer data to estimate activities aligned with ground truth.

## Problem Overview

PPG technology, widely used in wearable devices for continuous heart rate monitoring, faces accuracy challenges due to motion artifacts during daily activities. This project addresses these challenges by:
- Processing PPG signals (64 Hz sampling rate) with motion artifact compensation
- Utilizing accelerometer data (32 Hz sampling rate)
- Handling transitions between different activity types
- Maintaining accuracy across diverse subjects and activities

## Dataset Description

The project uses the PPG-DaLiA dataset which includes:

### Activities Tracked
- Stationary: sitting, working
- Dynamic: walking, cycling, climbing stairs
- Real-world: driving, lunch break, table soccer
- Transition periods between activities

### Sensor Data Sources
1. Wrist Device (Empatica E4)
   - PPG (64 Hz)
   - Accelerometer (32 Hz)
2. Chest Device (RespiBAN)
   - ECG (700 Hz)
   - Accelerometer (700 Hz)

## Key Challenges and Solutions

1. Data Imbalance
   - Challenge: Overrepresentation of stationary activities
   - Solution: Implemented stratified sampling in train-test splits

2. Feature Distribution Scaling
   - Challenge: Varying scales across features
   - Solution: Implemented multiple scaling techniques:
     - Standard Scaling
     - Min-Max Scaling
     - Robust Scaling
     - Quantile Scaling

3. High Dimensionality
   - Challenge: Complex model training due to numerous raw features
   - Solution: Applied PCA for dimensionality reduction

## Models Implemented

1. Logistic Regression
   - Best performance with Quantile and Robust Scaling
   - Significant improvement over unscaled data

2. Naive Bayes
   - Tested with and without PCA
   - Consistent performance across scaling methods
   - Best accuracy: 0.55858 with Quantile Scaling

3. MLP Classifier
   - Best accuracy: 0.90 with Standard and Robust Scaling
   - Strong performance improvement with scaled features

4. Decision Tree Classifier
   - Consistent ~94.8% accuracy across scaling methods
   - High precision and recall (0.92-0.97)

5. Random Forest Classifier
   - Best accuracy: 0.97 with No Scaling and Standard Scaling
   - Robust performance across different scaling methods

## Key Findings

- Scaling significantly improves performance for most models
- Quantile and Robust Scaling show consistently strong results
- Decision Trees and Random Forests demonstrate robustness to scaling
- MLPClassifier performs best on larger datasets compared to Logistic Regression

## Setup and Installation

```bash
# Clone the repository
git clone https://github.com/mayank2021264/ActivityEstimationBasedOnHeartRate.git

# Install required packages
pip install -r requirements.txt
```

## Usage

Detailed implementation and usage examples can be found in the project notebooks.

## Future Work

1. Evaluation and Benchmarking
   - Cross-dataset validation
   - Implementation of explainable AI techniques

2. Personalized Estimation
   - Development of subject-specific models
   - Integration of transfer learning approaches


## Contributors

- Manshaa Kapoor (maansha21540@iiitd.ac.in)
- Mayank Pandey (mayank21264@iiitd.ac.in)
- Niharika Singh (niharika21545@iiitd.ac.in)
- Ria Malhotra (ria21412@iiitd.ac.in)
- Vishal Singh (vishal21575@iiitd.ac.in)
