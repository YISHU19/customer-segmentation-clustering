# Customer Segmentation with K-Means and DBSCAN

Groups mall customers into segments by income and spending behaviour, comparing a centroid-based algorithm (**K-Means**) with a density-based one (**DBSCAN**).

## Dataset

The [Mall Customers](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python) dataset: 200 customers with gender, age, annual income (k$) and a spending score (1–100).

## Approach

1. **Exploration:** descriptive statistics, feature distributions, gender split, pairplots and a correlation heatmap
2. **Dimensionality reduction:** PCA on the scaled features to look for natural structure
3. **Feature selection:** annual income and spending score, which show the clearest cluster structure, standardised before clustering
4. **K-Means:** the number of clusters chosen with the elbow method and silhouette scores across k = 2–10
5. **DBSCAN:** `eps` chosen from a k-distance plot (`eps = 0.30`, `min_samples = 5`)
6. **Comparison:** side-by-side cluster plots plus silhouette and Davies–Bouldin scores

## Results

| Algorithm | Clusters | Noise points | Silhouette ↑ | Davies–Bouldin ↓ |
|---|---|---|---|---|
| **K-Means (k = 5)** | 5 | 0 | **0.555** | **0.572** |
| DBSCAN | 7 | 35 | 0.524 | 0.580 |

K-Means gives the cleaner segmentation here: five well-separated groups, such as high-income/low-spend and low-income/high-spend customers, that map directly onto marketing personas. DBSCAN finds similar dense cores but splits some groups and labels 35 customers (17.5%) as noise. That makes it useful for spotting unusual customers, but less practical for assigning every customer to a segment.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook customer_segmentation.ipynb
```

The data is in `data/`, so the notebook runs top to bottom with no setup.

## Tech

Python · scikit-learn · pandas · NumPy · Matplotlib · seaborn
