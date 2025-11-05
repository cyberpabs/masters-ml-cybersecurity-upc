# Data Preparation for ML Tasks

This is the most time-consuming but crucial part of the ML pipeline.

## Data Quality (The Six V's)
Good data must be:
* **Accuracy**: Must be true and reflect real-world events.
* **Completeness**: Must provide all necessary values.
* **Consistency**: Homogeneous across different sources.
* **Timeliness**: Readily available and updated when needed.
* **Uniqueness**: No duplicate records.
* **Validity**: Compliant with policies, correct formats, and within defined ranges.

## Handling Imperfections

### Missing Values (Imputation)
* **Deletion**: Remove the rows or columns with missing data.
* **Imputation**: Fill using a **placeholder value**, the **mean** or **median**, or a **prediction model**.

### Outliers
Values significantly different from others. Use statistical methods (IQR, Z-score) to detect them.
* **Handling**: Can be **removed** (if they are errors), **transformed** (e.g., logarithmic scaling), or **imputed**.

## Feature Engineering

### Feature Scaling
Ensures no single feature disproportionately influences the model due to a larger numerical range.
* **Normalization (Min-Max)**: Rescales features to a fixed range, usually 0 to 1.
* **Standardization (Z-score)**: Rescales data to have a mean of 0 and a standard deviation of 1.

### Other Techniques
* **Discretisation (Binning)**: Converting continuous variables into discrete intervals (e.g., age $\rightarrow$ age groups).
* **Data Augmentation**: Creating new training data from existing data (common in image processing).

## Data Governance
Crucial for ethical and legal compliance (GDPR/CCPA). Involves defining policies on data retention, usage, and ownership.