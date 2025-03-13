# Forecast Nonviolent Conflicts

I help policymakers identify key risk factors—like prior wars, population size, and ethnic diversity—before violence begins, using machine learning models

## Why Now?

Conflict studies have traditionally used Null Hypothesis Significance Testing (NHST), which lacks predictive power. This project uses machine learning on historical data to improve conflict prediction, addressing the under-researched area of nonviolent conflicts.

# Development Notes

## Tech Used
- **Python**
- **Matplotlib**
- **Scikit-learn**
- **RandomForestClassifier**

Datasets: NAVCO and Quality of Government (QoG)

## Data Preparation

1. **Data Cleaning & Preprocessing**:
   - Renamed and created common key variables (`cow` and `year`) to help with merging.
   - Selected relevant columns from both datasets.
   - Merged datasets using a left join on `cow` and `year`.
   - Filtered data to focus on the years 1981-2013 due to data availability

2. **Feature Engineering**:
   - Created target variables:
     - `violent`: binary indicator for violent conflicts.
     - `nonviolent`: binary indicator for nonviolent conflicts.
     - `conflict`: presence of any conflict.
     - `civil_war`: binary indicator for civil war.
     - `int_conflict`: binary indicator for international conflict.
   - Dropped unnecessary columns to reduce dataset complexity.

3. **Visualization**:
   - Aggregated yearly counts of different conflict types.
   - Plotted trends of conflicts over time using Matplotlib.

### Model Preparation
1. **Feature Selection & Lagging**:
   - Created lagged versions of target variables to use as predictors.
   - Handled missing values by dropping rows with NaNs.
   - Removed `cow` and `year` from features to prevent data leakage.

2. **Train-Test Split**:
   - Split data into training and test sets (80-20 split).
   - Created five different versions of the dataset, each focusing on one specific lagged variable as a predictor.

3. **Feature Scaling**:
   - Used `StandardScaler` from `sklearn.preprocessing` to normalize features.

### Model Training
1. **Random Forest Classifier**:
   - Trained separate `RandomForestClassifier` models for each of the five target variables.
   - Found which variables contribute the most to prediction.

## Optimizations
- **Refactored Merging Process**: Originally, merging datasets caused redundant columns. Restructuring eliminated unnecessary operations.
- **Efficient Feature Selection**: Initial dataset had many irrelevant variables. Selective feature extraction improved model efficiency.
- **Standardization**: Normalized input features to improve model convergence and reduce variance in predictions.

## Challenges

1. **Data Imbalance**: Conflict data is heavily imbalanced, with most countries in peace, making conflict prediction difficult. Solutions like oversampling or anomaly detection are necessary for handling this.

2. **Predicting Unpredictable Conflicts**: Current models often fail to foresee conflicts that happens out of nowhere, especially those without clear historical signals.

3. **Data Limitations**: Accurately measuring the severity of conflict, especially in war zones, is challenging. Text-based approaches, such as NLP, could help identify rising tensions and conflict signs.

4. **Cultural Sensitivity**: Models must account for local cultural and negotiation factors to improve prediction accuracy, as these greatly influence conflict dynamics.

5. **Geospatial & Climate Factors**: Integrating geospatial data (e.g., troop placements) and climate research could improve the model’s ability to predict conflict hotspots and escalation patterns.

6. **Outliers and Metrics**: Traditional performance metrics like mean square error can be misleading when outliers dominate the data. Alternative evaluation strategies are needed for better accuracy in conflict prediction.

## Lessons Learned
- **Feature Selection is important**: Removing irrelevant features significantly improved model performance.
- **Scaling Enhances Model Stability**: Standardization helped prevent models from being biased toward high-magnitude features.
- **Visualizing Data Before Modeling is Key**: Identifying trends before training provided insights into how conflicts evolve over time.



![11](https://github.com/user-attachments/assets/4144461f-5cbd-45b1-9543-c01797e88074)

![Untitled design-16](https://github.com/user-attachments/assets/e31ed82e-b84f-4ada-9bcc-a225b2d616d9)
