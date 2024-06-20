## ML Workflow on Breast Cancer Wisconsin Data Set

https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data?resource=download

#### Author: Andy Crossman

- This dataset contains features of breast mass cell nuclei and whether that mass was M(malignant) or B(benign).
- The features are the mean, standard error, and largest value for 10 attributes of cell nuclei in that sample.
- I will analyze the dataset and preprocess it. NOTE: this Kaggle dataset comes with no missing values.
- Once the dataset is understood and processed, I will train a binary classification model.
- A test set will be held out from training to determine the model's generalization capability on cell mass classification.
- Feature Importance will be performed to understand which features are the best predictors in the trained model.

## Conclusion

#### Reducing False Positive Rate

- To reduce false positives, the following actions were taken:
  - Increased Malignant(-1) misclassification penalty for training. A 20:1 (Malignant: Benign) penalty ratio was used.
  - When predicting on the test set, a threshold of 0.9 was used for classifying a cell mass as Benign (1).
  - This emphasis on reducing false positives actually decreased accuracy because several more examples were classified as false negatives as a result.

#### GridSearch

- Best Parameters: {'C': 100, 'degree': 1, 'gamma': 0.01, 'kernel': 'rbf'}
- Best Estimator Cross Validation Accuracy: 0.9670326478447775

#### Accuracy

- The trained SVM achieved an accuracy of 0.95.

#### Feature Importance

- Several features actually had a negative impact on the test accuracy which confirms the notion that mean, standard error, and largest values across these features are correlated.

#### Next Steps

- The results indicate I achieved a Precision of 1, which is ideal in this task. I wanted to reduce the risk of False Positives as much as possible. Consulting physicians for a proper threshold would be ideal, as I am currently just using 0.9 as a threshold value.
- The feature importance graph indicates that several features may actually just hold redundant information, so a new model with dropped features would be ideal.
