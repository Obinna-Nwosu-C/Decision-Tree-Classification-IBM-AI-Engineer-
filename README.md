 Decision-Tree-Classification-IBM-AI-Engineer

 💊 Drug Prescription Prediction using Decision Trees

[Python](https://img.shields.io/badge/Python-3.14-blue?logo=python)
[Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.6.0-orange?logo=scikit-learn)
[Pandas](https://img.shields.io/badge/Pandas-2.2.3-150458?logo=pandas)
[License](https://img.shields.io/badge/License-MIT-green)

Project Overview
This project explores the application of Decision Tree Classification to predict the appropriate medication for patients based on their health parameters. Acting as an "automated medical flowchart," the model analyzes patient data to accurately classify which of 5 distinct drugs (Drug A, B, C, X, or Y) a patient should be prescribed. 

The primary advantage of using a Decision Tree for this exercise is interpretability - allowing medical professionals to understand and trust the exact logic the AI uses to make life-impacting decisions.

The Dataset
The dataset consists of 200 patient records with the following features:
Age: Patient's age (Numerical)
Sex: Patient's biological sex (Categorical: M/F)
BP: Blood Pressure level (Categorical: High, Low, Normal)
Cholesterol: Cholesterol level (Categorical: High, Normal)
Na_to_K: Sodium to Potassium ratio in the blood (Numerical)
Target (Drug): The prescribed medication (A, B, C, X, or Y)

Methodology & Workflow

1. Data Preprocessing
  Handled categorical variables using `LabelEncoder` from Scikit-Learn to convert text data (e.g., "High", "Low") into machine-readable integers.
  Verified the dataset for null/missing values (Dataset was 100% clean).
  Conducted Exploratory Data Analysis (EDA) to check feature correlation and class distribution.

2. Model Training
  Split the data into training (70%) and testing (30%) sets.
  Trained a `DecisionTreeClassifier` using the Entropy criterion to measure information gain.
  Set a `max_depth` of 4 to prevent overfitting while allowing enough complexity to capture the medical nuances.

3. Evaluation & Interpretability
  Achieved an outstanding **98.33% accuracy** on the test set (correctly identifying 59 out of 60 test samples).
  Extracted the explicit decision rules from the tree to create a transparent, step-by-step medical checklist.

The Decision Logic (How the Model "Thinks")
Unlike black-box models, we can extract the exact logic the tree uses to prescribe medication:

| If the patient has... | ...they get prescribed: |
| High Sodium-to-Potassium ratio (`Na_to_K > 14.63`) | Drug Y |
| Low ratio + High BP + Age ≤ 50.5 | Drug A |
| Low ratio + High BP + Age > 50.5 | Drug B |
| Low ratio + Low BP + High Cholesterol | Drug C |
| Low ratio + Normal BP OR Normal Cholesterol | Drug X |

Key Insights & Hyperparameter Tuning
To understand the importance of model complexity, I experimented with the tree's depth:
  Max Depth = 4: Accuracy = 98.33% (Optimal)
  Max Depth = 3: Accuracy = 81.67% (Underfitting)

Takeaway: Reducing the depth by just one level caused the model to lose the ability to differentiate between the final sub-categories of drugs, proving that the 4th level of diagnostic questions is critical for this specific dataset.

Clear Explanation of the Exercise:

The Problem: 
Imagine you are a medical researcher. You have data on 200 patients who all suffered from the same illness, but they responded to 5 different medications (Drug A, B, C, X, and Y). The goal is to build a machine learning model that acts like an "automated doctor," looking at a new patient's health metrics and accurately prescribing the exact right drug.

The Approach: 
I used a Decision Tree Classifier. I chose this algorithm because, unlike "black box" models (like neural networks), a decision tree mimics human logic. It makes a series of Yes/No questions to narrow down the answer. 

The Data & Preprocessing:
The dataset contained 5 features: Age, Sex, Blood Pressure (BP), Cholesterol, and the Sodium-to-Potassium ratio (Na_to_K). Since machine learning models only understand numbers, I converted the text categories (like "High" or "Low") into numerical codes using Label Encoding. I also checked for missing values (there were none) and looked at the data distribution to ensure no drug was heavily underrepresented.

The Results & The "Logic":
I trained the model with a maximum depth of 4 (meaning it can ask up to 4 questions in a row). The model achieved a fantastic 98.33% accuracy on unseen test data. 

Because it's a decision tree, we can look exactly at how it makes decisions. It turns out the Na_to_K ratio is the ultimate deciding factor:
    If the Na_to_K ratio is high (> 14.63), the model immediately prescribes Drug Y.
    If the ratio is low, it checks Blood Pressure. 
    If BP is High, it checks Age (under 50 gets Drug A, over 50 gets Drug B).
    If BP is Low/Normal, it checks Cholesterol to decide between Drug C and Drug X.

Key Insight:
I also tested what happens if we restrict the model's "thinking" by reducing the tree depth to 3. The accuracy dropped significantly to 81.6%. This proved that the 4th level of questions was absolutely necessary to accurately distinguish between the final few drugs.

Course Participant/Code Executor: Obinna Nwosu C, Author: Jeff Grossman, Other Contributor(s): Abhishek Gagneja, © IBM Corporation. All rights reserved.
