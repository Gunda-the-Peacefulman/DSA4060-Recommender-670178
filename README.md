# DSA 4060 Personalized Movie Recommender

## Student Details

Name: Nicholas Kinyanjui  
Student ID: 670178  
Assigned User ID: 39

The assigned user was calculated using the last two numeric digits of the Student ID:
`78 MOD 40 = 38`, so the assigned User ID is `39`.

## Project Objective

This project builds a simple personalized movie recommender for one assigned user. It analyzes the movies that User 39 has already rated, identifies genre preferences from those ratings, and recommends five unrated movies that match the user's observed interests.

## Datasets

`movies.csv` contains the movie catalogue, including `movie_id`, `title`, and `genres`.

`ratings.csv` contains historical user ratings, including `user_id`, `movie_id`, and `rating`.

## Method / Approach

The notebook loads both datasets with pandas, checks their structure, and confirms whether missing values are present. It then filters the ratings for User 39 and treats movies rated `4.0` or higher as positive preference evidence.

Movie genres are converted into numerical one-hot features. Cosine similarity is then used to compare unrated movies with the movies User 39 liked. Movies already rated by User 39 are excluded before selecting the top five recommendations.

## How to Run

Required tools and libraries:

- Python
- Jupyter Notebook
- pandas
- numpy

Open `DSA4060_Recommender_670178.ipynb` in Jupyter Notebook or JupyterLab and run the cells from top to bottom. The notebook has already been executed, so the required outputs are visible in the submitted file.

## Results

The five recommended movies for User 39 are:

1. The Social Network
2. The Shawshank Redemption
3. Arrival
4. Crazy Rich Asians
5. Interstellar

These recommendations mainly reflect User 39's strongest observed preferences for Mystery, Comedy, Drama, and Biography. The recommended movies were selected because their genre profiles overlap with movies the user rated positively, such as `The Grand Budapest Hotel`, `Hidden Figures`, `Knives Out`, and `Sherlock Holmes`.

## Limitation and Improvement

A limitation of this recommender is that it only uses genre similarity. It does not consider actors, directors, release year, story themes, popularity, or rating behavior from similar users.

A realistic improvement would be to combine the content-based method with collaborative filtering. This would allow the recommender to use rating patterns from similar users, making the recommendations more personalized and accurate.
