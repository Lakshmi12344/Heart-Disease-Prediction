# Heart Disease Prediction (Python, scikit-learn)

Predicts whether a patient has heart disease from clinical measurements, using the Heart Failure Prediction dataset from Kaggle (918 patients, 917 after cleaning).

> Learning project. Not a medical diagnostic tool.

## Tools
Python, pandas, matplotlib, seaborn, scikit-learn, Google Colab

## Steps
1. Cleaned the data: removed 1 row with 0 blood pressure, converted 172 zero cholesterol values to missing (171 after the row removal) and flagged them
2. Explored heart disease rate by sex, chest pain type, exercise angina, ST slope, age, heart rate and Oldpeak
3. Split the data first, then filled missing cholesterol with the training median and scaled numeric columns, to avoid data leakage
4. One-hot encoded categorical columns
5. Trained Logistic Regression and Random Forest, and checked stability with 5-fold cross-validation

## Results (heart disease class, 184 test patients)
| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Logistic Regression | 0.89 | 0.89 | 0.91 | 0.90 |
| Random Forest | 0.88 | 0.89 | 0.89 | 0.89 |

Logistic Regression is the final model. It caught 93 of the 102 patients with heart disease and missed 9. Random Forest performed similarly, and 5-fold cross-validation recall was 0.88 vs 0.89 (spread about 0.04), so the two models are effectively tied. Logistic Regression was chosen because it is simpler to explain and had the highest recall on the test set.

## Key Insights
- About 55% of patients have heart disease.
- Patients with missing cholesterol records had an 88% heart disease rate vs 48% for recorded ones, likely a data-collection quirk.
- Higher risk: flat ST slope, higher Oldpeak, exercise angina, older age, lower maximum heart rate.
- Top Random Forest features: ST slope, Oldpeak, MaxHR, ExerciseAngina.
- Logistic Regression is the final model: 0.89 accuracy, 0.89 precision and 0.91 recall on 184 held-out patients (it caught 93 of 102 patients with heart disease and missed 9).
- Random Forest performed similarly (0.88 accuracy, 0.89 recall), and 5-fold cross-validation recall was 0.88 vs 0.89, so the two models are effectively tied.
- This is a learning project, not a medical diagnostic tool.

## How to Run
1. Download heart.csv from the Kaggle dataset below.
2. Open Heart_Disease_Prediction.ipynb in Google Colab.
3. Upload heart.csv when Colab asks, and run all cells.

## Dataset
Heart Failure Prediction Dataset (Kaggle, by fedesoriano)
