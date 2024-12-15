Credit Card Fraud Detection

This README file provides guidance to navigate the project files and code effectively.

--------------------------------------------------------------

Table of Contents

- Folder Contents
- Setup
- Execution

--------------------------------------------------------------

Folder Contents
The project folder includes 2 subfolders and 2 Jupyter Notebook files.

1. Fraud Dataset Folder: Contains 3 files – 2 CSV files and 1 Jupyter Notebook (.ipynb) file.  
2. Feature Generated Dataset Folder: Contains 3 files – 2 CSV files and 1 Jupyter Notebook (.ipynb) file.  

The primary file to run is Model with Coefficients.ipynb, which represents the latest version of the model.

--------------------------------------------------------------

Setup
The models are configured to run on Kaggle, while feature generation is designed to work locally, and EDA (Exploratory Data Analysis) is tailored for Google Colab. 

General Setup
Ensure the project folder structure remains unchanged after extraction.

Model Setup
To run models on Kaggle:
1. Upload Model with Coefficients.ipynb.  
2. Upload train_dataset.csv and test_dataset.csv from the Feature Generated Dataset folder.

Note: Avoid using the raw dataset from the Fraud Dataset folder, as it lacks the generated features.

Feature Generated Dataset Setup (Optional)
To recreate the feature-generated dataset:
1. Run Feature generation.ipynb from the Feature Generated Dataset folder locally.  
2. Keep the folder structure unchanged to avoid errors.  

Generated files (train_dataset.csv and test_dataset.csv) will appear in the same directory as the notebook after execution.

EDA Setup (Optional)
To recreate EDA results:
1. Run EDA.ipynb from the Fraud Dataset folder on Google Colab.  
2. Update the working directory path as required (e.g., %cd /content/drive/MyDrive/...).  

Ensure file paths align with your directory structure to avoid errors.

--------------------------------------------------------------

Execution
The main file to execute is Model with Coefficients.ipynb on Kaggle.  
- Under Accelerator, select GPU T4 x2.

Steps to Recreate Results
1. Run all cells in Model with Coefficients.ipynb.  
2. Note: Execution may take approximately 1 hour and 30 minutes due to hyperparameter tuning.  

For Faster Execution:  
- Comment out hyperparameter tuning sections and adjust the following lines in the fifth-last cell:  
  model_metrics_list.append(rf_tuned_model_metrics)
  model_names.extend('Tuned Random Forest')
  model_metrics_list.append(lgr_tuned_model_metrics)
  model_names.extend('Tuned Log Regression')

Model Coefficients
The current setup optimally outputs model coefficients. Other methods resulted in bugs that affected the display of coefficients. We appreciate your understanding of this limitation.  

--------------------------------------------------------------

This guide aims to simplify navigation and execution of the project files for seamless workflow.
