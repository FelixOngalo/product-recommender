# Item-Based Collaborative Filtering Recommender in R

## Project Overview

This project develops an **item-based collaborative filtering recommender system in R**. The system analyses customer-product interactions using a sparse customer-product matrix and recommends products based on the similarity between items.

**Cosine similarity** is used to identify products with similar customer interaction patterns. The recommender is evaluated using a **leave-one-out validation strategy** and compared against a simple **popularity-based baseline**.

The project demonstrates how recommendation algorithms can be developed, evaluated, and compared using reproducible R workflows.

## Objectives

- Build a customer-product interaction matrix.
- Handle sparse transactional data efficiently.
- Calculate item-to-item similarity using cosine similarity.
- Generate personalised product recommendations.
- Evaluate recommendation performance using leave-one-out validation.
- Establish a popularity-based baseline.
- Compare personalised recommendations against the baseline.

## Methodology

### 1. Data Preparation

Customer-product interaction data is cleaned and transformed into a matrix where:

- Rows represent customers.
- Columns represent products.
- Values represent customer-product interactions.

Because most customers interact with only a small proportion of available products, the resulting matrix is typically **sparse**.

### 2. Item-Based Collaborative Filtering

Instead of comparing customers directly, the recommender compares **products based on the customers who interacted with them**.

For example, if customers who purchase Product A frequently also purchase Product B, the two products will have a higher similarity score.

This allows the system to recommend products that are similar to those a customer has previously interacted with.

### 3. Cosine Similarity

Cosine similarity measures the similarity between two product vectors.

A higher similarity indicates that the products have more similar customer-interaction patterns.

The similarity matrix is then used to identify the most relevant candidate products for each customer.

### 4. Recommendation Generation

For each customer, previously interacted products are used as the basis for generating recommendations.

The system:

1. Identifies products associated with the customer.
2. Finds similar products using the item-item similarity matrix.
3. Removes products the customer has already interacted with.
4. Ranks the remaining candidates.
5. Returns the highest-ranked recommendations.

### 5. Leave-One-Out Evaluation

The recommender is evaluated using **leave-one-out validation**.

One known customer-product interaction is temporarily held out and treated as the test item.

The recommender then attempts to recover the held-out product from the customer's remaining interaction history.

This provides a realistic test of whether the system can recommend an item that the customer has not recently interacted with.

### 6. Popularity Baseline

A popularity-based recommender is used as a benchmark.

Instead of using personalised item similarities, the baseline recommends the most frequently interacted-with products.

Comparing the two approaches helps determine whether collaborative filtering provides value beyond simply recommending popular products.

## Analytical Workflow

```text
Customer-Product Transactions
            ↓
      Data Preparation
            ↓
   Sparse Interaction Matrix
            ↓
      Item Similarity
            ↓
     Cosine Similarity
            ↓
  Personalised Recommendations
            ↓
   Leave-One-Out Evaluation
            ↓
    Popularity Baseline
            ↓
     Model Comparison
```

## Technologies Used

- **R**
- `dplyr`
- `Matrix`
- `ggplot2`
- Sparse matrix operations
- Cosine similarity
- Collaborative filtering
- Recommender-system evaluation

## Evaluation

The recommender is evaluated using metrics appropriate for ranked recommendation systems, such as:

- Hit Rate
- Recall@K
- Precision@K
- Mean Reciprocal Rank (MRR), where applicable

The results are compared with the popularity baseline to assess whether personalised item-based recommendations improve the likelihood of recovering held-out customer preferences.

## Project Structure

```text
item-based-recommender-r/
│
├── data/
│   └── customer_product_transactions.csv
│
├── R/
│   ├── 01_data_preparation.R
│   ├── 02_sparse_matrix.R
│   ├── 03_cosine_similarity.R
│   ├── 04_recommendations.R
│   ├── 05_leave_one_out.R
│   └── 06_baseline_comparison.R
│
├── figures/
│   ├── interaction_distribution.png
│   ├── similarity_distribution.png
│   └── model_comparison.png
│
├── results/
│   ├── recommendations.csv
│   └── evaluation_metrics.csv
│
├── report/
│   └── recommender_analysis.qmd
│
└── README.md
```

## Business Application

Recommendation systems can help businesses personalise customer experiences and increase product discovery.

Potential applications include:

- Product recommendations
- Cross-selling
- Personalised marketing
- E-commerce recommendations
- Customer engagement
- Targeted promotional campaigns

For example, a retailer could use the system to recommend complementary products based on the purchasing behaviour of customers with similar interaction patterns.

## Key Skills Demonstrated

This project demonstrates practical skills in:

- R programming
- Recommender systems
- Collaborative filtering
- Sparse matrix manipulation
- Similarity modelling
- Cosine similarity
- Recommendation ranking
- Machine learning evaluation
- Baseline model comparison
- Data visualisation
- Reproducible analytics

## Limitations

Item-based collaborative filtering can struggle when products have very few interactions. New products and customers may also suffer from the **cold-start problem**.

The approach also relies heavily on historical interaction patterns and does not incorporate product attributes, customer demographics, price, or contextual information.

## Future Improvements

Potential extensions include:

- User-based collaborative filtering
- Matrix factorisation
- Hybrid recommendation models
- Content-based recommendations
- Time-aware recommendations
- Incorporating product metadata
- Personalised ranking models
- Handling cold-start customers and products

## Conclusion

This project demonstrates an end-to-end item-based recommendation workflow in R, from transforming transactional data into a sparse interaction matrix through similarity calculation, recommendation generation, and out-of-sample evaluation.

The comparison with a popularity baseline provides a practical benchmark for determining whether personalised recommendations offer additional value over simple popularity-based strategies.
