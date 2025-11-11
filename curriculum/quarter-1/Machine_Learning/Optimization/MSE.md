The **Mean Squared Error** is a common type of loss function, particularly for regression problems (predicting a continuous value).

The formula for MSE is:
$$
MSE = \frac{1}{n} \sum\limits_{i=1}^{n}(y_{i}-\hat y_{i})^2
$$
- The network calculates the **difference** between the true value ($y_i$​) and its prediction ($\hat y_{i}$​).
- It **squares** this difference (which ensures the result is always positive and penalizes larger errors more heavily).
- It then takes the **average** ($\frac{1}{n} \sum\limits$) of these squared differences across all data points ($n$).