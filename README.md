# Predicting Customer Subscription to Term Deposits in a Banking Institution

## Business Understanding
The bank conducts direct marketing campaigns via phone calls to promote term deposits. However, contacting every client is costly and time-consuming. The challenge is identifying which clients are most likely to subscribe to a term deposit, allowing the bank to reduce marketing costs by focusing on potential subscribers, improve conversion rates by targeting the right customers, and enhance customer experience by avoiding unnecessary calls.

## Objective
To develop a predictive model that helps a Portuguese banking institution determine the likelihood of a client subscribing to a term deposit based on direct marketing campaign data.

## Data Understanding
- Age : Age of the client
- Job : Type of job (categorical: admin, blue-collar, entrepreneur, housemaid, management, retired, self-employed, services, student, technician, unemployed, unknown)
- Marital : Marital status (categorical: divorced, married, single, unknown; note: divorced means divorced or widowed)
- Education : Education level of the client
- Default : Has credit in default? If a client has credit in default, they may be less likely to invest in a term deposit
- Balance : Average yearly balance
- Housing : Has housing loan? Clients with existing loans might have lower investment capacity
- Loan : Has personal loan? Clients with existing loans might have lower investment capacity
- Contact : Contact communication type (categorical: cellular, telephone)
- Day : Last contact day of the week
- Month : Last contact month of year 
- Duration : Last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
- Campaign : Number of contacts performed during this campaign and for this client (numeric, includes last contact)
- Pdays : Number of days that passed by after the client was last contacted from a previous campaign (numeric; -1 means client was not previously contacted)
- Previous : Number of contacts performed before this campaign and for this client
- Poutcome : Outcome of the previous marketing campaign (categorical: failure, nonexistent, success)
- Y : Has the client subscribed a term deposit? Yes or No

## Process
### Data Preprocessing 
Performing data inspection and cleaning, including understanding data characteristics, checking for missing values, duplicate data, and identifying imbalanced classes.
### Feature Engineering 
Feature engineering transforms raw data into meaningful representations that enhance model performance. The following techniques are applied:
   - **Handling outlier (IQR)**. These methods are more robust against outliers because they can adapt well to non-normal data distributions. Handling outliers helps balance the data and prevents model bias.
   - **Feature transformation (Label encoder)**. Label encoding is used to convert categorical features into numerical values so they can be processed by machine learning models. 
   - **Data augmentation (ADASYN)**. ADASYN is used to address class imbalance by generating synthetic samples adaptively, adding more synthetic samples to the minority class, and reducing bias toward the majority class.
   - **Feature scaling (Robust Scaler)**. Robust Scaler is used to normalize features while minimizing the influence of outliers by utilizing the median and IQR, making it more resistant to extreme values.
### Model Selection 
Model selection is carried out by testing several ensemble models such as Random Forest, Gradient Boosting, LightGBM, AdaBoost, CatBoost, and XGBoost because they are more robust to different data conditions, handle non-linearity well, and improve predictive performance by combining multiple weak learners into a strong model.
### Feature Selection 
Performed using Recursive Feature Elimination with Cross-Validation (RFECV), which iteratively removes less important features to enhance model interpretability, retains only the most relevant features to reduce complexity and improve efficiency, and prevents overfitting by eliminating redundant or irrelevant features.
### Cross Validation & Hyperparameter Tuning 
Cross-validation ensures the model is evaluated on different data subsets to reduce overfitting risk, while hyperparameter tuning with Optuna, using Bayesian optimization and the Tree-structured Parzen Estimator (TPE), efficiently automates model selection and finds optimal settings to maximize accuracy and minimize overfitting.

## Prediction Results
The CatBoost model achieved excellent performance on the bank subscription deposit dataset with the following metrics:
- Accuracy: 93.56% – indicating a high proportion of correctly classified instances.
- F1 Score: 93.62% – showing a strong balance between precision and recall.
- Precision: 92.74% – meaning that 92.74% of predicted positives are actual positives.
- Recall: 94.52% – indicating that 94.52% of actual positives were correctly identified.
- AUC-ROC: 0.9828 – demonstrating excellent discriminatory power between classes.

The CatBoost model effectively handles categorical features and delivers a highly accurate and well-balanced classification for predicting bank subscription deposits. The AUC-ROC of 0.9828 further confirms that the model has strong predictive capability and can confidently differentiate between subscribed and non-subscribed customers.
