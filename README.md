
# Wrangle Twitter Data Report
## Introduction:
In this project data is gathered from three different sources: twitter data archive, udacity server, and twitter API. This gathered data is then merged together and accessed for cleaning. Necessary cleaning operations are performed. Finally exploratory data visualizations are produced to explore the cleaned data.

## Data Gathering:
1. Data from twitter archive was downloaded and Imported the twitter-archive-enhanced.csv datafile as twitter_data dataframe

2. Data from image_prediction.tsv file from udacity server was imported using requests library and given url and was saved as server_data dataframe

3. Data from twitter api was gathered by the access and consumer tokens and by using tweepy library.
## Data Access and Cleaning:

### Quality issues:
1. The data from twitter archive i.e. twitter_data dataframe's 'text' column has three variables: tweet text, rating, and image url. These three variables were separated using 're' python library and saved as individual columns: text, text_rating, image_url

2. The twitter_data dataframe's 'timestamp' column has two varibles:Date and time. These two variables were separated using python datetime library and saved as individual columns- Date, Time
 
3. In image_predictions.tsv file there were three columns p1, p2, p3 that represent the same meaning dog breed and was reduced to one by comparing the corresponding p_conf value and p_dog if True
 
4. The datatype of rating_numerator and rating_denominator was int64, it was changed to float

5. The datatype of tweet_id was int64 in all datafiles, it was changed to object

6. Data was filtered and only those tweets were selected that has images. That is selected all the data for tweets who have media=photo

7. At some places the rating_denominator was not equal to 10, these ratings were compared with text extracted denominator ratings and were update if not same

8. At some tweets twitter text ratings and given ratings in twitter-archive did not match. So, rating_numerator was updated to the ratings of twitter text

9. The name column had unwanted dog names: a, such, the, very. This inaccurate information was replaced by nan values

10. As the combined data had many columns, only columns of interest were selected and unwanted variables were removed. This information was stored in a new dataframe

### Tidyness issues:

1. Data was collected from three different sources and so was to be merged together. Data from twitter archive datafile and data collected from twitter api was merged together

2. Data from combined_data dataframe (twitter_data_copy and api_data_copy) was merged with data gathered from udacity server (server_data_copy dataframe)

3. The columns: doggo, floofer, pupper, puppo columns in twitter_archive_enhanced.csv were combined into a single column named 'stage', as this is one variable that identify stage of dog


## Data Visualization and Findings:
1.) A box plot was created to observe the minimum, maximum and mean ratings for all dog ratings. And it was observed that min rating was 0, and mean rating was 12

![Plot1](Image\plot1.png)


2.) After grouping the data by type of dog breed and counting the number of dog, a bar plot was created to visualize the dog breed and its corresponding count of dogs. And it was observed that golden_retrriever has highest count of dogs

![Plot2](Image\plot2.png)


3.) After grouping the data by type of dog breed and summing the dog ratings, a bar plot was created to visualize the dog breed and its corresponding sum of ratings. And it was observed that golden_retrriever has highest summed ratings of dog

![Plot3](Image\plot3.png)

4.) A scatter plot was created to visualize the relationship between Dog rating and Count varibles. And was observed that there is a strong positive relationship, as the count increases so does the summed dog ratings.

![Plot4](Image\plot4.png)

5.) As there is positive relationship between count and summed rating, mean rating were considered. So, data was grouped by dog type and mean of its corresponding ratings were plotted. And it was observed that though golden_retriever had highest count and summed rating, hightest mean rating was given to Pekinese

![Plot5](Image\plot5.png)

6.) Data was grouped by date of tweets and its tweet_id count was plotted as a line plot, and it was observed that highest tweets were reported during 2015-12 to 2016-02

![Plot6](Image\plot6.png)

7.) Data was grouped by dog name and its tweet_id count was plotted as a bar plot and it was observed that most comman name given to dogs is Charlie

![Plot7](Image\plot7.png)

8.) Data was grouped by dog stage and its tweet count was plotted  as pie chart and it was observed that majority of dogs are pupper

![Plot8](Image\plot8.png)

