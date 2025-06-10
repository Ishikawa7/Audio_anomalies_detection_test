# Anomaly Detection on Audio MNIST (Digit "Six")
## Disclaimer: i used PCA but it would be better to use an autoencoder, i used simple algorithms for this test
---

This project delves into various **anomaly detection techniques** applied specifically to the pronunciations of the digit "six" within the Audio MNIST dataset. Our approach combines statistical methods with machine learning to identify different types of anomalies and visualize their characteristics, ultimately setting the stage for a **self-supervised anomaly classification** framework.

## Approach & Key Features

### 1. Data Preparation
Audio signals undergo **Fast Fourier Transform (FFT)**, and their amplitudes are normalized by dividing by the maximum amplitude.

### 2. Multi-faceted Anomaly Scoring
We employ two distinct methods to capture different anomaly types:
* **Isolation Forest:** Effective for detecting outliers that are **spatially separated or exhibit extreme values**. The anomaly score here reflects how easily a sample can be isolated.
* **PCA Reconstruction Error:** Used to identify anomalies that **deviate significantly from the learned 'normal' data distribution**. Higher reconstruction errors indicate a greater anomaly.

### 3. Advanced Anomaly Visualization
* **PACMAP for 2D Mapping:** A non-linear dimensionality reduction technique, PACMAP, is used to project high-dimensional features into a 2D scatter plot. On this map, the **size of each point corresponds to its PCA reconstruction error**, while its **color represents its anomaly score from Isolation Forest**.
* **Clustering by Reconstruction Error:** We apply PACMAP again, but this time to the reconstruction errors over frequencies. This creates a new map that groups samples with similar reconstruction error patterns. **K-means clustering** is then applied to these groups, and we visualize the **average reconstruction error for each cluster** to understand their characteristic anomaly profiles.

![alt text](https://github.com/Ishikawa7/Audio_anomalies_detection_test/blob/main/recostruction_errors_map.png?raw=true)
![alt text](https://github.com/Ishikawa7/Audio_anomalies_detection_test/blob/main/reconstruction_error_patterns.png?raw=true)

### 4. Detailed Anomaly Characterization
We perform visual comparisons of **original and reconstructed signals** (and their frequency spectra) for selected anomalous samples, providing clear insights into the nature of the discrepancies.

![alt text](https://github.com/Ishikawa7/Audio_anomalies_detection_test/blob/main/example_sample_analysis.png?raw=true)

## Goal

This repository aims to serve as a robust base for developing a **self-supervised anomalies classification system**. By combining diverse anomaly scoring methods with advanced visualization and clustering techniques, we gain a deeper understanding of the characteristics of anomalous audio samples.
