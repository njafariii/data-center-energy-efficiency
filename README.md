# Data Center Energy Efficiency

ADS-505 Applied Data Science for Business Team Project

## Project Overview
This project examines factors associated with energy
consumption and efficiency in AI data centers.

## Data Preparation and Reproducibility

### Dataset
The project uses the Green AI Data Center Telemetry Dataset by Deep Joshi (2026), available on Kaggle:

https://www.kaggle.com/datasets/deeplumiere/green-ai-data-center-telemetry-dataset

Download `green_ai_datacenter.csv` and place it inside the `data/` folder.

### Python Requirements
The preprocessing notebook uses the following libraries:
- pandas
- numpy
- matplotlib
- scikit-learn
- joblib

### Running the Notebook
1. Open `data_preparation.ipynb` in VS Code.
2. Select a Python environment with the required libraries installed.
3. Confirm that `data/green_ai_datacenter.csv` is available.
4. Run the notebook cells in order.

### Preprocessing Summary
The dataset contains 10,000 observations and 15 original variables.

The preprocessing workflow includes:
- Replacing missing data center regions with "Unknown".
- Checking for duplicate records and potential outliers.
- Creating a temperature-cooling interaction feature.
- Separating the efficiency classification target from predictors.
- Using an 80/20 stratified training and testing split.
- Standardizing numerical predictors.
- One-hot encoding categorical predictors.

The resulting datasets contain 24 features each, with 8,000 training observations and 2,000 testing observations.

### Modeling Considerations
PUE was excluded from the predictors to reduce potential target leakage when predicting energy efficiency classes.

Preprocessing transformations were fitted using training data only. For cross-validation, transformations should be refitted within each training fold using a scikit-learn Pipeline.

The saved preprocessing object is generated locally and is not included in the repository.

### Modeling Results
Three models were tested with and without the PUE variable. All models performed significantly better when PUE was kept as a predictor, but Random Forest and XGBoost particularly showed promising predictive capabilities. The final selected model was XGBoost, as it minimized the proportion of classification errors on all classes. 

### Nessa Jafari was responsible for:
- Domain research
- Problem statement and data set investigation
- Explore initial findings
- Discussion and conclusion

### Hannah Rueter was responsible for:
- Data preparation and transformation
- Feature Engineering 
- Scaling/Encoding as needed

### Veronica Burke was responsible for:
- Train and fit multiple ML models 
- Compare model performances
- Prioritize appropriate evaluation metrics and select optimal model

