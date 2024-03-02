# Data aquisition and analysis using Youtube API.

## Summary:

In this fun project, we have created two datasets corresponding to the popular Bengali Food Channel - Bpng Eats. Being a hard core foodie, Bong Eat is one of my most favourite channels
when it comes to recipes from West Bengal, India. I have been a long time subscriber of this channel, and in these years, I have seen it transform and grow quite a lot!
So, I thought it would be a fun idea to explore the statistics of this channel. This project has been built in Python.

## Tools

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

## EDA Process:


