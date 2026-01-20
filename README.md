# Learning Probability Density Functions using Non-Linear Transformation

## Overview

This project studies how a real-world variable behaves statistically after a non-linear transformation and how a probability density function (PDF) can be learned from the transformed data.

The dataset used is the India Air Quality dataset, and the feature selected is the NO2 concentration. A roll-number-dependent non-linear transformation is applied to the data, and a Gaussian-shaped probability density function is learned from the transformed values using Maximum Likelihood Estimation (MLE).

---

## Dataset

Source: India Air Quality Dataset (Kaggle)  
Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data  

Feature used: NO2 concentration  

The dataset contains air quality measurements collected from multiple cities across India. Only the NO2 column is used for analysis. Missing values are removed before further processing.

The dataset file is not included in this repository due to GitHub file size limitations.  

To run the notebook:

1. Download the dataset from the Kaggle link above.  
2. Extract the CSV file.  
3. Upload the CSV file into the Colab notebook environment.  
4. Ensure the file name matches the name used in the notebook (`india_air_quality.csv`).  

---

## Methodology

### Step 1: Non-Linear Transformation

Each NO2 value \( x \) is transformed into \( z \) using the function:

z = x + a_r sin(b_r x)

where:

a_r = 0.05 (r mod 7)  
b_r = 0.3 (r mod 5 + 1)  

and r is the roll number.

This transformation introduces non-linearity into the data and changes the shape of its statistical distribution.

---

### Step 2: Probability Density Function Model

The transformed data \( z \) is modeled using the function:

p̂(z) = c exp(-λ (z - μ)²)

where:

μ is the center of the distribution  
λ controls the spread of the distribution  
c is a normalization constant  

This function is Gaussian-shaped and approximates the empirical distribution of the transformed data.

---

### Step 3: Parameter Estimation using Maximum Likelihood Estimation

The parameters μ and λ are estimated using Maximum Likelihood Estimation.

For the model:

p̂(z) = c exp(-λ (z - μ)²)

the MLE solutions are:

μ = mean(z)  
λ = 1 / (2 Var(z))

The normalization constant c is derived theoretically using:

c = sqrt(λ / π)

---

## Results

The estimated parameters are:

| Parameter       | Value                   |
|-----------------|-------------------------|
| Lambda (λ)      | 0.0014612298133120176   |
| Mu (μ)          | 25.814687284943872      |
| c (theoretical) | 0.021566731221112533    |

The value of μ represents the mean of the transformed data.  
The value of λ is inversely related to the variance of the transformed data.  
The value of c is derived from λ to ensure that the learned PDF integrates to one.

---

## Graphical Results

The notebook includes the following plots:

1. Histogram of the transformed NO2 values (empirical PDF).  
2. Fitted Gaussian-shaped PDF overlaid on the histogram using MLE-estimated parameters.

The close alignment between the empirical PDF and the fitted curve confirms that the chosen model provides a good approximation of the transformed data distribution.

---

## How to Run

1. Download the dataset from the Kaggle link.  
2. Upload the CSV file into the Colab notebook environment.  
3. Run all cells sequentially.  
4. Observe the printed parameter values and plotted graphs.

---

## Dependencies

- pandas  
- numpy  
- matplotlib  

---

## Author

Gurmandeep Kaur
