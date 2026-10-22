# Recommender Systems: The Textbook

**TABLE OF CONTENTS**:

1. [An Introduction to Recommender Systems](#chapter-1-an-introduction-to-recommender-systems)
    - 1.1 [Introduction](#11-introduction)
    - 1.2 [Goals of Recommender Systems](#12-goals-of-recommender-systems)
    - 1.3 [Basic Models of Recommender Systems](#13-basic-models-of-recommender-systems)

---

## Chapter 1: An Introduction to Recommender Systems

### 1.1 Introduction

**User**: entity to which the recommendation is provided.

**Item**: product being recommended.

**Knowledge-based recommender systems**: recommendations are based on *user*-specified requirements rather than history.

**Collaborative filtering**: using ratings from multiple users in a *collaborative* way to predict missing ratings.

**Content-based recommender systems**: users' ratings and attribute descriptions are leveraged to make predictions.

### 1.2 Goals of Recommender Systems

**Recommendation problem**:
- Prediction version of problem:
    - Predicts rating for user-item combination. Assumes training data is available.
    - For $m$ users and $n$ items, corresponds to an incomplete $m \times n$ matrix.
    - Also referred to as *matrix completion problem*.
- Ranking version of problem:
    - Recommends the top-$k$ items for a particular user (or less commonly  the top-$k$ users to target with an item).
    - Also referred to as *top-$k$ recommendation problem*.

**Common operational and technical goals**:
1. <u>Relevance</u>: recommending items which are relevant to the users.
2. <u>Novelty</u>: recommending items the user has not seen in the past.
3. <u>Serendipity</u>: recommending items which are somewhat unexected, coming across as a "lucky discovery".
4. <u>Increasing recommendation diversity</u>: avoid recommending items which are too similar.

**Commercial recommender systems**:
- GroupLens Recommender System
- Amazon.com Recommender System
- Netflix Movie Recommender System
- Google News Personalization System
- Facebook Friend Recommendations

### 1.3 Basic Models of Recommender Systems

#### Collaborative Filterring Models

Use ratings provided by multiple users to make recommendations.

The main challenge is that ratings matrices are *sparse*.
- Specified ratings are also known as *observed ratings*.

Most models use either inter-item correlation or inter-user correlation. Some use both.

Types of models to impute missing values:

1. <u>Memory-based methods</u>: also referred to as *neighborhood-based collaborative filtering algorithms*. AMong the earliest collaborative filtering algorithms. Ratings of user-item combinations are predicted based on their neighborhoods.
    - *User-based collaborative filtering*:
    - *Item-based collaborative filtering*:
2. <u>Model-based methods</u>