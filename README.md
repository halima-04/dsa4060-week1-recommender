# DSA 4060 Week 1 Popularity Recommender

## Student

- **Name:** Halima Mohammed
- **Course:** DSA 4060 – Recommender Systems
- **Practical:** Week 1 – Build and Publish a Popularity Based Movie Recommender

## Project Overview

This project develops a simple movie recommendation system using the **MovieLens latest-small dataset**.

The project explores user-item rating interactions and implements two non-personalized recommendation approaches:

1. Minimum-rating popularity recommender
2. Weighted-rating recommender

The recommender is non-personalized, meaning that the same ranked list of movies is recommended to all users. This provides a simple baseline that can later be extended into a personalized recommender system.

The project includes data exploration, rating distribution analysis, interaction sparsity calculation, popularity-based recommendation, weighted-rating recommendation, testing, comparison of recommendation methods, and visualization.

## Dataset

This project uses the **MovieLens latest-small dataset** provided by GroupLens Research.

**Dataset source:**  
https://grouplens.org/datasets/movielens/

### Files Used

- `movies.csv`
- `ratings.csv`

### Main Columns

The `ratings.csv` file contains:

- `userId` - unique identifier for each user
- `movieId` - unique identifier for each movie
- `rating` - rating given by the user
- `timestamp` - time associated with the rating

The `movies.csv` file contains:

- `movieId` - unique identifier for each movie
- `title` - movie title
- `genres` - movie genre information

## Data Exploration

The dataset contains:

- **610 unique users**
- **9,742 movies in movies.csv**
- **9,724 movies with at least one rating**
- **100,836 total rating interactions**

The ratings range from **0.5 to 5.0**.

The overall mean rating is **3.502**.

### Rating Distribution

| Rating | Number of Ratings |
|---:|---:|
| 0.5 | 1,370 |
| 1.0 | 2,811 |
| 1.5 | 1,791 |
| 2.0 | 7,551 |
| 2.5 | 5,550 |
| 3.0 | 20,047 |
| 3.5 | 13,136 |
| 4.0 | 26,818 |
| 4.5 | 8,551 |
| 5.0 | 13,211 |

The most common rating was **4.0**, with **26,818 ratings**.

### Ratings Per User

The average number of ratings per user was **165.30**.

- Minimum: **20**
- First quartile: **35**
- Median: **70.5**
- Third quartile: **168**
- Maximum: **2,698**

### Ratings Per Movie

The average number of ratings per movie was **10.37**.

- Minimum: **1**
- First quartile: **1**
- Median: **3**
- Third quartile: **9**
- Maximum: **329**

## Interaction Sparsity

There are **5,931,640 possible user-movie interactions**.

There are **100,836 observed interactions**.

The calculated sparsity is:

**98.30%**

This means that most possible user-movie combinations do not contain a rating. This high sparsity is an important challenge in recommender systems.

## Recommendation Problem

A recommendation system can help users discover movies that they may be interested in.

For this practical, a simple popularity-based approach is used. Movies are ranked using information from historical user ratings.

Average rating alone can be misleading. For example, a movie with only two ratings of 5.0 would have a perfect average but very little rating evidence. A movie with hundreds of ratings and a high average rating provides stronger evidence of overall user approval.

Therefore, this project considers both:

- **Rating quality** - the average rating of a movie
- **Rating volume** - the number of ratings received by a movie

## Recommendation Methods

### 1. Minimum-Rating Popularity Recommender

The first method calculates the average rating and rating count for each movie.

A minimum threshold of **50 ratings** is applied. Only movies with at least 50 ratings are considered for the recommendation list.

The qualifying movies are ranked according to their average rating.

This reduces the possibility of movies with very few ratings receiving an artificially high ranking.

### 2. Weighted-Rating Recommender

The second method uses a weighted-rating formula:

**Weighted Score = (v / (v + m)) × R + (m / (v + m)) × C**

Where:

- **R** = average rating of the movie
- **v** = number of ratings received by the movie
- **C** = overall mean rating
- **m** = minimum rating-count threshold

For this project:

- **C = 3.502**
- **m = 27.0**

The value of `m` represents the 90th percentile of movie rating counts.

There were **976 movies** meeting the 90th-percentile threshold.

## Most-Rated Movie

The movie with the most ratings was:

**Forrest Gump (1994)**

- Rating count: **329**
- Average rating: **4.164**

Other highly rated movies with large numbers of ratings included:

- **Shawshank Redemption, The (1994)** - 317 ratings - 4.429 average
- **Pulp Fiction (1994)** - 307 ratings - 4.197 average
- **Silence of the Lambs, The (1991)** - 279 ratings - 4.161 average
- **Matrix, The (1999)** - 278 ratings - 4.192 average

## Highest-Rated Movies

When movies were ranked by average rating without considering the number of ratings, several movies received an average rating of **5.0**.

Examples include:

- **Lamerica (1994)** - 2 ratings - 5.0 average
- **Heidi Fleiss: Hollywood Madam (1995)** - 2 ratings - 5.0 average
- **Lesson Faust (1994)** - 2 ratings - 5.0 average
- **Belle époque (1992)** - 2 ratings - 5.0 average

This demonstrates why average rating alone is not a reliable popularity measure. A small number of ratings can produce an extremely high average.

## Top 10 Movies Using the 50-Rating Threshold

| Rank | Movie | Rating Count | Average Rating |
|---:|---|---:|---:|
| 1 | Shawshank Redemption, The (1994) | 317 | 4.429 |
| 2 | Godfather, The (1972) | 192 | 4.289 |
| 3 | Fight Club (1999) | 218 | 4.273 |
| 4 | Cool Hand Luke (1967) | 57 | 4.272 |
| 5 | Dr. Strangelove or: How I Learned to Stop Worrying and Love the Bomb (1964) | 97 | 4.268 |
| 6 | Rear Window (1954) | 84 | 4.262 |
| 7 | Godfather: Part II, The (1974) | 129 | 4.260 |
| 8 | Departed, The (2006) | 107 | 4.252 |
| 9 | Goodfellas (1990) | 126 | 4.250 |
| 10 | Casablanca (1942) | 100 | 4.240 |

The top movie after applying the 50-rating threshold was **Shawshank Redemption, The (1994)** with:

- **317 ratings**
- **4.429 average rating**

## Weighted-Rating Results

The overall mean rating was:

**3.502**

The 90th-percentile rating-count threshold was:

**27 ratings**

The number of movies meeting this threshold was:

**976 movies**

The top movie using the weighted-rating method was:

**Shawshank Redemption, The (1994)**

Weighted score:

**4.356**

## Comparison of the Two Methods

The two recommendation lists had **4 movies in common**.

The common movies were:

- **Shawshank Redemption, The (1994)**
- **Godfather, The (1972)**
- **Fight Club (1999)**
- **Godfather: Part II, The (1974)**

The minimum-rating method focuses on movies that have at least 50 ratings and then ranks them using their average rating.

The weighted-rating method considers both the average rating and the number of ratings. This helps reduce the influence of movies that have very high average ratings but very little rating evidence.


## Results Visualization

### Top 10 Movie Recommendations


<img width="1483" height="884" alt="image" src="https://github.com/user-attachments/assets/e77014d2-73e8-4f13-a651-bd59d61917ce" />



## Key Findings

1. The dataset contains **610 users and 9,742 movies**.
2. There are **100,836 rating interactions**.
3. The rating scale ranges from **0.5 to 5.0**.
4. The overall mean rating is **3.502**.
5. The dataset has **98.30% interaction sparsity**.
6. **Forrest Gump (1994)** has the highest number of ratings with **329 ratings**.
7. **Shawshank Redemption, The (1994)** is the top movie after applying the 50-rating threshold.
8. **Shawshank Redemption, The (1994)** also has the highest weighted score of **4.356**.
9. The two recommendation lists have **4 movies in common**.
10. Both rating quality and rating volume are important when building a popularity-based recommender.

## Interpretation

The results demonstrate that popularity-based recommendation provides a simple baseline for recommender systems.

Ranking movies using average rating alone can be misleading because movies with only a few ratings can receive very high average scores.

Applying a minimum rating threshold reduces this problem by requiring sufficient rating evidence before a movie is considered.

The weighted-rating approach further improves the ranking by combining average rating, rating count, and the overall dataset mean.

The fact that **Shawshank Redemption, The (1994)** was ranked first using both approaches indicates that it has both a high average rating and strong rating evidence in the dataset.

The **98.30% sparsity** also demonstrates an important challenge for recommender systems because most users have not rated most movies.

## Limitations

### Non-Personalized Recommendations

The recommender gives the same recommendations to every user and does not consider individual user preferences.

### Popularity Bias

The system may favour movies that are already popular and may give less exposure to less-rated movies.

### Cold-Start Problem

New movies with few or no ratings cannot be effectively ranked using this approach.

### No Time-Based Preferences

The recommender does not consider whether ratings are recent or old.

### Limited Diversity

The system does not explicitly optimize for diversity or novelty.

### No Personalized Explanations

The system does not explain recommendations based on an individual user's preferences.

## Possible Improvements

Future versions of the recommender could include:

- Content-based filtering
- Collaborative filtering
- Hybrid recommendation
- Personalized recommendations
- Precision@K
- Recall@K
- NDCG@K
- Catalogue coverage
- Diversity
- Novelty
- Time-aware recommendation

## How to Run

### Requirements

- Python 3
- Pandas
- Matplotlib
- Jupyter Notebook
- VS Code

### Clone the Repository

```bash
git clone https://github.com/halima-04/dsa4060-week1-recommender.git
```

### Enter the Project Folder

```bash
cd dsa4060-week1-recommender
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Download the Dataset

Download the MovieLens latest-small dataset from:

https://grouplens.org/datasets/movielens/

Place the following files inside the `data` folder:

```text
data/
├── movies.csv
└── ratings.csv
```

### Run the Notebook

Open:

`notebooks/week1_popularity_recommender.ipynb`

in VS Code.

Select the appropriate Python/Jupyter kernel and run all cells from beginning to end.

## Repository Structure

```text
dsa4060-week1-recommender/
│
├── data/
│   ├── movies.csv
│   └── ratings.csv
│
├── images/
│
├── notebooks/
│   └── week1_popularity_recommender.ipynb
│
├── .gitignore
├── README.md
└── requirements.txt
```

## Conclusion

This project demonstrates how a simple popularity-based movie recommender can be developed using the MovieLens latest-small dataset.

The analysis identified **610 users, 9,742 movies, and 100,836 rating interactions**. The dataset has **98.30% interaction sparsity**.

Both the minimum-rating and weighted-rating approaches identified **Shawshank Redemption, The (1994)** as the top recommendation.

The weighted-rating method produced a score of **4.356** for the movie.

Although the recommender provides a useful baseline, it is not personalized. Future work could introduce content-based filtering, collaborative filtering, hybrid recommendation, personalized ranking, and recommendation evaluation metrics.
