# LOS-Hospital-Prediction-model-
Analyzes Hospital data to predict patient Length of Stay (LOS) using regression modeling and feature engineering. Data cleaning, encoding, and visualization are applied to uncover key predictors and support healthcare decision-making.Team: Me( Sourabh saini) ,Maximilian, Tobias, Raghvendra.


Research Question

Can we predict a patient's hospital stay duration from the number of visitors and the patient's age?


Dataset
The analysis uses a fictional hospital dataset (Topic3_healthcare_analytics_dataset.csv) containing information about individual patient stays across multiple hospitals. The full dataset totals 455,495 rows, of which 318,438 rows constitute the training data (rows where the Stay column is populated). The remaining rows are Kaggle test data and are excluded from this analysis.

Notebook Structure
1. Package Import
Dependencies: pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn
2. Data Import & Initial Exploration

Loads the dataset and generates summary statistics
A 1,000-row test subsample was used during development for faster iteration

3. Data Cleaning
StepApproachTraining/test separationRows 0–318,437 used; test rows droppedMissing valuesRows with missing data dropped; City_Code_Patient filled with -1 dummyCategorical encodingAge and Stay range strings (e.g. "11-20") encoded as midpoint values (e.g. 15)OutliersIQR and Z-score functions implemented; not applied (no significant outliers found)PipelineAll preprocessing steps consolidated into preprocessDataPipeline()
4. Problem Statement
Hospital stay duration is a high-value prediction target — accurate forecasts enable better resource planning (room assignments, staffing, food, cleaning). The team identified Visitors with Patient and Age as the strongest candidate predictors.
5. Data Analysis

Value Scaling: All numeric features standardized using StandardScaler
Linear Regression: Individual and combined predictor models evaluated using:

Mean Squared Error (MSE)
StatsModels OLS summary (p-values, R²)



Key result: The combined model using Visitors with Patient and Age as predictors yields:

p-value < 0.001 — statistically significant relationship confirmed
MSE = 0.7118 — strong predictive performance

6. Data Visualization
Plots generated with matplotlib and seaborn:

Scatter: Age vs. Visitors with Patient (coloured by Stay)
Line: Age vs. Stay
Line: Visitors with Patient vs. Stay
Count: Patient distribution by Department
Relplot: Age vs. Stay sized by Admission Deposit, coloured by Department


Key Functions
FunctionPurposecreateDataStatistics(df)Generates a summary statistics table per columnpreprocessDataPipeline(...)Runs the full cleaning and encoding pipelinehandleMissingEntries(df)Fills/removes missing valuesencodeData(df)Encodes Age and Stay range strings to numeric midpointshandleOutliers(...)IQR/Z-score based outlier detection and handlingscaleData(df)Applies StandardScaler to all numeric columnslinearRegression(...)Fits and evaluates a linear regression modelanalyseColumn(...)Runs regression analysis on a specified target/predictor pair
