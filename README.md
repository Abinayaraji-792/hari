In this project, I built a complete time-series forecasting system using State-Space Models and the Kalman Filter, and I compared it with a traditional SARIMA model. The goal was to create my own synthetic dataset, estimate hidden states, learn model parameters, and evaluate forecasting performance.

1. Data Generation

I created a custom dataset with 600 time steps, which includes:

A linear trend

A sinusoidal seasonality pattern

Gaussian noise

I also defined and printed the true parameters (trend, seasonal coefficients, noise levels) so I could later compare them with the estimated values. This helps prove whether the Kalman Filter is learning correctly.

2. State-Space Model

I designed a 4-state model that captures:

Level

Trend

Sine seasonal component

Cosine seasonal component

I defined both:

The observation equation (how data is observed), and

The transition equation (how hidden states evolve over time).

3. Kalman Filter Implementation

I implemented the full Kalman filtering process:

Prediction step

Update step

Kalman gain calculation

Log-likelihood computation

Rauch–Tung–Striebel smoother

This allowed me to estimate the underlying states and later use them for forecasting.

4. Parameter Estimation (MLE)

Using Maximum Likelihood Estimation (MLE), I optimized the model to learn:

Trend slope

Seasonal strengths

State and measurement noise levels

I compared the estimated parameters with the true parameters, and the results were very close — which means the Kalman filter learned the system correctly.

5. Model Comparison

To evaluate performance, I compared:

Kalman Filter (with MLE-learned parameters)

Kalman Filter (using true parameters)

SARIMA baseline model

I calculated:

RMSE

MAE

MAPE

The Kalman Filter achieved much better performance than SARIMA. SARIMA struggled because the synthetic data had complex seasonality and hidden dynamics that Kalman models handle more naturally.

Final Result

The Kalman-based model produced:

Very low RMSE

High accuracy forecasts

Smooth state estimates

Parameters that closely match the true data-generation process
