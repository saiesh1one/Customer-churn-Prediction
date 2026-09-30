# Customer-churn-Prediction
📞 Telecom Customer Churn PredictionAn end-to-end Machine Learning pipeline developed in Python to predict customer churn for a telecommunications provider. This project identifies high-risk retention candidates using classification algorithms trained on clean, balanced, and engineered customer telemetry.

📌 Business Overview & ObjectiveAcquiring new subscribers can cost 5 to 25 times more than retaining existing ones. By accurately predicting customer churn before it happens, telecom operators can implement targeted retention strategies, improve customer loyalty, and reduce revenue leakage.Project Goals:Preprocess raw customer telemetry data while maintaining compliance with current Pandas Copy-on-Write standards.Address significant class imbalance between retained customers and churners using SMOTE (Synthetic Minority Over-sampling Technique).Train, evaluate, and benchmark multiple ML classifiers focusing on Recall and ROC-AUC scores.Extract key feature importances to reveal business drivers behind churn behavior.

📊 Dataset SummaryThe project utilizes the IBM Telco Customer Churn dataset (7,043 instances and 21 attributes).Target Variable: Churn (1 = Yes, 0 = No)Demographics: Gender, SeniorCitizen, Partner, DependentsSubscribed Services: PhoneService, MultipleLines, InternetService (DSL/Fiber optic), OnlineSecurity, TechSupport, StreamingTVAccount Info: Tenure, Contract type (Month-to-month, One year, Two year), PaymentMethod, MonthlyCharges, TotalCharges🛠️ Repository Structuretelecom-churn-prediction/
├── README.md                           <-- Project Overview & Documentation
├── requirements.txt                    <-- Python Dependencies
├── .gitignore                          <-- Git Ignore Rules
├── Customer_Churn_Prediction.ipynb     <-- Full Jupyter Notebook Pipeline
└── data/
    └── WA_Fn-UseC_-Telco-Customer-Churn.csv
    
⚙️ Data Pipeline StepsData Cleaning & Standardization:
Removed non-predictive identifiers (customerID).Cleaned blank values in TotalCharges using median imputation, updated for modern Pandas 2.x/3.x Copy-on-Write guidelines.Converted target variable Churn to binary numerical encoding (1 / 0).Feature Engineering & Preprocessing:Applied One-Hot Encoding (pd.get_dummies) to multi-class categorical attributes.Scaled numerical features (tenure, MonthlyCharges, TotalCharges) using StandardScaler.Performed stratified train-test splitting (80/20) to maintain underlying class ratios.Imbalance Handling:Applied SMOTE to the training split only, successfully rebalancing the training set to 8,278 samples across 30 engineered features while preventing data leakage into test sets.

📈 Model Performance & ResultsModels were trained on the resampled data and evaluated on unseen test data. The evaluation emphasizes Recall (catching maximum actual churners) and ROC-AUC.ClassifierAccuracyRecall (Churn = 1)ROC-AUCLogistic Regression~75%0.79~0.84Random Forest~78%0.58~0.83XGBoost Classifier~78%0.65~0.85

🔍 Key Business InsightsBased on XGBoost Feature Importance analysis:Contract Structure is Paramount: Short-term (Month-to-Month) contracts are the single largest predictor of customer churn. Incentivizing annual contracts reduces churn risk drastically.Fiber Optic Service Dissatisfaction: Fiber optic subscribers churn at a higher rate despite higher average bill amounts, indicating price sensitivity or competitive friction.Critical Tenure Window: Highest churn velocity occurs within the first 12 months of customer acquisition. Targeted onboarding campaigns during this timeframe yield high ROI.

🚀 Quickstart Guide
1. Clone the Repositorygit clone https://github.com/YOUR_USERNAME/telecom-churn-prediction.gitcd telecom-churn-prediction
2. Set Up Environment & Install Dependenciespython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
3. Run the Jupyter Notebookjupyter notebook Customer_Churn_Prediction.ipynb
🛠️ Tech StackLanguage: Python 3.10+Data Processing: Pandas, NumPyVisualization: Matplotlib, SeabornMachine Learning: Scikit-Learn, XGBoost, Imbalanced-Learn (SMOTE)
