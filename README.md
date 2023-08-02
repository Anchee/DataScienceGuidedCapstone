# DataScienceGuidedCapstone

## Data Science Guided Capstone Project Documentation
### Problem Statement

The project aims to solve advise management on the optimal resort prices so that the facilities have higher utilization rate and different facilities can be charged with a different price depending on the importance, to increase profit for the resort, by the end of the season. 



### Data Wrangling

The dataset used for this project is sourced from a CSV file retrieved from the database manager. It contains per resort data with various features describing each resort. Initially, the dataset consisted of 300 rows. However, to ensure data quality and model effectiveness, certain preprocessing steps were applied:

#### Removing fastEight feature: 
The "fastEight" feature, which contains a substantial number of null values, was removed from the dataset as it lacked sufficient data to be informative.

#### Removing rows with missing price data: 
Rows with no price data for either the Weekday price or Weekend price were removed. This step ensured that we work with complete and relevant information for the modeling process.

After these data cleaning operations, the dataset was reduced to 277 rows, which now forms the foundation for further analysis and modeling.

### Exploratory Data Analysis

After some exploratory analysis of the data, we find that there is a big variation between state and ticket price. The total number of numerical features included is 28. Among the features, from the correlation plot, fastQuads, Runs and Snow Making_ac stand out. Of the new features, resort_night_skiing_state_ratioseems the most correlated with ticket price. As well as Runs, total_chairs is quite well correlated with ticket price.

### Model Preprocessing with Feature Engineering

32 features was used in feature engineering. 
Scaling was applied to the data. 

### Algorithms Used to Build the Model with Evaluation Metric

The metrics to measure performance are: R-squared, MAE(Mean absolute error), MSE(Mean squared error)

A baseline of mean value was created, with a R-squared of 0.
By using a simple linear regression, we managed to achieve R-squared of over 70%, and mean absolute error 9, which means we are able to estimate the price within 9 dollars of the actual price, and mean_squared_error of 161. With grid search, we discovered the best amount of features to include is 8, and the most important one is vertical of the drop. Then we used cross-validation to estimate the model, the average performance of test split is consistent with the estimate with an average 63% in r squared, and 11 in MAE. Then a random forest model was fit, again cross-validation result yields 71% r squared and 9.5 in MAE. Overall, Random Forest seem to be the best model.
Features that came up important in the model:
vertical_drop
Snow Making_ac
total_chairs
fastQuads
Runs
LongestRun_mi
trams
SkiableTerrain_ac

### Winning Model and Scenario Modelling

Random forest model as the best model. 
Scenarios modelled:
Permanently shutting down up to 10 of the least used runs. This doesn't impact any other resort statistics. - price was expected to drop 1.71 by the 10th run
Increase the vertical drop by adding a run to a point 150 feet lower down but requiring the installation of an additional chair lift to bring skiers back up, without additional snow making coverage - This scenario increases support for ticket price by $1.99. Over the season, this could be expected to amount to $3474638
Same as number 2, but adding 2 acres of snow making cover - This scenario increases support for ticket price by $1.99. Over the season, this could be expected to amount to $3474638
Increase the longest run by 0.2 mile to boast 3.5 miles length, requiring an additional snow making coverage of 4 acres - This scenario causes no difference in the predicted price.

### Pricing Recommendation

Big Mountain Resort modelled price is $94.22 versus actual price is $81.00

### Conclusion

Additional data that might be required including customer demographics data to predict the actual flow of customers. The model can be implemented on a server and can be retrained and accessed by analysts to generate new predictions given updated data.

## Pipenv

The `Pipefile` has all the python dependencies and requirements you should need. So you can use [Pipenv](https://pipenv-fork.readthedocs.io/en/latest/) is you want to create a seperate python enviornment for this project. 

To install pipenv see [here](https://pipenv-fork.readthedocs.io/en/latest/#install-pipenv-today).

To create the env and install the required libraries (once you have pipenv installed) you can just do:
```
pipenv install
```

Then to activate the env and launch jupyter from this env you can do something like the below two commands:
```
pipenv shell
jupyter lab
```
