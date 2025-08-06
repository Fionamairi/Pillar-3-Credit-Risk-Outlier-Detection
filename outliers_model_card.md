# Model Card

## Model Description

**Input:** The model takes numeric features from the CR6 tables published in the Pillar 3 disclosures made by UK banks for all available exposure classes. The variables included are: Original exposure (On balance sheet); Original exposure (Off balance sheet); Average CCF; Exposure at default (post CCF); Average Probability of Default (PD); Obligor number, Average loss given default (LGD), Average maturity, Risk Weighted Assets (RWA), RWA as a percentage of EAD, Expected loss (EL), Provisions. Each row of data is tagged with metadata including the name of the bank, the name of the Pillar 3 table and the exposure class the data relates to.

**Output:** The models output is a binary label for each row: 1 = normal observation; -1 = outlier.
It also outputs scores which represent the confidence of the prediction (lower scores = more anomolous)

**Model Architecture:** Two unsupervised models are used:
Isolation forest - detects outliers by isolating the points that give fewer splits in random decision trees. Hyperparameters optimised are n_estimators, max_samples, contamination and max_features.
One-Class SVM - learns a boundary around "normal" data and flags any points outside of this boundary as outliers. Hyperparameters optimised are nu and gamma.

Hyperparameter optimisation was performed using Optuna.

## Performance

Performance was evaluation based on oulier detection behavious, including:
- Outlier counts per model and fold
- Consistency of detected outliers across K-fold cross-validation

## Limitations

There are no labelled outliers, true or false positives and true or false negatives are unknown.
Anomalies may be over or under detected depending on hyperparameter tuning, in particular contamination or nu settings.
One-Class SVM is computationally intensive, so this may become operationally infeasible as the dataset grows.


## Trade-offs

Sensitivity v specificity - increasing contamination or nu will flag more outliers but also may increase false positives;
Isolation Forest scores are interpretable using the path lengths, however it is more difficult to isolate the drivers behind the One-Class SVM scores
One-Class SVM performance varies more across folds, whereas Isolation Forest is more stable.
Domain expertise will be required to understand drivers and validate model performance and results.
