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

`movies.csv` contains the movie catalogue, including `movie_id`, `title`, and `genres`. It has 36 rows and 3 columns.

`ratings.csv` contains historical user ratings, including `user_id`, `movie_id`, and `rating`. It has 440 rows and 3 columns.

The notebook confirmed that both datasets have 0 missing values, so no missing-value cleaning was needed before building the recommender.

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

User 39 rated 13 movies. Four of those movies had ratings of `4.0` or higher, so they were treated as positive examples:

| Positively Rated Movie | Genres | Rating |
| --- | --- | ---: |
| The Grand Budapest Hotel | Comedy, Drama | 4.5 |
| Hidden Figures | Drama, Biography | 4.0 |
| Knives Out | Mystery, Comedy | 4.0 |
| Sherlock Holmes | Mystery, Action | 4.0 |

The genre summary from the notebook shows why these genres matter:

| Genre | Movies Rated by User 39 | Average Rating | Ratings of 4.0 or Higher |
| --- | ---: | ---: | ---: |
| Mystery | 2 | 4.00 | 2 |
| Action | 1 | 4.00 | 1 |
| Comedy | 3 | 3.83 | 2 |
| Biography | 2 | 3.75 | 1 |
| Drama | 8 | 3.44 | 2 |
| Sports | 4 | 3.00 | 0 |
| Horror | 1 | 2.50 | 0 |
| Thriller | 1 | 2.50 | 0 |
| Adventure | 1 | 2.00 | 0 |
| Animation | 1 | 2.00 | 0 |

This suggests that User 39 especially likes Mystery, Comedy, Biography, and some Drama movies. Sports movies appeared often in the user's history, but none received a rating of 4.0 or higher, so Sports was not treated as a strong positive preference.

The five recommended movies are:

| Rank | Recommended Movie | Genres | Similarity Score | Interpretation |
| ---: | --- | --- | ---: | --- |
| 1 | The Social Network | Drama, Biography | 0.375 | This shares Drama and Biography with `Hidden Figures`, which User 39 rated 4.0. |
| 2 | The Shawshank Redemption | Drama | 0.354 | This matches the Drama side of liked movies such as `The Grand Budapest Hotel` and `Hidden Figures`. |
| 3 | Arrival | Sci-Fi, Drama | 0.250 | This includes Drama, a genre that appears in two positively rated movies. |
| 4 | Crazy Rich Asians | Romance, Comedy | 0.250 | This includes Comedy, which appears in two positively rated movies and has a strong average rating of 3.83. |
| 5 | Interstellar | Sci-Fi, Drama | 0.250 | This includes Drama and is similar by genre to the user's positively rated Drama movies. |

The similarity score is the average cosine similarity between each unrated movie and the movies User 39 rated `4.0` or higher. A higher score means the movie has stronger genre overlap with the user's liked movies. All five recommended movies were checked against User 39's rating history, and none had already been rated by the user.

## Limitation and Improvement

A limitation of this recommender is that it only uses genre similarity. It does not consider actors, directors, release year, story themes, popularity, or rating behavior from similar users.

A realistic improvement would be to combine the content-based method with collaborative filtering. This would allow the recommender to use rating patterns from similar users, making the recommendations more personalized and accurate.
