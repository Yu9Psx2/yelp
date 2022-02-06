# yelp
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