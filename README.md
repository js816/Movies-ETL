# Movies ETL

# Overview of the project 

## Purpose

The purpose of this project was to gather a variety of data on a large number of movies to be utilized by the Amazing Prime Video hackathon participants.  The participants will use the rich movie dataset to help predict which movies will be popular.  Amazing Prime Video has challenged the participants to help them predict which videos they should feature on their streaming platform.  Amazing Prime Video wants to make strategic selections of movies that would be popular on the site and fit well within their budget.


# Datasets

In an effort to gather accurate and complete data, a variety of datasets were used.

## Wikipedia Scrape

A JSON file with data on more than 7,000 movies released since 1990 was utilized.  This file scraped Wikipedia.org gathering up metadata such as that shown on the image below.

![Wikipedia_scrape](https://user-images.githubusercontent.com/82730954/122661432-be48dd80-d14f-11eb-9022-f412ee0a8740.PNG)

Because of its nature, the data from Wikipedia was often in varying formats, structures, and nomenclatures.  A good deal of cleaning was conducted in an attempt to standardize the data and help ensure accuracy.  

## Kaggle movie metadata

A second dataset from Kaggle was downloaded.  One file within the dataset featured metadata on more than 45,000 titles.  Features of this file include budget, genres, original language, release date, revenue, and run time among other columns.

## Ratings from MovieLens site

A separate file within the Kaggle download includes more than 26,000,000 movie ratings.  These ratings, from more than a quarter of a million users, allow users to rank each movie from 0.5 to 5 in half-point increments.

# Joining and cleaning the data

The two tables containing metadata were joined together.  Films were combined based upon their unique IMDB identifier.  The join was an inner join where data was retained when films existed in both tables.  If a film only existed in one of the two tables, the data was not carried into the merged table.

In general, the Kaggle data was more consistent and thorough and so it was preferred over the Wikipedia data.  However, the Kaggle data tended to have more missing values and in these cases the Wikipedia data was added before the Wikipedia columns were dropped.

There were also a number of columns that had a large number of null values or columns that didn’t provide much value.  These columns were dropped.  

Numerical data for several columns were cleaned to provide apples to apples comparisons.  The box office and budget data were cleaned from a small number of varying formats to consistently show the data in a consistent float format (such as 200000000.0 for $200 million).

The release date format was cleaned to consistently show a YYYY-MM-DD format.

The running time data format was cleaned to consistently show the number of minutes as a float (such as 143.0 for 2 hours and 23 minutes).

The 26 million ratings were consolidated and pivoted for each film showing the count of each rating level by film.  The image below shows an example of the consolidated ratings counts.

![Rating_counts](https://user-images.githubusercontent.com/82730954/122661435-cef95380-d14f-11eb-8a47-532b7bf94fad.PNG)

# Summary

The cleaned dataset will give the hackathon participants a great deal of metadata and ratings to help predict which films could be a good match for what Amazing Prime Video balancing popularity and budget.  It will be fascinating to see how the various groups of participants use the data and the variety of responses that are developed.  It was a pleasure working on this project and providing a clean dataset for the participants.
