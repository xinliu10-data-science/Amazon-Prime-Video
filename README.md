# Predictive Analytics of Amazon Prime Movies

When a user opens the homepage for Amazon Prime Video, he/she will probably end up seeing a page that looks like this. But have you ever wondered, what are the most important characteristics of a movie that make people spend more time on it? Is it the genre? Is it the language of the movie? Or even the position of the movie on the webpage? 

<p align="center">
<img src="Amazon%20Prime%20Movie.png" width="600">
</p>

There is no easy answer for this question. In this project, I built a prediction model to predict whether a movie is going to perform well (measured by cumulative time viewed by audiences per day) on the Amazon Prime Video platform. The analysis is based on a dataset with 4000+ rows and 16 columns. 

The following are the descriptions of the columns:
Video_id	:	A unique id for a movie
Cvt_per_day	:	Cumulated view time per day, this is also the variable the model is used to predict
weighted_categorical_position	:	Average vertical positions on the home page that the movie was placed
weighted_horizontal_poition	:	Average horizontal positions on the home page that the movie was placed
genres	:	genres of the movie
release_year	:	the year the movie was released
imdb_votes	:	the number of votes on IMDB, typically higher the votes the better
budget	:	budget of the movie production, typically the higher the better
boxoffice	:	gross box office in US as updated on IMDB, typically the higher the better
imdb_rating	:	ratings on IMDB
duration_in_mins	:	How long is the content in minutes
mpaa	:	MPAA ratings
awards	:	TVPG ratings
Import_id	:	Content partners
Metacritic Score	:	Metacritic score on IMDB page. Typically, the higher the better
Star_cateogry	:	A score to measure how popular the actor/actress are associated with the movie

[Add a link to the notebook]


