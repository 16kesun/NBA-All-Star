# NBA-All-Star
Uses several methods to predict whether a player is an all-star or not

## Webscraping
I used beautiful soup to scrape two seasons (2018-2019 and 2017-2018) of stats from Pro Basketball Reference. These stats are all season averages and include points, rebounds, assists, three point percentage, steals, blocks, minutes etc. and placed this data into two separate dataframes. I then added a new column "star" which indicates whether the player was an all star that year or not (0 if not, yes if is). Finally I combined the two dataframes into one.

After this I began cleaning my data. First I made the necessary columns numeric (all other than Name and Team). Next I filled in missing values with zeros.

## Exploratory Data Analysis
First I made a scatterplot with points and minutes to test my assumption that all-stars will average a high number of points and minutes. This assumption was proven true, based on the cluster of all-stars found at the top right of the plot.

I then looked at histograms for each of my features to check if they are normally distributed. Some of these features were skewed so I applied a log transformation on those features so they could be included in my logistic regression.

I also used boxplots to compare regular players with all-stars, as expected all-stars outperformed the general population in all features.

Lastly I created a heatmap to check for multicollinearity between features.

## Logistic Regression
Using the scikit-learn package I performed a logistic regression with "star" as the dependent variable and my transformed features as independent variables. I seperated my data into a training set (70%) and a test set (30%). In order to deal with the small number of all-stars, I applied SMOTE to my training set, artificially boosting the number of all-stars in the training set so that the model has more of opportunities to learn what the characteristics of an all-star are. When comparing the SMOTE model with a regular one, SMOTE is slightly less accurate but yields less false negatives, making it the more effective model. Logistic regression yielded an accuracy score of 93%.

## Decision Tree
My next model was a decision tree, also built with scikit-learn. I built an Area Under Curve chart to determine the optimal number of levels that my tree should have and landed at 6. I used the same features that went into the logistic regression and achieved an accuracy score of 96% and yielded less false positives.

## SVM
My final model was support vector machines, also builty with scikit-learn. This model was able to achieve a slightly better accuracy score than logistic regression, 94%. It is also superior to the decision tree model in that it had zero false positive predictions.

## Conclusion
When it comes to interpretability, logistic regression is the most useful, as you can look at each of the feature coefficients to determine the effect that each feature has on the model's prediction. However looking purely at the accuracy of the predictions, the decision tree model performed the best, boasting the highest accuracy score of the three models.


