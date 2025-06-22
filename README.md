Multi-Label Text Classification using TITLE & ABSTRACT

This project focuses on building a robust multi-label text classification pipeline using textual data (TITLE and ABSTRACT) to predict 6 distinct labels (topics). Each input sample may be associated with one or more labels, and the problem is treated using advanced multi-output classification strategies.

Problem Overview
Task: Predict one or more topics for each article based on its title and abstract.

Data Characteristics:

Features: TITLE and ABSTRACT

Targets: 6 topic labels (multi-label)

No missing values

No duplicates

Most rows have 1–2 active labels, a few have 3 or more

Techniques Used
1. Feature Engineering
Text preprocessed using TF-IDF vectorization

Dimensionality reduced with TruncatedSVD (LSA) for efficient computation

2. Modeling Approaches
We implemented and compared different multi-label classification strategies:

Strategy	Description
MultiOutputClassifier (MOC)	Trains one classifier per label independently
Classifier Chains (CC)	Chains classifiers such that each predicts a label using all previous predictions as features
MLSMOTE	Synthetic oversampling technique tailored for multi-label imbalanced data


3. Handling Imbalance
Computed Imbalance Ratio per Label (IRPL) to identify tail labels.

Applied MLSMOTE to synthetically generate samples for underrepresented label combinations.

Tail label samples are interpolated with their nearest neighbors in feature space to increase class diversity.

Evaluation Metrics
Evaluated all models using:

Subset Accuracy: Exact match of all labels

Mean Label-wise Accuracy

Subset F1 Score

Mean Label-wise F1 Score

Hamming Loss

Key Findings
Method	Subset Accuracy	Mean Accuracy	Subset F1	Mean F1
Classifier Chain (CC)	⭐ Highest	⭐ Highest	Competitive	Competitive
MOC + MLSMOTE	Very Good	Very Good	⭐ Highest	⭐ Highest

Classifier Chain: Best overall performance on accuracy-based metrics

MOC + MLSMOTE: Achieved the best F1 performance (especially on rare labels)
