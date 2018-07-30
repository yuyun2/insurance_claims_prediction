## Health Insurance Claim Predicition

Diabetes is a highly prevalent and expensive chronic condition, costing about $330 billion to Americans annually. Most of the cost is attributed to the ‘type-2’ version of diabetes, which is typically diagnosed in middle age.

The goal of this project is to predict which of the insurance company's members are most likely to be newly-diagnosed with type-2 diabetes in 2017 and file an insurance claim. 

## Data
The data provided are real patient claims records from a large insurance company and it is stored in semi-structured Jason blobs. The data is consisted of basic demographic information, the diagnoses, medications, and procedures that were noted/prescribed/performed at each doctor’s visit and the lab tests that were completed by each member. 

## Challenges
* Data Processing: extracted relevant information from a collection of semi-structured JSON blobs containing medical records for 100K+ patients, and created a set of structured relational tables (SQLite).  
* Feature engineering: each member has completed different procedures and labs, generated three classes of features - frequency, duration, and feature based on claim rate. 
* Model Evluation Metirc Selectio: since data is highly unbalanced, claim rate is arppocimately about 4%, chose the AUC, precision at 20 recall and average precision as the model evaluation metrics. 

## Modeling
Attmpted to generated predictions using random forest and XGBoost, and ensemble of these two models for this project. Finally, XGBoost was choosen because it gave the best performance. 
## Result
* Achived AUC of 0.795. 
* The five most important features are:

	1. Age, this is in accordance with research by American Diabetes Association.

	2. Average value of test loinc_4548-4, which tests the patients Hemoglobin level in blood.

	3. Number of days since last resource code cpt_83036. This is also related with Hemoglobin level.

	4. Number of resource code icd10_I10. The code is related with hypertension, which is the most common comorbid condition in diabetes.

	5. Number of days since last doctor visit. A recent doctor visit might indicate a claim. 

## Notebooks
The *notesbooks* directory contained two ipython notebooks - code for data processing and modeling process. 

## Installation
Run following code to create an environment for this project. 

	conda create -n myenv python=3.4
	source activate myenv
	pip install -r requirements.txt 
