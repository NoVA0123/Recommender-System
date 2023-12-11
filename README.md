# Recommender-System

Recommender system for games made in python.

# Project-Overview

This project is about recommending games through conten-based recommendation process. This project used an already cleaned dataset of steam. It has an over 20,000 games for recommendation.

# Tools

1. Kaggle was used to run this program as it provides free powerful cloud computer.
2. Sci-kit learn library
3. Pandas and Numpy library

# Resources 

1. [Dataset](https://www.kaggle.com/datasets/nikdavis/steam-store-games)
2. [Notebook](https://www.kaggle.com/code/abhijitrai/recomender-system)


# Data Preparation

As the data was already cleaned, I didn't need to clean the data. But there are multiple datasets were given and out of them, I chose two datasets:

1. steam.csv
2. steam_data_desciption.csv

Now, I need to combine the datasets, but before doing so, I need to remove some columns:

1. Columns such as positve_ratings, negative_ratings, average_playtime, meadian_playtime and owners come under collaborative based filitering.
2. We don't nedd achievement and required age because they are not a good basis for recommending someone a game.
3. From steam_data_descripiton.csv, we don't need short description as it shortens up the large description.

Now we have to join them on the basis steam_appid column abd we need to drop the NaN values. (Incase if any)

After joining the the two datasets we need to prepare datasets for TfidfVectorizer. To do so, I performed following steps:

1. converting all columns to string
2. splitting words and using split() function (which will convert the sentence into list of words).
3. creating a new column which contains all columns and using lower case function to convert words into lowecase letters

Note: this process was performed using pandas


# Making a model that will perform recommedation

1. Using [TfidfVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html) to convert words into vectors.
2. Using [cosine_similarity](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html) to find cosine distance of the vectors.


# Recommender function

To create a recommender function we need to perform following steps:

1. The function has a parameter of game_name that will take the name of the game to recommeend.
2. We will find the index of the game
3. Then will use our model to find similar using index. To do so, we need to sort the top 10 closest value.
4. Then printing the game in a sorted order.


