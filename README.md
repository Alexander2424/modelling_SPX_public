# Modelling S&P500
_January 2023_
#### Note: _Code for this repository is currently private as I may use it for an upcoming academic project. I can share full code repository with any potential future employer_

Linear regression approach to build a model that predicts daily price change for S&P500 index using technical indicators (e.g., RSI, ADX, MACD). Results compared against benchmark returns for buying daily at market open and selling at market close. Training and test datasets contain a random selection of days between 2000 and 2020 with an 80/20 split. Results are again visualised on unseen dataset (2020-2023) to compare with benchmark.

### Comments on results:
- #### linear model with no basis expansion:
  - Model appears to capture the underlying data generating function (if it exists) that maps input technical indicator values to following day price change.
  - This model generalises well to the randomised test set of days between 2000 and 2020. Additionally, the model outperforms the benchmark between 2020 and 2023 on unseen data (see figure _linear_model.py_).
  - Interestingly between 2020 and 2023 even though the model outperforms the benchmark (24% vs 7%), buying and holding S&P500 for this duration (without daily trades) yields the best result (26%). This suggests a large portion of market returns are accumulated overnight during market close.
- #### linear model with basis expansion {x}->{x,x^2}:
  - Model is too complex, it captures the noise in the training data set leading to poor generalisation despite great performance on training set.
  - This model overfits, as evidenced by a much better performance on the training set than test set. Additionally, the model does not outperform the benchmark between 2020 and 2023 on unseen data (see figure _linear_model_basis_expansion.py_), further adding evidence to the likelihood of overfitting.

### Conclusions
Daily price change prediction for S&P500 index appears to be successfully modelled (compared with benchmark returns) using linear regression approach (without basis expansion) with selected technical indicators as input parameters. However, more in depth statistical analysis needs to be done on the results to deliver the probability of the correctness of the model (using the PAC framework for learning in formal Learning Theory). There exists uncertainty as to whether the linear model without basis expansion will continue to perform well on unseen data.

The more complex model with basis expansion can be discarded as it clearly overfits, though it would be interesting to apply this model again with L2 norm regularisation.

Potential future areas of investigation include modelling with Neural Networks (basic feed-forward, RNN - LSTMs). The biggest challenge in effective prediction appears to be avoiding overfitting to training data and selecting appropriate input features with predictive power.
