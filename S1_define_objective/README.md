# Exploring Regression Metrics (Loss functions)
## MAE (Mean Absolute Error)

$$ MAE(y^{true}, y^{pred}) = \frac{1}{n} \sum_{i=1}^{n}|y^{true}_{i} - y^{pred}_i|$$

It is the mean of the absolute value differences between the ground truth $y^{true}$ and the 
predicted labels $y^{pred}$.

## MSE (Mean Squared Error)

$$ MSE(y^{true}, y^{pred}) = \frac{1}{n} \sum_{i=1}^{n}(y^{true}_{i} - y^{pred}_i)^2 $$

It is the mean of the squared differences between the groud truth and the models predictions.

## Huber Loss

$$ Huber_{\delta}(y^{true}, y^{pred}) = \frac{1}{n}\sum_{i=1}^n\begin{cases}\frac{1}{2} a^{2} & 
\text { for }|a| \leq \delta \\ 
\delta 
\cdot\left(|a|-\frac{1}{2} \delta\right), & \text { otherwise }\end{cases} $$
