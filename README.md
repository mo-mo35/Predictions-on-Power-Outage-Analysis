# Predictions-on-Power-Outage-Analysis
Project for UCSD DSC80

## Framing the Problem

In this analysis I aim to predict the number of customers affected based on various attributes using linear regression. 
I chose to predict the customers affected since I believe that is the most detrimental aspect of power outages. I'll be evaluating the model using
root mean squared error to see the exact error rather than correlation. Since this dataset is mostly made up of variables that
are found after the outage is restored, many features were left out, e.g. Outage Duration, Cause, Demand Loss etc. 

## Baseline Model

My baseline model uses cross validation and only two features—the number of industrial and commercial customers—to predict the number of customers affected by an outage.
Both features were quantitative and required no necessary encodings. I believe the performance of my model was not good since the error was much higher 
than the average amount of customers affected.

## Final Model

My final model uses an additional two features created by one-hot encoding the climate category, and binarizing the energy drawn from the state as either large or small amounts.
I added these to my model because it seemed to be two potential causes to a power outage: extreme weather, and high strain on the power grid.
Additionally these are available before the end of the power outage and are much more useful than other attributes. 

I manually used different combinations of these 4 features as well as cross validating with 5 folds to find the optimal 
model, which ended up being a model including all 4 features. Using this optimal model improved performance and lowered 
the error in both training and testing sets from the previous less complex model. 

## Fairness Analysis

To test fairness I chose to binarize the instances where residential usage was higher than non-residential usage. I continued using the same
metric—root mean squared error—to test how fair my model is. 

#### Null Hypothesis: 
The model is fair and its error is roughly the same for both groups.

#### Alternative Hypothesis:
The model is biased and its error is higher when predicting for non-residential usage.

#### Significance level: 0.01

The resulting p_value was 0, meaning that the model is extremely prone to error in predicting customers affected when non-residential usage is higher than residential usage and we reject the null hypothesis



