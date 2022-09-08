# Objective
The aim of the project is to create a log-log regression model using the sales data for each and every spf (variant of a prodcut) and identify the coefficient values of the independent features which are actually the elasticiy numbers in a log- log model. Elasticity numbers indicates the change in one variabe (in this case demand) in response to the change in other variables (in this case the focus is mainly on the price variables). 
# Methodology
Implemented Bayesian Regression for two main reasons. Firstly, the input data is at a weekly level which is why the number of data points were quite less. Secondly, the final coefficients (elasticity numbers) are restricted to attain values in a defined range.
Two variations of Bayesian Regressions are tested -
## Bayesian Regression for each spf - Different models are created for different spfs
*Used the coefficients from the OLS run as the priors
*Designed a customized function to update the coefficients iteration after iteration such that they do not go beyond the defined range. Also, the function in sensitive to the priors value and the correlation between the feature and the error (actual - predicted)
## Hierarchical Bayesian Regression - One high level single model for all the spfs (no pooling). This ensured inclusion of random effects while model building. The model used No U Turn Sampler (NUTS) from MCMC family to draw from posterior distribution.
*Incorporated business logic into the model using hyperpriors, priors and bound for posterior distribution
*Distributions of hyperpriors are defined to get multiple distribution of the priors for different spfs
*This enabled to integrate information from different units or groups using hyperpriors
*This also helped to simulate future scenarios using sampling from posterior distributions

# Conclusion
Final Model was selected for each spf based on best R_square and MAPE values. In many cases Hierarchical Bayesian Regression gave better results in comparison to the other variation of Bayesian regression
