# NBA Outcome Predictor

*Kaushika Uppu, Yun Ei Hlaing, Iris Cheung, Miranda Billawala*

The National Basketball Association (NBA) is one of the most well-known sports leagues, with a widespread global fanbase. With the rise of machine learning and statistical modeling, data-driven sports analytics has become more and more common, and the vast availability of past NBA game data as well as the league’s popularity makes game forecasting a profitable and appealing task. The main objective of this project was to be able to predict the winner of an NBA game matchup given two teams and by using past game data. With that objective in mind, we had a two-step process to achieve this. Our goal was to use two machine learning models to first develop a preliminary model that can predict game statistics using historical NBA game data, and to then use those as inputs into our final model to determine the most likely game winner. The second objective was our use case, which was to use these models to predict the 2024-25 NBA playoffs winner. For game outcome prediction, we found that the XGBoost model with hyperparameter tuning had the best performance, with an accuracy of 0.685, precision of 0.683, and recall of 0.69.

### Project File Descriptions:

***Import-Update_Data.ipynb —***
This file is used to get the NBA game logs. Once we get the data, we clean it as necessary (fixing dates, changing columns to usable formats, and dropping unnecessary columns) then we export to csv for use in the other notebooks. Use this file when new games have happened and the current logs need to be updated.

***EDA.ipynb —***
This file has comprehensive exploratory data analysis to better understand the data and direct our next steps for our approach when building the model.

***NBA_Game_Statistics_Predictor.ipynb —***
Our project build a game predictor with a two-step approach. First, we predict statistics indicated team performance (like Field-Goal Percentage) for the game we want to predict the outcome of. Then, we use these values to predict our outcome. This notebook handles predicting game statistics. We try two different ways: a basic rolling window and an XGBoost model which predicts the statistics when given the rolling averages. We perform hyperparameter tuning on the XGBoost Regression model, then compare performance between the two methods. This notebook is not necessary to run for training and testing of the model as we saved the csv files since predicting the statistics can take nearly 10 hours. However, for Playoff Prediction, this notebook needs to be run in tandem with NBA_Game_Outcome_Predictor since we are constantly going between predicting statistics and outcome.

***NBA_Game_Outcome_Predictor.ipynb —***
This notebook handles the outcome prediction. We validate the model, perform feature selection and hyperparameter tuning, and finally test using the predicted statistics from before. Once this is complete, we perform playoff prediction at the end.

***all_stats_cleaned.csv —***
Includes all the game log information, which contains team information (name, id, abbreviation), opponent, win/loss, game information (min, points, shooting statistics). This file is used primarily for statistics prediction.

***df_model_tuned.csv —***
Has the predicted statistics from the XGBoost Regression Model for the seasons from 2014-2024. This can be used to avoid the lengthy prediction running and should be constantly updated with new games.
