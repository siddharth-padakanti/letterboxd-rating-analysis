# Letterboxd Movie Ratings Analysis

A data science project exploring my personal movie watching history from [Letterboxd](https://letterboxd.com). The goal is to understand what drives my ratings and whether my taste can be modeled using machine learning.

---

## Overview

This project analyzes 1,005 movies I've watched and rated on Letterboxd. The original export only contains movie names, watch dates, and personal ratings — so the dataset was expanded by adding **genres**, **runtime**, and **average community ratings** for each film to enable meaningful analysis.

The notebook covers:
- Exploratory data analysis and visualization
- Comparing personal ratings against community averages
- Attempting to predict my ratings using genre and runtime data
- Clustering movies based on taste patterns
- Building a simple content-based movie recommender

---

## Project Structure

```
letterboxd-analysis/
│
├── data/
│   └── ratings.csv           # Personal Letterboxd export (expanded)
│
├── notebooks/
│   └── analysis.ipynb        # Main analysis notebook
│
└── README.md
```

---

## Dataset

The dataset was originally exported from Letterboxd and then manually expanded to include additional features:

| Column | Description |
|---|---|
| `Name` | Movie title |
| `Year` | Release year |
| `Rating` | My personal rating (1.0 – 5.0) |
| `Date` | Date I watched the movie |
| `Genres` | Genre tags (multi-label) |
| `Runtime` | Movie duration in minutes |
| `Average Rating` | Community average rating on Letterboxd |

---

## Key Findings

- **Genre and runtime alone cannot predict my ratings** — all regression models produced near-zero R² scores, suggesting personal taste is too nuanced for metadata to capture.
- **My ratings correlate weakly with the community average** (R² ≈ 0.39), but the relationship exists — I tend to rate movies I enjoy above the community consensus, and vice versa.
- **Genres I rate highest:** Documentary, Music, Mystery, Animation, and War films.
- **Genres I rate lowest:** TV Movies, Romance, and Action films.
- **KMeans clustering did not produce clean groupings**, likely due to the sparse, binary nature of one-hot encoded genre data.
- **The KNN recommender produced intuitive results** — similar movies were grouped correctly by genre and style.

---

## Tools & Libraries

- Python 3
- [pandas](https://pandas.pydata.org/)
- [NumPy](https://numpy.org/)
- [matplotlib](https://matplotlib.org/)
- [scikit-learn](https://scikit-learn.org/)

---

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/letterboxd-analysis.git
   cd letterboxd-analysis
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib scikit-learn jupyter
   ```

3. **Run the notebook**
   ```bash
   jupyter notebook notebooks/analysis.ipynb
   ```

> To use your own data, export your ratings from Letterboxd via **Profile → Export Your Data** and replace `data/ratings.csv`. You will need to add the `Genres`, `Runtime`, and `Average Rating` columns manually or via an API such as [TMDB](https://www.themoviedb.org/documentation/api).

---

## Limitations

- The expanded columns (genres, runtime, average rating) were added externally and may contain minor inaccuracies.
- With only ~1,000 entries, the dataset is relatively small for machine learning.
- Personal rating behavior (e.g. batch-watching a director's filmography) can skew year-based trends.

---

## Author

Made by **Siddharth Padakanti** — feel free to fork this and run it on your own Letterboxd data (needs manual addition of `Genres`, `Runtime`, and `Average Rating` columns or via an API such as [TMDB](https://www.themoviedb.org/documentation/api))!