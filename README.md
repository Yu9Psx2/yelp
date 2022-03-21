# yelp re-scorer
I like eating at one-off type non-chain restaurants.
I do a lot of travelling, and it's easy to find established local favourites on yelp.
However, I don't drive, so when I go to one of these places I have to make a day of it.
There are times when I need to find a place to eat that's nearby - 2 km is my normal walking radius.

The restaurants within a 2km radius might not have many reviews, making the dining decisions harder.

This workbook is geared towards helping me re-score the reviews in my own way.

There are several problems that I am trying to solve for:

1) With so few reviews, restaurants do not stand out.
2) There are so few reviews that a negative review doesn't mean anything - it might have come from a competitor or 'negative nancy'
3) A restaurant can serve great food and bad food at the same time - for example, a place that has great milkshakes but mediocre burgers.

Yelp has a large open-data sample dataset that I think can help solve for these problems.

At the outset, in respect of each of the three points listed above, I am going to rescore the ratings as follows:
1) Put additional weight towards reviews by those with a bigger review history.
2) Use the open data set to find reviews by 'negative nancys' and try to use NLP to train on these negative reviews and use the results to disregard 'negative nancy' reviews in live data.
3) Figure out a way to solve for 3) above.
## Completed to date
### Loaded data
Yelp has a [large dataset](https://www.yelp.com/dataset) of businesses and reviews.  
So many rows that I was running out of memory  
It was a bit of work to learn how to use the chunksize feature to format the data bit-by-bit so that the data I needed would be in a single dataframe that I could load

### Cleaned data
The data included reviews for businesses that were not restaurants, I had to reference against the business_df dataframe in order to find those reviews for restaurants.
I also wanted to limit the reviews to those restaurants that had more than 5 reviews.

### Labelled data
By merging the review and the business_df together, I was able to label the data using my custom score: If a review was three or more stars below the restaurant's average star rating, I labelled it a 1.
My theory is that if I train a ml-model on this data, then I might be able to identify 'negative nancy' type reviews for restaurants with very few reviews. E.g. if a restaurant has less than 10 reviews, and one of these is a 1 score, that would have too great an impact on the average

## Key takeaways
Formatting data in chunks and using pandas lambda functions
