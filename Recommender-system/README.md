# Book Recommender System

**Author:** Yamkela Kwakwi

## Introduction

This project aims to build a recommender system for books using the Book-Crossing dataset from Kaggle. The dataset comprises three primary files:

- **Users.csv**: Contains anonymized user IDs and demographic information (age, location) where available.
- **Books.csv**: Includes valid ISBNs, basic information about books (Title, Author, Year of Publication, Publisher), and cover image URLs in various sizes.
- **Ratings.csv**: Contains explicit, scaled, or implicit ratings (Book-Rating) provided by users.

## Objectives

- Build recommender systems using various collaborative filtering approaches:
  - User-based Collaborative Filtering (UB-CF)
  - Item-based Collaborative Filtering (IB-CF)
  - Matrix Factorization
- Evaluate the accuracy of the matrix factorization recommender system using cross-validation, both with and without regularization.
- Develop an ensemble model combining the IB and UB collaborative filtering approaches 

## Exploratory Data Analysis

### Data Exploration

The datasets contain the following observations:
- **Books**: 271,360
- **Users**: 278,858 (with only 105,283 having rated books)
- **Ratings**: 1,149,780 (with users often rating books multiple times)

A histogram analysis showed that many users have rated fewer than 200 books, leading to a decision to filter out users who rated less than 200 books for statistical significance.

### Data Engineering

- Simplified column names for ease of data manipulation.
- Identified the top book rater and noted the number of single ratings from users.

### Filtering Data

After filtering users in Canada, we focused on 87 unique users and 521 unique books for model building.

## Model Building

### Reshaping Data

Converted the data into a wide format suitable for user-based and item-based collaborative filtering models.

### User-Based Collaborative Filtering

- **Similarity Matrix**: Calculated user similarity using cosine similarity.

### Item-Based Collaborative Filtering

- **Similarity Matrix**: Computed similarities between books based on common ratings.

### Predictions and Comparisons

Predicted ratings were compared between the UB-CF and IB-CF models, revealing differing themes in recommendations.

### Matrix Factorization

- **Data Preparation**: Converted IDs to integers and split ratings into training and testing datasets.
- **Model Training**: Built and evaluated a matrix factorization model, applying L2 regularization to improve accuracy.

## Results

- **Matrix Factorization RMSE**: 
  - Without regularization: 4.04
  - With L2 regularization: 3.64 (indicating improved performance).

## Conclusion

The matrix factorization model with regularization performed well. Future work could focus on evaluating the accuracy of all four models and creating a website that utilizes the most accurate model or an ensemble of the top two. The website could feature a login system for capturing user IDs and provide top 10 recommendations based on user searches. Additionally, clustering analysis could be conducted to incorporate users and books not included in this model.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/YamkelaKwakwi/book-recommender-system.git
   cd book-recommender-system

2. Install required packages in R
  ```R
  install.packages(c("dplyr", "recosystem", "ggplot2", "tidyr"))
