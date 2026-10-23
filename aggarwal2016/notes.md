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

#### 1.3.1 Collaborative Filtering Models

Use ratings provided by multiple users to make recommendations.

The main challenge is that ratings matrices are *sparse*.
- Specified ratings are also known as *observed ratings*.

Most models use either inter-item correlation or inter-user correlation. Some use both.

**Types of models to impute missing values**:

1. <u>Memory-based methods</u>: also referred to as *neighborhood-based collaborative filtering algorithms*. AMong the earliest collaborative filtering algorithms. Ratings of user-item combinations are predicted based on their neighborhoods.
    - **Approaches**:
        - *User-based collaborative filtering*: determine users who are similar to a target user $A$; infer values for unobserved ratings of $A$ by computing weighted averages of the ratings of the similar users.
        - *Item-based collaborative filtering*: determine set of items $S$ which are most similar to target item $B$; the ratings of $S$ by user $A$ are used to predict whether $A$ will like item $B$.
    - **Pros**: Techniques are simple to implement, recommendations are easy to explain.
    - **Cons**: Do not work well with sparse matrices.
2. <u>Model-based methods</u>: machine learning and data mining models are used to make predictions; if models are parameterized, parameters are learned using optimization.
    - **Examples**: decision trees, rule-based models, Bayesian methods, [latent factor models](https://rafalab.dfci.harvard.edu/dsbook-part-2/highdim/latent-factor-models.html).

**Types of ratings**:

*Interval-based ratings*: a discrete set of ordered numbers is used to quantify like or dislike.

*Forced choice rating system*: system in which a neutral rating is missing.

*Ordinal ratings*: a discrete set of ordered categorical values to express like or dislike.

*Binary ratings*: users indicate only a like or dislike for the item.
- *Unary ratings*: special case, in which the user can specify a liking for an item but not a dislike; particularly common in [implicit feedback data sets](https://ieeexplore.ieee.org/document/4781121).

> NOTE: "Pre-substitution of missing ratings is not recommended in explicit ratings matrices. In explicit ratings matrices with both likes and dislikes, the substitution of missing entries with any value (such as a $0$ or the row/column/data mean) always leads to a significant amount of bias in the analysis." (p. 12)

**Collaborative filtering** can be seen as a special case of [missing value analysis](https://bookdown.org/drki_musa/dataanalysis/introduction-to-missing-data-analysis.html) in which the data matrix is very large and sparse.

**Collaborative filtering** can also be seen as a generalization of classification and regression modeling, in which any column is allowed to have missing values, instead of only the class (target) variable.

#### 1.3.2 Content-based Recommender Systems

Use descriptive attributes of items to make recommendations.

Ratings and the users' buying behavior are combined with content information avaiable on the items (e.g., for a movie, it could be its description).

Here, the descriptions of the items are labeled with ratings and used as training data to create a *user-specific* classification or regression model.

**Advantage**: making recommendations for new items, with insufficient ratings data.

**Disadvantages**:
- They might make obvious recommendations, avoiding items with a a set of keywords the user never consumed (which means the recommndations might lack diversity).
- They are not effective in providing recommendations for new *users*, since the training models require to leverage said user's past ratings.

#### 1.3.3 Knowledge-based Recommender Systems

Particularly useful when items are not consumed or purchased very often, thus sufficient ratings may not be available.

Ratings are not used for recommendations, but rather the similarity between customer requirements and item descriptions.

Facilitated by the use of *knowledge bases*, with data about rules and similarity functions to use during retrieval.

Provide user with more control over the recommendation process, due to the explicit specification of requirements (in contrast with collaborative filtering and content-based systems, which basically rely on the users' past actions).

**Types of interface (and corresponding knowledge)**:

1. <u>Constraint-based recommender systems</u>: user typically specify requirements or constraints (e.g., lower or upper limits) on items' attributes. Domain-specific rules are used to match the user requirements to item attributes. 
2. <u>Case-based recommender systems</u>: users specify targets or anchor points. Similarity metrics are defined on the item attributes to retrieve similar items to these cases.

**Methods of interactivity**:
1. <u>Conversational systems</u>: user preferences are determined iteratively, in a feedback loop.
2. <u>Search-based systems</u>: user preferences are defined by using a preset sequence of questions.
3. <u>Navigation-based systems</u>: the user specifies a number of change requests to the item being currently recommended, until they arrive at a desirable item.