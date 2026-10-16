# Predicting *Apis mellifera* Pesticide Toxicity Using Machine Learning

## Project Overview

Pesticide exposure is a major concern for honeybee populations, which play an important role in ecosystem stability and agricultural pollination. Identifying potentially toxic chemical compounds is essential for supporting environmental safety and reducing harm to bee populations.

This project develops and compares machine learning models to classify chemical compounds as **toxic or non-toxic to honeybees (*Apis mellifera*)** using the ApisTox dataset from the UCI Machine Learning Repository. Molecular descriptors and agrochemical attributes are used to identify patterns associated with pesticide toxicity.

## Objectives

- Develop machine learning models for binary pesticide toxicity classification.
- Extract molecular descriptors from chemical SMILES representations using RDKit.
- Compare the performance of multiple classification algorithms and ensemble methods.
- Optimize model performance through hyperparameter tuning.
- Evaluate models using metrics suitable for an imbalanced classification problem.

## Dataset

**Source:** [ApisTox — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/995/apistox)

ApisTox contains chemical compound data related to toxicity in honeybees. The dataset supports the investigation of relationships between molecular properties, agrochemical characteristics, and toxicity outcomes.

The target variable represents two classes:
- **Toxic:** Chemical compounds classified as toxic to honeybees.
- **Non-Toxic:** Chemical compounds classified as non-toxic to honeybees.

## Methodology

### 1. Data Preprocessing
- Checked for missing values and duplicate records.
- No missing or duplicate values were found in the dataset, according to the analysis.
- Prepared the data for exploratory analysis and model development.

### 2. Exploratory Data Analysis (EDA)
Exploratory analysis was conducted to understand:
- The distribution of toxic and non-toxic compounds.
- Toxicity patterns across agrochemical categories.
- The distribution of compounds across `toxicity_type` categories.
- The distribution and potential outliers of molecular weight (`MolWt`).
- Correlations between molecular descriptors.

### 3. Feature Engineering and Selection
Chemical SMILES representations were processed using **RDKit** to extract molecular descriptors, including:

- `MolWt` — Molecular weight
- `TPSA` — Topological polar surface area
- `MolLogP` — Molecular lipophilicity
- `NumHDonors` — Number of hydrogen-bond donors
- `NumHAcceptors` — Number of hydrogen-bond acceptors

These descriptors provide molecular-level information for predicting chemical toxicity.

### 4. Model Development
The dataset was split into **70% training data and 30% testing data**.

The following classification algorithms were evaluated:
- Random Forest
- Logistic Regression
- Decision Tree
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)

Hyperparameter tuning was performed to improve model performance. Ensemble approaches, including Bagging with KNN and Voting classifiers, were also investigated.

### 5. Model Evaluation
Because the dataset exhibits class imbalance, **F1-score** was selected as the primary evaluation metric to balance precision and recall.

Additional evaluation included:
- Area Under the Receiver Operating Characteristic Curve (ROC-AUC)
- ROC curve comparisons
- Feature importance analysis
- Comparisons of model performance before and after hyperparameter tuning

## Results

The experiments produced the following key findings:

| Model | Result |
|---|---|
| Random Forest baseline | F1-score: 0.69 |
| Tuned K-Nearest Neighbors | F1-score: 0.70 |
| Random Forest | ROC-AUC: 0.84 |
| KNN Bagging ensemble | F1-score: 0.69 |

After hyperparameter tuning, KNN achieved the highest reported F1-score of **0.70**, outperforming the baseline models. Random Forest also demonstrated strong discrimination performance, achieving an ROC-AUC of **0.84**.

These results suggest that different algorithms offer different strengths depending on the evaluation metric. KNN performed best in terms of F1-score, while Random Forest showed strong ROC-AUC performance.

## Conclusion

This project demonstrates the potential of machine learning for predicting pesticide toxicity to honeybees using molecular descriptors and agrochemical attributes. Feature engineering from SMILES representations provided useful chemical information for classification, while hyperparameter tuning helped improve model performance.

Although the best reported F1-score was 0.70, the results highlight the potential of data-driven toxicity prediction as a preliminary screening tool for identifying potentially harmful compounds. Further improvements could explore additional molecular representations, more extensive feature selection, and strategies for handling class imbalance.

**Note:** Model predictions should complement, rather than replace, laboratory toxicity testing and ecological risk assessments.

## Tools and Technologies

- **Programming:** Python
- **Data Analysis:** Pandas, NumPy
- **Chemical Informatics:** RDKit
- **Machine Learning:** Scikit-learn
- **Visualization:** Matplotlib, Seaborn

## Authors

- Aaron Jeremy Alexander
- Angela Kei Budiwinoto
- Bella Nadya Aurelia
- Ivana Joyceline

## References

1. Adamczyk, J., Poziemski, J., & Siedlecki, P. (2025). *ApisTox: a new benchmark dataset for the classification of small molecules toxicity on honey bees*. Scientific Data, 12, 5. https://doi.org/10.1038/s41597-024-04232-w
2. UCI Machine Learning Repository. (2023). *ApisTox: A dataset for bee toxicity prediction*. https://archive.ics.uci.edu/dataset/995/apistox
3. Yang, P., Henle, E. A., Fern, X. Z., & Simon, C. M. (2022). Classifying the toxicity of pesticides to honey bees via support vector machines with random walk graph kernels. *The Journal of Chemical Physics, 157*(3).
4. Wang, F., et al. (2020). Graph attention convolutional neural network model for chemical poisoning of honey bees’ prediction. *Science Bulletin, 65*(14), 1184–1191.
