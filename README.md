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
*Can you describe the vibe of each Seattle neighborhood using listing descriptions?
*What are the busiest times of the year to visit Seattle? By how much do prices spike?
*Is there a general upward trend of both new Airbnb listings and total Airbnb visitors to Seattle?

I also split the data into train and tests sets with a test size of 20%.   

I tried two different models and evaluated them using Accuracy_score and Classification Report. I used accuracy_score and classification_report because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried two different models:
*	**k-nearest neighbor** – Baseline for the model
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 



**Classification Report:**

|               | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|---------|
| 0             | 0.69      | 0.67   | 0.68     | 492     |
| 1             | 0.80      | 0.81   | 0.81     | 808     |
| **Accuracy**  |           |        | 0.76     | 1300    |
| **Macro Avg** | 0.74      | 0.74   | 0.74     | 1300    |
| **Weighted Avg** | 0.76   | 0.76   | 0.76     | 1300    |

*	**k-nearest neighbor**: accuracy_score =  0.76

**Classification Report:**

|               | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|---------|
| 0             | 0.80      | 0.73   | 0.76     | 492     |
| 1             | 0.84      | 0.89   | 0.87     | 808     |
| **Accuracy**  |           |        | 0.83     | 1300    |
| **Macro Avg** | 0.82      | 0.81   | 0.81     | 1300    |
| **Weighted Avg** | 0.83   | 0.83   | 0.83     | 1300    |




