# Technical Report - California Hiking Trails Recommendation System

This is a detail technical report summary of the steps to gather the data for the hiking trails, and the step to create a user to user explicit colaborative based filtering recommendation system. My goal for this project is to learn about recommendation systems since we didn't really have a project on this in the Data Science Immersive program. I want to be able to showcase I have an understanding of how to webscrap a javascripted website and gather data I collected and calculate cosine similarity to find similairities between users to recommend hiking trails.  

## Problem Statement

So you live in California and you want to go on a nature hike but you don't really know where to go. Your options are to go on to yelp or alltrails website to look at a bunch of reviews and decide on a hike or just ask your friends. Instead of reading a bunch of reviews, you can instead use my recommendation system! What my recommendation system does is it gathers and looks at a large number of reviewers of California trails on alltrails.com, analyzes their ratings, and based on one certain reviewer you pick from the website, returns a list of trails it predicts and suggest this user will want to hike next based on similar users with similar ratings. 


## Data Collection

I collected data from https://www.alltrails.com/us/california. I used the selenium libraries and the chrome webdriver to automate the javascript load more button to load more trails and the hiking trail reviewers and their ratings. I used the inspect feature on chrome to find the button for it to press. The data was backed up using Github as suggested by my instructor. The data collection took about 2 weeks to do on two different computers. I used a macbook pro 2009 with upgraded RAM of 8GBS with a SSD hard drive. This computer died about 1 week into the data collected due to running the web collection day and night. With 2 weeks left in the course, my only other option was to buy a new laptop to complete the course. The second computer I used is a 2018 macbook pro with 8GBs and quad-core. I pulled the back up files from github and re-download everything and install everything from day 0 of the course. The data was successfully extracted and stored as a csv. I didn't save the soup which contains the html because those files are too big. I divided the trails in sections for scrapping. For the most popular trails I tried to scrap 5-10 trails and saved the data since it took hours. For the the less popular trails I tried to scrap 500-1000 at a time. 

### Strategy

1. Collect all the trails, the trails features, and reviewers and reviewer's ratings.
2. Clean up the data, remove duplicated trails, remove reviewers with less than a certain number of reviews, and remove any null values.
3. Create a dataframe of rows of users and columns of trails with the rating values. Fill in zeroes for no ratings.
4. Reduce the size of the dataframe so that it is compatiable with the compute power on my computer.
5. Use cosine similarity to find the top users most similar to the main user.
6. Extract a list of trails from those users, sum up the ratings, remove the same trails as the main user that's compared to the other users, and the remaining trails are the suggested/recommended trails the main user should hike next based on user to user similarities in rating hiking trails.

## Exploratory Data Analysis

For this dataset, it started out with 7,728 hiking trails that were strictly in California only. I managed to scrapped 308,752 reviewers. However, after I removed duplicated reviewers, there were only 114,711 reviewers remaining which helped alot for computing the dataframe. 

The bulk of the hiking trails have less than 10 reviews.

![Num Reviews](https://git.generalassemb.ly/boxndragon04/California_Hiking_Recommendation_System/blob/master2/plots/num_reviews_less_than_32_greater_than_0.png)

The majority of the ratings are between 4 and 5 stars.

![Dist Rating](https://git.generalassemb.ly/boxndragon04/California_Hiking_Recommendation_System/blob/master2/plots/dist_rating.png)


## Results

1. Successfully extracted all the trails and reviewers and their ratings from all the California hiking trails on alltrails.com
2. Successfully generated the cosine similarity matrix for user to user similarity. 
3. Successfully able to create a function that extracts the trails from the similar users that are not in the main users review and suggest these new trails to the main user based on the sum of the ratings from the similar users.

## Future Steps

**Create a Sparse Matrix** - instead of removing the users and trails, I want to be able to save as much of the data as possible. As suggested by my instructor, I can 

**Setup a Flask** - Setup a flask app. This app would link up to postgres and generate hiking trail recommendations. 

**Setup Item to Item** - Allow an input box so you can enter in a location, difficulty of the hike, some keywords to what you are looking for in a hike, i.e. waterfall, view, trees, beach, etc... This would work with an NLP of the dscriptions and the location and type of trail.

**Setup a AWS** - I would want to setup a place to store the jupyter notebook so it can be ran anywhere.

**Validate the Recommendations** - I should do a train test split and see if the prediction are correct
