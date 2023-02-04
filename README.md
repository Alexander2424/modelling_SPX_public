# Modelling S&P500
_January 2023_
#### Note: _Code for this repository is currently private as I may use it for an upcoming academic project but will eventually be made public._

Linear regression approach to build a model that predicts daily price change for S&P500 index using technical indicators (e.g., RSI, ADX, MACD). Results compared against benchmark returns for buying daily at market open and selling at market close. Training and test datasets contain a random selection of days between 2000 and 2020 with an 80/20 split. Results are again visualised on unseen dataset (2020-2023) to compare with benchmark.

### Comments on results:
- #### linear model with no basis expansion:
  - Model appears to capture the underlying data generating function (if it exists) that maps input technical indicator values to following day price change.
  - This model generalises well to the validation and test data sets (36% of total data).
  - The model outperforms the benchmark of daily buying at market open and selling at market close.
  - Interestingly, the model performs similaraly to buying and holding the S&P500 for the past 28 years. A significant proportion of increases in the S&P500's price occur overnight while US market is closed.
  - The linear model achieves far lower volatility than buying and holding S&P500. This is due to the tuning of hyperparameters e.g., stop loss.
  - Potential future areas of investigation include modelling with Neural Networks (basic feed-forward, RNN - LSTMs). The biggest challenge in effective prediction appears to be avoiding overfitting to training data and selecting appropriate input features with predictive power.
