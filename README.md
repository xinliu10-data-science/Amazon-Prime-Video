# Predictive Analytics of Amazon Prime Movies

Project Description
----------------------

When a user opens the homepage for Amazon Prime Video, he/she will probably end up seeing a page that looks like this. But have you ever wondered, what are the most important characteristics of a movie that make people spend more time on it? Is it the genre? Is it the language of the movie? Or even the position of the movie on the webpage? 

<p align="center">
<img src="Amazon%20Prime%20Movie.png" width="600">
</p>

There is no easy answer for this question. In this project, I built a prediction model to predict whether a movie is going to perform well (measured by cumulative time viewed by audiences per day) on the Amazon Prime Video platform. The analysis is based on a dataset with 4000+ rows and 16 columns. 

The following are the descriptions of the columns:<br/>
Video_id	:	A unique id for a movie<br/>
Cvt_per_day	:	Cumulated view time per day, this is also the variable the model is used to predict<br/>
weighted_categorical_position	:	Average vertical positions on the home page that the movie was placed<br/>
weighted_horizontal_poition	:	Average horizontal positions on the home page that the movie was placed<br/>
genres	:	genres of the movie<br/>
release_year	:	the year the movie was released<br/>
imdb_votes	:	the number of votes on IMDB, typically higher the votes the better<br/>
budget	:	budget of the movie production, typically the higher the better<br/>
boxoffice	:	gross box office in US as updated on IMDB, typically the higher the better<br/>
imdb_rating	:	ratings on IMDB<br/>
duration_in_mins	:	How long is the content in minutes<br/>
mpaa	:	MPAA ratings<br/>
awards	:	TVPG ratings<br/>
Import_id	:	Content partners<br/>
Metacritic Score	:	Metacritic score on IMDB page. Typically, the higher the better<br/>
Star_cateogry	:	A score to measure how popular the actor/actress are associated with the movie<br/>

[Add a link to the notebook]

Main Challenges and Investigations
----------------------------------
### Handling of Missing Data
One of the main challenges I had during this project is dealing with missing values. Among the 10 numerical features, I found that 4 features (budget, boxoffice, metacritic_score, star_category) have more than 25% missing data, and 2 features (imdb_votes, imdb_rating) have less than 10% of missing data. There are 3242 samples have at least one missing data.

There are two common types of missing data: _**informative**_ and _**non-informative**_. The first category is produced by random data loss; in this case, the observations with missing values are no different from the ones with complete data. As for _informative_ missing data, it telss you something about your observation. A simple example is a customer record with a missing subscription cancellation date meaning that this customer's subscription has not been cancelled so far. 

Ways of dealing with missing data are: <br/>
1) Elimination from analysis; 
2) Imputation (e.g. mean, median or mode, last observation carried forward, ); 
3) Model/reason-based imputation (e.g. k-NN) 

We usually don't want to fill in informative missing data with a mean or a median because the high majority of missing data in tech companies come from the fact that the user has chosen not to provide information: by not filling out profile, or by changing privacy settings, or deleting cookies. That is cruicial information for predictive model that we would lose, if we were to replace the missing values with predicted values. In this case, we may want to generate a seperate feature for them (Missing = Y/N), as an indicator of whether user chose to tell us the information. 

Though the above discussion, I assume the missing data in this project is non-informative and for all 6 features with missing data, their corresponding mean values were imputated to replace missing entries. 

### Feature Engineering 
Two categorical features caught my attention: _**genres**_ and _**release_year**_. 

_**Genres**_: In the original 'genres' column, some movies have more than one genre listed, separated by comma. First thing I did was splitting the genres and plotted the number of movies belong to each individual genre. This helped me understand the impact of each individual genre. 
 
[Insert a plot]

The 'genres' have 27 different sub-types, 6 of them are rarely observed (Anime, Reality, Lifestyle, Adult, LGBT, Holiday). Therefore, during feature processing, these 6 genres were grouped together as one single sub-type - 'Other'. All the genre sub-types were encoded into dummy variables. We ended up having 22 dummy variables for movie genres. 

_**Release year**_: The release year of movie varies through a wide range (1916-2017). Considering the popularity of a video usually decays over time, the release_year were bucketed based on the release_year percentiles. 

After the feature engineering step, the feature space holded 4226 observations and 58 features in total, and with no null data. The dataset was scaled using standard scaler before training. 

### Model Training and Evaluation 
The metric to predict (cumulative time viewed by audiences per day) is continuous, so regularized linear models (LASSO linear regression, Ridge linear regression) and non-linear model (random forest regression) were implemented and evalualted. 5 models were compared using coefficient R^2, mean squared error (MSE) and root mean squared error (RMSE). 

A majority of the effort was to inrease the model performance. The baseline model (LASSO linear regression) only generated R^2 score of 0.36457853303. 

Random forest tree regressor generates the best prediction accurarcy (R^2 score of 0.50839320352), with best parameters n_estimators=14 and max_depth=55. 

### Business Insights and Discussion








