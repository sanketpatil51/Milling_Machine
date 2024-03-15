# Predictive Modeling for Milling Machine Process 


## Abstract
<img align="right" alt="milling machine" width="300" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/m_img.png" >

This study focuses on developing a predictive model for forecasting the success or failure of milling machine operations in manufacturing processes. We utilize logistic regression, random forest, artificial neural networks (ANN), and decision tree algorithms to construct the predictive model.

Our analysis includes a comprehensive evaluation using confusion matrices to summarize the 
performance of each model. By leveraging these advanced analytical techniques, our research aims to provide actionable insights for optimizing milling machine operations and enhancing overall process reliability in manufacturing.

## Introduction
Milling machine operations are integral to various manufacturing processes, impacting efficiency and reliability. This study employs logistic regression, random forest, artificial neural networks (ANN), and decision tree algorithms to develop a predictive model for pridicting the success or failure of milling machine operations. By leveraging these advanced analytical techniques, our research aims to provide actionable insights for optimizing milling machine operations and enhancing overall process reliability in manufacturing. The predictive model's evaluation includes a comprehensive analysis using confusion matrices to summarize each model's performance. Through this analysis, we seek to contribute to the advancement of predictive maintenance strategies and overall process optimization in the manufacturing industry. This research addresses the pressing need for reliable predictive models to anticipate and mitigate potential failures in milling machine operations. By identifying key factors influencing success or failure, our study aims to assist manufacturing industries in making informed decisions to improve operational efficiency and reduce downtime. This research contributes to the ongoing efforts in leveraging data-driven approaches to enhance manufacturing processes' reliability and productivity.

## Data understanding
<img align="center" alt="milling machine" width="1100" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/data_img.png" >

The dataset utilized in this project is a synthetic representation derived from an existing milling machine. It comprises 10,000 data points organized as rows, each containing 14 features in columns.


Features Description
### UID (Unique Identifier)
Ranges from 1 to 10,000, serving as a distinct identifier for each data point.
### Product ID
Consists of a letter ('L', 'M', or 'H') representing low, medium, or high product quality variants respectively, followed by a variant-specific serial number.
### Type
Represents the product type ('L', 'M', or 'H') derived from the Product ID column.
### Air Temperature [K]
Generated using a random walk process and normalized to a standard deviation of 2 K around 300 K.
### Process Temperature [K]
Generated using a random walk process, normalized to a standard deviation of 1 K, and added to the air temperature plus 10 K.
### Rotational Speed [rpm]
Calculated from a power of 2860 W and overlaid with normally distributed noise.
### Torque [Nm]
Torque values are normally distributed around 40 Nm with a standard deviation of 10 Nm and no negative values.

### Tool Wear [min]
The quality variants 'H', 'M', 'L' add 5, 3, and 2 minutes of tool wear respectively to the used tool in the process.

### Machine Failure Label
Indicates whether the machine has failed in this particular data point for any of the following failure modes.

### Machine Failure Modes
### 1)Tool Wear Failure (TWF)
The tool will be replaced or fail at a randomly selected tool wear time between 200 - 240 mins. In the dataset, the tool is replaced 69 times and fails 51 times at this point.

### 2)Heat Dissipation Failure (HDF)
Occurs if the difference between air- and process temperature is below 8.6 K and the tool's rotational speed is below 1380 rpm. This condition is met for 115 data points.

### 3)Power Failure (PWF)
The process fails if the product of torque and rotational speed (in rad/s) is below 3500 W or above 9000 W. This condition is observed 95 times in the dataset.

### 4)Overstrain Failure (OSF)
If the product of tool wear and torque exceeds specific thresholds for each product variant, the process fails due to overstrain. This occurs for 98 data points.

### 5)Random Failures (RNF)
Each process has a 0.1% chance of failing regardless of its parameters. This occurs for 5 data points.

## Feature Engineering
### Chek missing value
<img align="center" alt="milling machine" width="500" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/isna_img.png" >
Conclusion: The heatmap analysis unequivocally reveals the absence of any missing values within the dataset.

### tool wear type
<img align="center" alt="milling machine" width="500" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/count.png" >
Conclusion: The comparison of the two graphs reveals a clear similarity between the proportion of machine failures by type and the corresponding use of of tool wear types


### Correlation 
<img align="center" alt="milling machine" width="500" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/hmap.png" >
Conclusion: Based on the heatmap presented above, it is evident that there is a strong correlation between Process temperature [K], Rotational speed [rpm], and Torque [Nm]. However, since Air temperature [K] and Process temperature [K] are closely related terms, we have decided to exclude Air temperature [K] from further analysis. Rotational speed [rpm] and Torque [Nm] remain relevant as distinct variables.

### Nature of response
<img align="center" alt="milling machine" width="500" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/inb.png" >
Conclusion: The graph above clearly illustrates that the data is imbalanced, indicating a need for balancing methods to address this issue.

## Final data 

After one-hot encoding and balancing the data, it appears as follows
<img align="center" alt="milling machine" width="900" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/fdata_img.png" >
## Check below is the code for model fitting and feature engineering.
Google colab link   [clik_here](https://github.com/sanketpatil51/Milling_Machine/blob/main/milling.ipynb)

## Model Performance Evaluation
<img align="center" alt="milling machine" width="500" src="https://github.com/sanketpatil51/Milling_Machine/blob/main/fs_img.png" >
Conclusion: Random Forest achieved the highest accuracy among the evaluated models, indicating its superior predictive capability. This underscores its potential as a robust and reliable algorithm for the given dataset.

## Suggestions
For the successive operation of a milling machine, the following are some suggestions
1) Kept Torque less than 50 NM.
2) Replace Tool wear less than 200 times.
3) Kept rotational seed in between 1379 to 2416 rpm.
   
## limitations
1) Imbalanced data can still pose challenges in accurately representing the minority class, potentially affecting model performance.
2) The superior performance of Random Forest may not generalize across all datasets and could be subject to overfitting or bias towards specific features.

