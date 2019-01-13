
# Wrangle Twitter Data Report
## Introduction:
In this project data is gathered from three different sources: twitter data archive, udacity server, and twitter API. This gathered data is then merged together and accessed for cleaning. Necessary cleaning operations are performed. Finally exploratory data visualizations are produced to explore the cleaned data.

## Data Gathering:
1. Data from twitter archive was downloaded and Imported the twitter-archive-enhanced.csv datafile as twitter_data dataframe

2. Data from image_prediction.tsv file from udacity server was imported using requests library and given url and was saved as server_data dataframe

3. Data from twitter api was gathered by the access and consumer tokens and by using tweepy library. Retweet status was stored in a data dictionary where key is the tweet id and value is 'True' if retweet, else 'False'. If tweet data not present 'no data'

## Data Access and Cleaning:
### Tidyness issues:
 1. The data from twitter archive i.e. twitter_data dataframe's 'text' column has three variables: tweet text, rating, and image url. These three variables were separated using 're' python library and saved as individual columns: text, text_rating, image_url.
 2. The twitter_data dataframe's 'timestamp' column has two varibles:Date and time. These two variables were separated using python datetime library and saved as individual columns- Date, Time.
 
### Quality issues:

1. The twitter archive data and data collected from twitter api were merged together as single dataframe. Merged twitter_data and api_data dataframes on tweet_id column using join function.

2. Merged combined_data dataframe (twitter achrive and api_data) with data gathered from udacity server (server_data dataframe). Now data collected from all three sources is in combined_data dataframe.

3. The required columns from combined_data dataframe were selected and saved in data dataframe,that would be used for analysis.

4. Data from data dataframe was filtered and only those tweets were selected that has images. That is selected all the data for tweets who have image_url

5. Data from data dataframe was filtered and selected data whose tweets are original. That is, deleted tweets that are re-tweets or whose data is not present

6. Numerator and denominator rating were checked for accuracy. If denominator rating was not equal to 10, it was updated to 10.

7. Further, numerator rating and rating from twitter text were compared. If numerator rating was not equal to text rating, it was updated.

8.  Missing values were deleted from data dataframe

9. From p1, p2, p3 one single column  was created whose corresponding p_conf was highest and p_dog was True

10. Removed unwanted columns

## Data Visualization and Findings:
1. A box plot was created to observe the minimum, maximum and mean ratings for all dog ratings. And it was observed that min rating was 0, max was 14 and mean was 12
2. After grouping the data by type of dog breed and counting the number of dog, a bar plot was created to visualize the dog breed and its corresponding count of dogs.
3. Also, first 10 dog breed with highest count were plotted. And it was observed that golden_retrriever has highest count of dogs
4. After grouping the data by type of dog breed and summing the dog ratings, a bar plot was created to visualize the dog breed and its corresponding sum of ratings.
5. Pie chart was created to visualize top 10 highest summed ratings of dogs. And was observed that golden_retriever has highest summed rating
6. A scatter plot was created to visualize the relationship between Dog rating and Count varibles. And was observed that there is a strong positive relationship, as the count increases so does the summed dog ratings.
7. As there is positive relationship between count and summed rating, I thought we should consider mean rating. So, data was grouped by dog type and mean of its corresponding ratings was stored and plotted.
8. A boxplot was created to visualize the minimum mean, maximum mean and average mean rating for dog type. And it was observed that min mean is 9, max mean is 14 and avg mean is 12.
9. Lastly a scatter plot was created to visualize the relationship between mean rating and dog type count, and it was observed that there is a weak positive relationship.
