# Recognizing anomalies in financial and crypto translations

1. Implementation Plan

a. Data Ingestion and Preprocessing  
• Load the Dataset: Load data from a CSV file.  
• Clean Data: Remove unwanted characters from numeric fields and convert fields to appropriate data types.  
• Feature Engineering: Derive additional features such as transaction time differences and frequency flags to enrich the data.  

b. Exploratory Data Analysis (EDA)  
• Analyze Basic Distributions: Visualize distributions of transaction values, token prices, liquidity, and market cap.  
• Examine Correlations: Identify multicollinearity to optimize feature selection.  
• Create Visualizations: Use heatmaps, bar charts, and scatter plots to observe feature relationships and identify patterns in the data.  

c. Model Training and Evaluation  
• Define Labels: Set conditions for labeling transactions as anomalies based on transaction frequency and transaction amount.  
• Split the Dataset: Separate data into training and testing sets using standard techniques.  
• Model Selection: Choose unsupervised models for anomaly detection, such as One-Class SVM, Isolation Forest, and DBSCAN.  
• Hyperparameter Optimization: Apply grid search or Bayesian optimization (e.g., Hyperopt) for model parameter tuning.  
• Neural Network Training: Design and train an Autoencoder to learn a compressed representation of normal transactions and detect anomalies as significant deviations from this baseline.  

d. Evaluation and Metrics  
• Evaluate Models: Calculate performance metrics such as accuracy, precision, recall, F1 score, and silhouette score to assess model performance.  
• Model Comparison: Compare models based on these metrics to select the best-performing model for deployment.  

e. Alerting Mechanism and Confidence Scores  
• Confidence Scoring: Calculate confidence scores based on distance from decision boundaries or isolation scores.  
• Threshold Setting: Set probability thresholds for generating alerts.  

--- 

2. Step-by-Step Implementation with Results

Step 1: Data Ingestion and Preprocessing  
• Result: Successfully loaded and cleaned data. Addressed issues with timestamp formatting errors, and implemented data validation at the loading stage.  
• Additional Features: Created transaction time differences and frequency flags. Converted categorical features to numerical values for model training.  
• Outcome: Prepared dataset with derived features to enhance model training.  

Step 2: Exploratory Data Analysis  
• Result: Limited data volume for analysis and model training.  
• Visualizations showed multicollinearity between fields like market cap and token price, leading to removing some fields.  
• Outcome: Selected optimal features based on EDA, improving model efficiency.  

Step 3: Model Training and Evaluation  
• Result: Trained three unsupervised anomaly detection models—One-Class SVM, Isolation Forest, DBSCAN—and one neural network model (Autoencoder). Limited data affects the reliability of the metrics obtained.  
  - One-Class SVM: Achieved high recall and moderate precision, effectively identifying transaction volume and timing anomalies.  
  - Isolation Forest: Performed moderately, particularly effective for detecting anomalies in transaction volumes but with lower precision than SVM.  
  - DBSCAN: Limited performance due to dataset size and clustering noise. We have successfully grouped transactions from the same account in short intervals, useful for identifying frequency-based anomalies.  
  - Autoencoder: Detected anomalies based on high reconstruction error, balanced in identifying unusual transaction patterns or values. With more data, this neural network could capture complex patterns missed by simpler models.  

• Outcome: Selected One-Class SVM as the preferred model based on overall performance. The Autoencoder shows high potential and could improve with more data and features. Future enhancements may include integrating two models for parallel anomaly detection (One-Class SVM + DBSCAN).

f. Saving Model and Results  
• Model Persistence: Save trained models for later use in anomaly detection.  
• Output Results: Export predictions with confidence scores for further analysis.  

g. Testing with Synthetic Data  
• Testing: Generate synthetic data and apply trained models to it, set alerting system.
