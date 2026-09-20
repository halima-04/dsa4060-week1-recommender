# DSA 4060 Week 1 Popularity Recommender

## Student
- Name: Halima Mahdi
- Student number: 670315

## Project overview
This project explores MovieLens user-item ratings and builds two non-personalized movie recommendation baselines:
1. Minimum-rating popularity recommender
2. Weighted-rating recommender

## Dataset
MovieLens latest-small from GroupLens:
https://grouplens.org/datasets/movielens/

Place `movies.csv` and `ratings.csv` in the `data/` folder.

## Methods
1. Rating-count and average-rating exploration
2. Minimum-rating popularity baseline
3. Weighted-rating baseline
4. Basic tests and parameter comparison
5. Optional genre filtering

## How to run
```bash
python -m pip install -r requirements.txt
```
Then open `notebooks/week1_popularity_recommender.ipynb` in VS Code and run all cells from top to bottom.

## Key findings
Complete this section after running the notebook using the actual values produced.

## Limitations
The recommender is not personalized because every user receives the same ranked list. It can also create popularity bias, has a cold-start problem for new movies, does not model changing preferences, and does not guarantee diversity or novelty.

## Repository structure
```text
dsa4060-week1-recommender/
├── data/
│   ├── movies.csv
│   └── ratings.csv
├── images/
│   └── top10_recommendations.png
├── notebooks/
│   └── week1_popularity_recommender.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

## Screenshot
The notebook saves the Top 10 chart to `images/top10_recommendations.png`.
<img width="1483" height="884" alt="image" src="https://github.com/user-attachments/assets/69a66754-0869-4d68-be78-67ee17be21db" />


## Dataset attribution
MovieLens latest-small is provided by GroupLens Research. Retain the dataset README/licence information when distributing permitted dataset files.
