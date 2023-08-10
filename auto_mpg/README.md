# Car MPG prediction

The purpose of this project is to develop a model that accurately predicts the car fuel consumption or mpg.
The data used for this project can be found on the [UCI Datasets archive site](https://archive.ics.uci.edu/dataset/9/auto+mpg).

The dataset contains 406 entries and 7 attributes. The task is to predict the 'mpg' (which is continuous ) attribute.

## The project structure:

### 1. Read the data

This section is straight forward, we import the required dependencies, read the data, and gain a sense on what we're working with (what do the variables mean and in what units are they measured)

### 2. Clean the data

In this section we focus on handling missing values, the data contains 406 initial entries out of which only 398 have the 'mpg' attribute. Further, 6 entries miss the 'horsepower' attribute and we manually populated this attribute using online data.

### 3. Transform the data

Here we've done a couple of steps:
* Converting origin, which is categorical to one-hot representation
* Assigning proper data types for the attributes (e.g mapping floating points to ints)
* Handling manufacturer misspellings (initially we wanted to also include info about the manufacturer but since we only have 398 examples we've decided not to)

### 4. Explore the data

We begin data exploration by examining the distribution of each attribute and then continue with bivariate analysis.

### 5. Model the data

To model the data we've analyzed different algorithms. We've started with a simple linear regression model into which we've fed all the variables.
We then proceeded to remove the variables whose contribution wasn't statistically significant (p-val > 0.05) and further transformed the target to match
the model's assumption that the data is homoscedastic and the residuals are normally distributed.

We then proceed to select other models such as ElasticNet and SVR (support vector regressor) and perform grid search as well as cross-validation to
find the best params for them.\
For SVR we've obtained a train R^2 of **0.926** and test R^2 of **0.911**.\
For OLS linear regression we've obtained a train R^2 of **0.877** and test R^2 of **0.885**.\
Thus, we can conclude that both models have learned a robust representation of the problem.