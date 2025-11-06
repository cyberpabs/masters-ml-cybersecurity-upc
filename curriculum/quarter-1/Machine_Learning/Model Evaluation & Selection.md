# Model Evaluation & Selection

The process of ensuring a model generalizes well to unseen data.

## Evaluation Metrics

### For Classification
* **Confusion Matrix**: Shows True Positives (TP), False Positives (FP), etc.
![[Model Evaluation & Selection_matrix_example.png|500x400]]
* **Accuracy**: Overall fraction of correct predictions.
* **Precision**: Of all predicted positives, how many were correct: $TP / (TP + FP)$.
* **Recall**: Of all actual positives, how many were correctly identified: $TP / (TP + FN)$.
* **F1-Score**: The harmonic mean of Precision and Recall (used for balancing the two).

### For Regression
* **Mean Absolute Error (MAE)**: Average magnitude of errors. Less sensitive to outliers.
* **Mean Squared Error (MSE)**: Average of the *squares* of the errors. More sensitive to large errors/outliers.
* **R-squared ($R^2$)**: Measures the proportion of variance predictable by the independent variables. Higher is better.

## Bias-Variance Trade-off
The core tension in model building.
* **High Bias**: Model is too simple $\rightarrow$ **Underfitting**.
* **High Variance**: Model is too complex $\rightarrow$ **Overfitting** (fits the noise in the training data).
* **Goal**: Find the sweet spot that minimizes both.
![[variance_bias_tradeoff_example.png]]

## Model Selection: Cross-Validation

Used to estimate generalization performance on new data by testing the model on different subsets of the data.

### K-Fold Cross-Validation
1.  Split the dataset into $k$ subsets/folds.
2.  Train the model $k$ times, each time using one fold for testing and the rest ($k-1$ folds) for training.
3.  Average the error/accuracy across all $k$ runs.
4.  Choose the model with the best average score.
![[cross_validation_kfold.png]]