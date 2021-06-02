---
title: "Data Science Program Projects"
date: 2020-2021
tags: [data wrangling, data science, messy data]
header:
  image: "/images/perceptron/percept.jpg"
excerpt: "Data Wrangling, python"
mathjax: "true"
---

# Movie Recommender System

## Using Python, Statistics for Data Science and Domain Knowledge of Movies

### This project describes a movie recommender for a movie viewing platform. Companies such as Amazon and Netflix use recommender systems to personalize choices for the consumer. “Product recommendations are increasingly important for the retail industry in general” (Siegel, pg. 185). Product recommendations are so important to the user experience overall that Netflix has sponsored a $1 million competition to improve movie recommendations. The amount awarded can be justified as it has been reported that “70 percent of Netflix movie choices arise from its online recommendations” (Siegel).  

**Business Understanding: Defining the Problem** 
	A recurring problem in the digital streaming experience is indecision and the paradox of choice that can overwhelm the media consumer. Many Netflix consumers often spend too much time browsing movies but a “good” recommender can help make the user experience more enjoyable overall.   
This analysis aims to recommend movie titles to a user based on their provided ratings of movies and movies that are similar. This project will use the method of Item-based Collaborative Filtering which focuses on the attributes of the items and give a recommendation based on the similarity between the movies. 

**Data Understanding**
	The “movielens” dataset used in this recommendation project can be found on the GroupLens website at (source: https://grouplens.org/datasets/movielens/latest/). The dataset used in this analysis contains 100,000 ratings and 3,600 tag applications applied to 9,000 movies by 600 users. This dataset was last updated on September of 2018. The dataset feature columns are movie ID, user ID, rating and movie title. All attributes in the dataset are numerical with the exception of the movie title which is a string data type. 
1.	Movie ratings:  1 to 5 (ordinal) 
2.	Movie ID: mapped to a movie title (nominal)
3.	User ID: (nominal)
4.	Movie title: (String data type) 

**Data Preparation**
There are two csv flat files. The ratings csv file contains a movie ID, user ID, and rating. The movie csv file contains movie ID and movie title. The two csv files were merged into a pandas data frame for analysis. The data types had to be converted from object type to numeric in order to implement a panadas pivot table. The pivot table was used to construct a user/movie rating matrix as shown in Table 1 where NaN indicates missing data which are movies that specific users didn’t rate. 

Table 1: User/Movie Rating Matrix
 

**Modeling**
Movie Similarity
A correlation score was calculated to determine the quantified similarity between movies. Panda’s correlation function, was used to compute the pairwise correlation of a sample movie such as “Fight Club (1999)” vector of user rating with every other movie. After the computation, any results with no data were dropped. Then, a new data frame of movies and their correlation score which is the quantified similarity to “Fight Club (1999)” is constructed. The list of similar movies to  “Fight Club (1999)” were sorted for highest correlation score at the top. As someone who enjoys movies, I can say that in this first trial recommendation list, a lot of the movies listed were obscure. 
In order to avoid spurious data, I checked for the size or number of ratings for each movie. Spurious relationships can provide inaccurate results because it is “a relationship between two variables that is caused by a statistical artifact or a factor, not included in the model, that is related to both variables” (Downey, pg. 143). I dropped movies that did not have very many ratings. I used a threshold of 200 ratings in order to drop any movies rated by fewer than 200 people and then check for the top-rated ones that are left as shown in Table 2.

Table 2: Movies that provide a higher number of rating data
 

I then joined the movies with a higher amount of rating data to the similarity correlation score in table 3 below: 
Table 3: Movies similar to Fight Club
 

Item-based Collaborative filtering:
Item-Based is focused on the attributes of the items and give a recommendation based on the similarity between them. I created a simulated user who provided a few ratings and based on those ratings the recommender system can recommend a list of similar movies. 

**Model Interpretation**
Based on the results in Table 3 and my own knowledge of the film I can see that the recommender system does a pretty good job of identifying similar movies to “Fight Club” such as “Seven” and “Pulp Fiction” which is dark, gritty, and violent. If the user provide ratings that are accurate to their taste, I can retrieve the list of similar movies from the correlation score matrix and then scale those correlation scores by how well the user rated the movie they are similar to. Movies similar to the ones the user like count more than movies similar to the ones the user hated.  




References:
Abbott, D. (2014). Applied predictive analytics: Principles and techniques for the professional data analyst. Indianapolis, IN: Wiley.
Downey, A. (2015). Think Stats: Exploratory Data Analysis. O’Reilly Media, Inc.
Siegel, E. (2016). Predictive Analytics: The Power to Predict Who Will Click, Buy, Lie, or Die. Indianapolis, IN: Wiley.

[link](https://grouplens.org/datasets/movielens/latest/)











What about a [link](https://github.com/dataoptimal)?

Here's a bulleted list:
* First item
+ Second item
- Third item

Here's a numbered list:
1. First
2. Second
3. Third

Python code block:
```python
    import numpy as np

    def test_function(x, y):
      z = np.sum(x,y)
      return z
```

R code block:
```r
library(tidyverse)
df <- read_csv("some_file.csv")
head(df)
```

Here's some inline code `x+y`.

Here's an image:
<img src="{{ site.url }}{{ site.baseurl }}/images/perceptron/linsep.jpg" alt="linearly separable data">

Here's another image using Kramdown:
![alt]({{ site.url }}{{ site.baseurl }}/images/perceptron/linsep.jpg)

Here's some math:

$$z=x+y$$

You can also put it inline $$z=x+y$$
