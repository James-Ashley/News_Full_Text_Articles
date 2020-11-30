# News_Full_Text_Articles

Version 1.0.0

## Description
This project scrapes newspaper articles on the topic of immigration and stores the articles and metadata about the articles in a MongoDB database.

## Background
As part of a previous project, we used the NewsAPI data to retrieve news articles on the topic of immigration from the past three months (9/2020 - 11/2020). This API call was run multiple times to retrieve as many articles as possible. We performed a sentiment analysis of the news headlines using NLTK’s Vader. The code for retrieving this data can be viewed here (ADD LINK HERE). 

## Data REtrieval and Cleaning

### NewsAPI Data
For the current ETL project, there were 6 csv files in a similar format which contained the following columns pertaining to each news article: keyword used to find the article, source, author, title, URL, article text preview, publication date, and sentiment analysis scores (compound, negative, positive and neutral). 

These csv files were combined, duplicate articles were removed, and the headline sentiment analysis was performed for articles missing these scores. In addition, articles that did not have an article text preview or that had duplicate text previews were removed since these articles were videos or links to other articles and were not relevant to our analysis of sentiment. Some of the news domains had very few sources in the dataset, so any source domains with fewer than 50 articles were removed from the dataset. 

After cleaning, a final csv file with 2667 unique articles in 9 news source domains was saved.

### News Article Data
In the future, we are interested in analyzing the full text of the articles which was not available to us through the NewsAPI. We used Newspaper3K to webscrape the articles using the URLs in our NewsAPI dataset. 

After scraping the full text of each article, the URLs and full text were saved in a Pandas dataframe. Duplicate URL’s and null values for the text were removed. This dataframe was merged with the original dataset using an inner join. This was saved to a JSON file to allow for further cleaning.

This text included line breaks and the string “AD” which were removed using replace(), and a cleaned version of the JSON file was saved. 

This final dataset included 2663 unique articles. This JSON file was loaded into a shared MongoDB database which all members of our group have access to.

## Challenges


## Instructions


## Contributors
James Ashley, Rebekah Callari-Kaczmarczyk, Brandon Martin, Scot Wilson

## License and Copyright
&copy; James Ashley, Rebekah Callari-Kaczmarczyk, Brandon Martin, Scot Wilson