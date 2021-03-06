## This is my Udacity program project

will be finished in July 2020

# Wrangle-and-Analyze-Data

Introduction

The dataset that I wrangled (and analyzed and visualized) is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators are almost always greater than 10. 11/10, 12/10, 13/10, etc. 

In this project, you'll be using Tweepy to query Twitter's API for additional data beyond the data included in the WeRateDogs Twitter archive. This additional data will include retweet count and favorite count.

Some APIs are completely open, like MediaWiki (accessed via the wptools library) in Lesson 2. Others require authentication. The Twitter API is one that requires users to be authorized to use it. This means that before you can run your API querying code, you need to set up your own Twitter application. Here are the steps to do that on the Twitter site:


Quality issues
1.Missing data

There are 2356 rows in twitter_archive table. From code (twitter_archive.info()), we know many columns like "in_reply_to_status_id" and "in_reply_to_user_id" only has 78 non-null values.

2.Data validity issue

In twitter_archive table,the last few rows show some dog names are 'None', 'a', or 'an.' These are obviously wrong.

3.Data accuracy issue

In twitter_archive table, timestamp is an object and retweeted_status_timestamp is also an object (the other retweeted statuses are floats).

4.Data consistency issue

There are some strange outliers in columns. From code(twitter_archive.rating_denominator.value_counts()),there are 23 rating_denominators that are not equal to 10. Similarly, there are rating_numerators that are even bigger than 100.

5.Erroneous data

pupper, puppo, floofer and doggo column: There are some IDs with more than one dog "stage" information (two dogs are rated).

6.Duplicated values

From code (sum(image_prediction.jpg_url.duplicated())),we know there are some duplicated values in this column.

7.Data types are not consistent

In tweet_json table, tweet_id is object type. this is not consistent with data type in other 2 tables(int64 data type).This is not suitable for further data analysis.

8.Table size do not match

There are 2356 rows in twitter_archive, while 2075 rows in images_prediction.The size of the table do not match.


Tidiness Issues
1 Columns issue.

Each variable forms a column. In twitter_archive table,the last four columns all relate to the stage of dogs (dogoo, floofer, pupper, puppo).

2 Untidy data. In twitter_archive table, column source data have "<a" tag in HTML format surrounding the text.These are not common internet address for ordinary users.

3 Uppercase and lowercase mixture

In images prediction table, there is no consistency in p1, p2 and p3 columns. Sometimes the dog breed predictios are lowercase, sometimes they are uppercase.

4 Image_prediction table.

Tidiness require each type of observational unit forms a table.Tweet_archive and tweet_json can be merged into one table because they have same tweet_id column.
