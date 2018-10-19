# California Hiking Trail Recommendation System 

## Directory Structure

```
.
├── Technical_Report.md
├── README.md
├── data
├── notebooks
├── plots
├── chromedriver

```

## Goals

1) Scrap 7000+ California Trails from All.trails.com and the 300,000+ reviewers and their ratings
2) Put the data into a table for evaluation
3) Use cosine similarity to find the top similar users to a given user
4) Generate a recommended list of hikings trails from the users

## Technical Report

This will be the detail report of how I collected the data, what libraries were used, and what calculations were performed on the data to generate the top similar users and predict a recommended list of trails for hiking. It will also include some exploratory data analysis of charts and graphs of the types of trails, location of the trails, the reviewers per trails and ratings per trail, and so on. 

## Data Directory

1) california_hikes_df.csv file that contains rows of all the trails with 

| Columns | Description |
| ------ | ------ |
| trails_web_extension | url extension for each trail |
| name | name of the trail |
| description1 | 1st description of the trail |
| description2 | 2nd description of the trail |
| distance | distances of the trail in miles |
| elevation | elevation of the trail in feet |
| route | the type of route: out and back, loop, point to point |
| location | location, usually a national park or city |
| numreviews | number of reviewers |
| reviewers_rating | average reviewers rating |

2) all_user_df.csv is an extremely large csv. The size is 1.81 GBs. The shape of the file is (117292, 7727). 117292 is the number of reviewers and 7727 is the number of trails. This is not shown on github because the file is too big to be stored on github.

3) trails_id_df.csv is a dataframe that has 2 columns. the first column is the name of the trail and the second column is the trail_id to match up with the trail_id in the all_user_df.csv

4) trails_df.csv is a dataframe of the url extension link to each hiking trail on alltrails.com

5) clean_df.csv is a clean version of the california_hikes_df.csv file with the nulls removed and the numerical columns for the numerical values

## Notebook Directory

| Notebook | Description |
| ------ | ------ |
| 01_Selenium_Get_All_CA_Hiking_Trails.ipynb | Code for gathering each trail's url extension with Selenium from alltrails.com |
| 02_Scrapping_Reviews.ipynb | Follows 01_Selenium_Get_All_CA_Hiking_Trails.ipynb and uses the url to collect the description of the trail and the reviewers and ratings of that trail |
| 03_EDA_California_Hiking_Trails.ipynb | Follows 02_Scrapping_Reviews.ipynb. It will have the EDA on the trails |
| 04_recommendation_system_user_to_user.ipynb | Follows 03_EDA_California_Hiking_Trails.ipynb. Calculation using cosine similarities |

## Notebook Directory

Plots

## Chromedriver

This is a open source webdriver for automating the load more button to load more hiking trails when running the selenium code for web scrapping


