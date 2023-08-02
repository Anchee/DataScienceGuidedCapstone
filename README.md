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

During the exploratory analysis, we identified significant variations between state and ticket prices. The dataset contains 28 numerical features, and 4 textual features. Notably, fastQuads, Runs, and Snow Making_ac showed strong correlations. The newly engineered feature resort_night_skiing_state_ratio also exhibited a notable correlation with ticket prices. Additionally, Runs and total_chairs were relatively well-correlated with ticket prices.
![image](https://github.com/Anchee/DataScienceGuidedCapstone/assets/32008044/20cd3b22-05bd-4663-acf5-4049eb46e385)


### Model Preprocessing with Feature Engineering

For model preparation, we utilized 32 features in the feature engineering process. The data was scaled to ensure numerical stability.

### Algorithms Used to Build the Model with Evaluation Metric

The model performance was evaluated using the following metrics: R-squared, Mean Absolute Error (MAE), and Mean Squared Error (MSE).

A baseline model using the mean value resulted in an R-squared of 0. By employing a simple linear regression, we achieved an R-squared of over 70% and a mean absolute error of 9, indicating that price estimates were within $9 of the actual price. The mean squared error was 161.

Through grid search, we determined that the optimal number of features to include in the model is 8, with "vertical_drop" being the most important. Cross-validation revealed that the model had an average R-squared of 63% and an average MAE of 11. Subsequently, a random forest model was trained and evaluated using cross-validation, resulting in an R-squared of 71% and an MAE of 9.5. Overall, the random forest model outperformed others.

Key features identified as important in the model include: vertical_drop, Snow Making_ac, total_chairs, fastQuads, Runs, LongestRun_mi, trams, and SkiableTerrain_ac.

### Winning Model and Scenario Modelling

The winning model was identified as the random forest model based on its superior performance.

Various scenarios were modeled to analyze their impact on ticket prices:

Permanently shutting down up to 10 of the least used runs: Predicted price decrease of $1.71 by the 10th run.
Increasing the vertical drop by adding a run 150 feet lower down, requiring an additional chair lift: Predicted price increase of $1.99, potentially amounting to $3,474,638 over the season.
Similar to scenario 2, but adding 2 acres of snow making coverage: Predicted price increase of $1.99, potentially amounting to $3,474,638 over the season.
Increasing the longest run by 0.2 miles, requiring an additional 4 acres of snow making coverage: No significant difference in the predicted price observed.

### Pricing Recommendation

Big Mountain Resort modelled price is $94.22 versus actual price is $81.00

### Conclusion

To enhance the model's predictive capabilities, additional data, such as customer demographics, might be required to predict the actual flow of customers. The model can be implemented on a server, retrained, and accessed by analysts to generate new predictions given updated data. Continued optimization and monitoring can provide valuable insights for resort management to make informed pricing decisions and maximize profitability.

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
