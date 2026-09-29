# M1 Admission Prediction & Student Performance Simulator — Python

## Overview

This project was developed as part of the **Programming for Data Science** course.

The objective was to build a complete data science workflow around the prediction of student performance and potential admission to a Master's program (M1).

The project starts with the creation of a **synthetic dataset of 500 students**, followed by data exploration, preprocessing, statistical analysis, predictive modeling and the development of an interactive prediction simulator.

Two complementary machine learning approaches are implemented:

* **Linear regression** to predict a student's final score.
* **Logistic regression** to predict the student's admission status.

The predictive models are then integrated into an interactive simulator and a **Streamlit application**.

---

## Project Objectives

The main objectives of the project were to:

* Generate and structure a synthetic student dataset.
* Explore demographic, academic and behavioral variables.
* Analyze relationships between student characteristics and performance.
* Prepare categorical and numerical variables for machine learning.
* Build a linear regression model to predict a final score.
* Build a logistic regression model to predict admission.
* Analyze regression coefficients and statistical significance.
* Create an interactive student score simulator.
* Develop a Streamlit application for prediction.

---

## Dataset

The dataset is synthetically generated using Python and contains **500 simulated students**.

It includes several categories of variables.

### Demographic and general information

* Age
* Sex
* Previous academic program
* Internet access
* Professional situation

### Study habits and well-being

* Preferred study method
* Motivation level
* Stress level
* Hours of sleep
* Sleep quality
* Hours of study per day
* Hours of classes per day

### Academic performance

* Mathematics grade
* Econometrics grade
* English grade
* Calculated academic average
* Exam difficulty
* Class attendance

### Target variables

Two target variables are constructed:

* `M1_success`: continuous predicted final score
* `admitted`: binary admission indicator based on a score threshold of 60

The data are generated programmatically using predefined relationships between several student characteristics and academic outcomes.

---

## Data Generation

The project begins by generating the student population using **NumPy** and **Pandas**.

A fixed random seed is used to ensure reproducibility.

The generated variables include:

* Demographic characteristics
* Academic background
* Study habits
* Motivation and stress
* Sleep characteristics
* Academic grades
* Attendance
* Study time

Additional variables are then constructed according to predefined relationships.

For example, sleep duration is modeled as a function of stress, while study time depends on motivation, stress, professional situation and course workload.

---

## Exploratory Data Analysis

The dataset is explored before modeling through:

* Data structure inspection
* Missing-value checks
* Descriptive statistics
* Histograms
* Categorical variable distributions
* Correlation analysis

Categorical variables are encoded to produce a complete correlation matrix.

Both ordinal encoding and label encoding are used depending on the nature of the variables.

---

## Data Preprocessing

Several preprocessing techniques are applied before training the models.

### Categorical encoding

Categorical variables are transformed using:

* Ordinal mappings for ordered variables such as sleep quality and exam difficulty.
* `LabelEncoder` for selected categorical variables.
* One-hot encoding using `pandas.get_dummies()` for model preparation.

### Feature scaling

Numerical variables are standardized using:

```python
StandardScaler
```

The same preprocessing pipeline is then reused by the prediction simulator.

---

## Predictive Modeling

### 1. Linear Regression

A **Linear Regression** model is developed to predict the continuous variable:

`M1_success`

The dataset is divided into training and test sets using `train_test_split`.

The model is evaluated using:

* R²
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)

The project also examines the regression coefficients to identify the variables associated with the predicted score within the model.

---

### 2. Logistic Regression

A **Logistic Regression** model is used to predict the binary variable:

`admitted`

The admission variable is constructed from the predicted score:

```text
admitted = 1 if M1_success ≥ 60
admitted = 0 otherwise
```

The classification model is evaluated using:

* Accuracy
* Classification report
* Predicted admission status

---

## Statistical Analysis with Statsmodels

In addition to Scikit-learn, the project uses **Statsmodels** to perform an Ordinary Least Squares (OLS) regression.

This provides a more detailed statistical analysis of the regression model, including:

* Coefficients
* P-values
* Statistical significance
* Regression summary

The project also creates a table highlighting statistically significant variables using conventional significance levels.

---

## Prediction Simulator

The trained models are integrated into a custom prediction function:

```python
simulateur_score()
```

The function then:

1. Builds an input DataFrame.
2. Encodes categorical variables.
3. Aligns the input features with the training data.
4. Standardizes numerical variables.
5. Predicts the final score.
6. Predicts the admission status.

The final output provides:

* An estimated score out of 100.
* A predicted admission status.

---

## Interactive Interfaces

Two interactive approaches were developed.

### Jupyter / Google Colab Interface

An interactive interface was created using:

```python
ipywidgets
```

It allows users to modify student characteristics through sliders, dropdown menus and selection controls and immediately obtain a predicted score and admission status.

### Streamlit Application

The project also includes a standalone **Streamlit application**.

The application provides a graphical interface where users can enter student information and request a prediction.

The interface is organized into three main sections:

* Demographic and general information
* Academic and study information
* Performance and well-being

The application then displays:

* Estimated final score
* Predicted M1 admission status

---

## Model Deployment Preparation

The trained models and preprocessing objects are saved using **Joblib**.

The repository contains serialized objects for:

* Linear regression model
* Logistic regression model
* Standard scaler
* Training feature order
* Numerical columns
* Academic programs
* Study methods
* Professional situations
* Sleep-quality mappings
* Exam-difficulty mappings

These objects allow the Streamlit application to reuse the trained models without retraining them.

---

## Technologies

| Category              | Technologies                      |
| --------------------- | --------------------------------- |
| Programming           | Python                            |
| Data manipulation     | Pandas, NumPy                     |
| Data visualization    | Matplotlib, Seaborn               |
| Machine Learning      | Scikit-learn                      |
| Statistical modeling  | Statsmodels                       |
| Interactive notebooks | Google Colab, Jupyter, ipywidgets |
| Model serialization   | Joblib                            |
| Application           | Streamlit                         |

---

## Skills Demonstrated

This project demonstrates practical skills in:

* Python programming
* Synthetic data generation
* Data preprocessing
* Exploratory data analysis
* Feature engineering
* Categorical encoding
* Feature scaling
* Linear regression
* Logistic regression
* Model evaluation
* Statistical inference
* Correlation analysis
* Interactive data applications
* Model serialization
* Streamlit application development
* Building a complete data science workflow

---

## Project Structure

```text
M1-Admission-Prediction/
│
├── Programmation_pour_la_science_des_donnees.ipynb
│
├── Presentation_projet_programmation.pdf
│
├── Application_simulateur/
│   ├── app.py
│   ├── requirements.txt
│
└── README.md
```

---

## Limitations

The project is based on a **synthetically generated dataset** rather than real student records.

Consequently, the predictions produced by the models are intended for educational and demonstrative purposes and should not be interpreted as real admission decisions.

The project also identifies a possible extension: connecting the system to a database containing collected student information and potentially using this information to establish a ranking or waiting list.

The current simulator was designed to operate locally, which limits its accessibility compared with a fully deployed online application.

---

## Possible Future Improvements

Several extensions could be considered:

* Use a real-world student dataset.
* Develop a database to store student information.
* Improve the feature engineering process.
* Compare several regression and classification algorithms.
* Perform hyperparameter tuning and cross-validation.
* Add model performance visualizations.
* Develop a more robust preprocessing pipeline.
* Deploy the Streamlit application online.
* Develop a ranking system for applicants.
* Add an interactive dashboard for admission analysis.

---

## Academic Context

This project was completed as part of the **Programming for Data Science** course during my Master's studies in **Econometrics and Statistics – Data Science**.

It combines programming, statistical analysis and machine learning concepts to develop a complete predictive application.

---

## Authors

* **Bintou Daouda GARANGO**
* **Hariane TOGNIBO**

---

## Repository Contents

The repository contains both the original analytical notebook and the files required for the interactive prediction application.

The notebook documents the complete workflow, from synthetic data generation and exploratory analysis to model development and simulator creation.

The `Application_simulateur` folder contains the Streamlit application and the serialized objects required to generate predictions.
