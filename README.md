# SteamRecommenderSystem
This project built a recommender system for Steam based on customer segmentation analysis and topic modeling. The system is based on both customer's game-playing behavior and socialization properties.

## Methodology
The goal here is to retain customers by recommending proper games. To do recommendations, we need to firstly find out similar users which is defined further by using distances. And to calculate distances, we need to fist create a user profile. There are two main components of a user profile: what the user mainly talk about and the users’ game-playing behaviour profile.
 
We got the original data. Based on different data types, we have two processes. For textual data which is mainly our review text, we conducted texting mining and NLP. Next, we did topic modeling to create the first component of the user profile: what is the user talking about.

For numerical data like play time, last play date etc, with aggregation and some other data calculations, we successfully get the information on a user level regarding their game-playing behavior like how many games they played, how much they play etc.

With the two components of the user profile generated we are able to calculate distances and do recommendations.


## Data
The raw data was totally manual scraped from Steam platform and we organized them into three tables: *Reviews, Games, Users*.   
We scraped 91,925 game-related data and 1.8 million user-review data from Steam platform using API. After exploratory data analysis, we decided to narrow our analysis scope to 7,808 games based on the following conditions:   
1. Games that are not free.  
2. Games that were released between 2000 - 2020.  
3. Games that have enough reviews: without label like “without enough reviews to infer sentiment” or “no user reviews”.  
4. Games that are under the TOP 3 popular genres: Action-Adventure, Simulation and RPG (Role-Playing games).   
Finally, using these 7,808 games, we scraped totally 1,817,436 reviews which involved 1,091,552 distinct users.

## Customer Segmentation Analysis
We built a segmentation metrics by using variables regarding the number of games that the user purchased and the frequency of playing times, and divided all users into four segmentations: game lover, game devoter, game explorer and occasional gamer.   
We focused mainly on game devoters and game explorers and further dinstinguished *active* and *inactive* users.

## Modeling
Of the top 3 genres, by extracting bi-gram features from tokenized user reviews, we developed a LDA topics model to investigate further what are the underlying information of the reviews from these most hitted genres. This is the main component of our user profile.   
Based on the user’s profile we established, we calculated user similarity using both euclidean distance and cosine similarity.    


