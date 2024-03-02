# Data aquisition and analysis using Youtube API.

## Summary:

In this fun project, we have created two datasets corresponding to the popular Bengali Food Channel - Bpng Eats. Being a hard core foodie, Bong Eat is one of my most favourite channels
when it comes to recipes from West Bengal, India. I have been a long time subscriber of this channel, and in these years, I have seen it transform and grow quite a lot!
So, I thought it would be a fun idea to explore the statistics of this channel. This project has been built in Python.

## Tools:

Programming Language:  Python  
IDE : jupyterlabs

## ETL Process:

## Extract:

The data acquisition process was a bit tricky and had a learning curve. I made a lot of use of the Youtube API documentation for reference code, and to identify which components to retrieve in order to 
get the statistics that I was looking for. I will try to outline the steps below:

1. We need to create our Youtube developer key. The link below from Youtube API documentation outlines the steps needed for this. Once the API key is generated, please save it in a secure location.Activate the 
   API service by clicking Enable button. 
   https://developers.google.com/youtube/v3/getting-started

2. We install and import the packages that we need to call the API and get back the results from the API call. In additon we also import packages such as Pandas, matplotlib and seaborn for analyzing and 
   visualizing the data.

3. The next step is to identify the channel id for the channel. For this project, I had to go to the channel homepage, right clicked and selected 'View Page Source'. Once on the page, I ran a search with
   'channel', and I was able to retrive the 24-characted channel id.
   
4. The rest of the process performs the following in a step by step fashion
   a. Retrieves all the playlists under the channel. In this case there was only one
   b. Retrieves all videos in that playlist
   c. Retrieves the statistics and comments for each video and loads all this info in to Pandas dataframes, one for Video Stats, and the other for Comments
   Note that the data returned by the API call is in JSON format, so I had to work with Python dictionaries to be able to store them with the correct key and values, and process them to load in to
   dataframes.

## Transform:

The following steps were taken to clean and transform the data:

1. For the Videos dataset, I verified that there was no Null value.
2. I modified the data type of columns such as likeCount, commentCount, favoriteCount and viewCount to numeric.
3. Extracted the day of week from 'publishedAt' column.
4. Added durationSecs column to store the calculated value in seconds from the column duration , which is in ISO 8361 format. For this step, I used Regex for this transformation.
5. For the comments dataset, I identified the comments that were in English letters, and dropped the rest . For this, I used the method detect_langs from the package langdetect

## Load:

The videos and the comments dataframes were loaded to two csv files.

## EDA Process and Findings:

I wanted to understand some statistics of this channel, the findings for which I wil share below"

1. Best and Worst Performing videos- The following graphs show the most and the least popular videos. The metric used here is **'viewCount'**
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/e179c041-c08e-4fb0-93bc-46a445d16691)

   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/d8d28edf-3eb5-4ba9-bd00-dc118ae92752)

2. View Distribution- What's the average number of views that the channel gets? Are there any outliers with exceptionally high or low view counts? The following snapshot shows that. We
   plotted a histogram to understand the view distribution, and we find that majority of videos have around 100 K views, with one video having 6 million views! Not surprising, considering the video
   is for the recipe of 'Kosha Mangsho', one of the most popular Bengali delicacies. I have probably watched this video 20 times myself.
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/43aeaa52-d81c-4a62-8a95-7b1f84d73348)

3. Comment Distribution : Similar analysis to find the distribution of comment count across the videos. Majority seem to have under 200 comments, with a few videos having more than 2000 comments,
   which is certainly unusual, but expected, given the content.
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/fea33cba-289d-4c4f-b314-3372ac00cc6b)

5. Publishing schedule: Majority of videos are published on Fridays, around 230 out of 292. Some very early videos and a shorts have been published on Wednesday, about 5, making it the least common
   day for publishing videos. A Friday video is a good strategy to hook viewers in time for a weekend cooking session.
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/945c8e37-7823-4610-8e84-92d5d109f3eb)

7. Average Video Duration: Majority of videos span about 600 secs, about 10 mins, with a about 2-3 videos with a duration longer than 30 mins.<find vid name for longest vid>
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/54465569-7726-4ca5-8973-c315512f9070)

8. Relation between views, and like count, comment count and duration: There is quite clear positive correlation between view count , like count and comment count. Howver, no such correlation is
   found with duration. < add heat map> and corr coeff
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/a0673724-7d50-4889-ac20-ead15bb17b8e)

10. And Finally, what are some of the most common words used in the channel , that makes it uniquely foodie and Bengali?
   ![image](https://github.com/Debduti/Youtube-API-Data-Acquisition-and-Analysis/assets/58540839/5004bfc2-5d09-4db5-b667-64d16c7c03f4)







