# Airbnb analysis: Project Overview

* Analyzed neighborhood trends in Seattle, focusing on availability, prices, and visitor behaviors.
* Preprocessed the data by converting date formats, handling missing values, and encoding availability.
* Analyzed the impact of new visitors on availability and identified key months for visitor influx.
* Created a neighborhood sentiment analysis based on visitor reviews using text processing and vectorization.
* Extracted the most frequent keywords associated with each neighborhood's reviews.
  
## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, matplotlib, seaborn  
**Kaggle Dataset:** https://www.kaggle.com/datasets/swsw1717/seatle-airbnb-open-data-sql-project/data?select=calendar.csv

## Data Cleaning 
After getting the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

- Converted date columns and extracted year, month, and day features.
- Encoded availability (`t/f` → 1/0) for easier analysis.
- Cleaned price data by removing symbols and converting to numeric format.
- Identified and analyzed new visitors by using listing duplication to track unique bookings.

## Sentiment Analysis
- Merged review comments with listing data to perform sentiment analysis for the top 20 neighborhoods.
- Applied text cleaning techniques (lowercasing, removing punctuation and stopwords) to extract relevant keywords.
- Created a model using `CountVectorizer` to identify the top 5 keywords for each neighborhood.
  
## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/Samir4569/Airbnb_analysis/blob/main/Screenshot%202024-08-15%20173339.png)
![alt text](https://github.com/Samir4569/Airbnb_analysis/blob/main/Screenshot%202024-08-15%20173454.png)
![alt text](https://github.com/Samir4569/Airbnb_analysis/blob/main/Screenshot%202024-08-15%20173515.png)




## Key Questions 
* 1. Can you describe the vibe of each Seattle neighborhood using listing descriptions?
* 2. What are the busiest times of the year to visit Seattle? By how much do prices spike?
* 3. Is there a general upward trend of both new Airbnb listings and total Airbnb visitors to Seattle?

1) I performed a sentiment analysis and identified the most frequently used words in reviews for the top 20 neighborhoods. Based on these results, it seems fair to say that these neighborhoods are worth visiting.

Broadway: apartment, clean, comfortable, great, hill
Central Business District: apartment, clean, comfortable, great, perfect
Columbia City: city, clean, comfortable, great, nice
East Queen Anne: clean, comfortable, great, perfect, space
Eastlake: clean, comfortable, easy, great, nice
Fairmount Park: clean, comfortable, great, nice, west
First Hill: apartment, clean, comfortable, easy, great
Fremont: clean, comfortable, fremont, great, space
Gatewood: clean, comfortable, great, nice, recommend

2) Using the groupby and mean functions, I determined that July is the busiest month.
month - the sum of avilable places 
7    0.304679
6    0.334716
5    0.388274
4    0.401806

3) After determining the cheapest average price per month and analyzing new visitors, I found that new visitors arrived in the month with the lowest average price.

month - avg price for each month
1     267.474076
2     267.474076
3     267.474076
4     267.474076
5     267.474076
6     266.927041

df_new_visitor['month'].unique()
output : array([6])



