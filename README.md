# MSCS_634_Lab_5

# Clustering Techniques Using DBSCAN and Hierarchical Clustering

## Purpose

This lab was designed to provide hands-on experience with unsupervised machine learning techniques, specifically focusing on clustering algorithms. The central goal was to understand how different clustering methods behave when applied to the Wine dataset — a widely-used dataset that contains chemical analysis results of wines grown in the same region in Italy but derived from three different cultivars.

The primary objectives were:
- To understand how clustering algorithms can uncover hidden patterns or natural groupings in data.
- To evaluate the effects of data preprocessing, such as standardization, on clustering outcomes.
- To compare different clustering techniques (Hierarchical and DBSCAN) both visually and quantitatively.
- To gain practical skills in interpreting clustering results using visualization and evaluation metrics.

---

## Key Insights

### Data Exploration and Preprocessing
- The dataset includes 13 numerical features such as alcohol content, malic acid levels, ash, alkalinity, and more, across 178 samples.
- Initial exploration using `.head()`, `.info()`, and `.describe()` helped identify key characteristics such as feature ranges, missing values (none), and variance.
- Standardization using `StandardScaler` was crucial. Without standardizing, clustering would have been biased toward features with larger numerical scales, such as "Proline."

### Hierarchical Clustering
- Agglomerative Hierarchical Clustering was performed with varying values for `n_clusters`. A visual inspection of the dendrogram provided strong evidence for the presence of 3 major clusters.
- Using 2D PCA projection, we plotted the clustered data and observed good separation between the wine classes.
- The dendrogram was particularly useful in visualizing the nested structure of clusters, helping interpret the relationship between samples and groups.
- The clustering closely resembled the actual wine types, validating the effectiveness of this method for well-separated, spherical clusters.

### DBSCAN Clustering
- DBSCAN, a density-based clustering method, was effective in identifying not only dense clusters but also noise and outliers.
- The parameters `eps` and `min_samples` were tuned using visual techniques (k-distance graphs) and empirical testing.
- One major insight was DBSCAN’s sensitivity to `eps`. A very small `eps` yielded too many small clusters or treated most points as noise; a large value merged distinct clusters into one.
- While DBSCAN sometimes underperformed in matching the true wine classes, it provided additional value by highlighting noisy data that other algorithms ignored.

### Evaluation Metrics
To quantitatively assess clustering performance, the following metrics were used:
- **Silhouette Score**: Indicated how well-separated and cohesive the clusters were. Hierarchical clustering scored higher, suggesting more well-defined clusters.
- **Homogeneity Score**: Measured whether each cluster contained only members of a single class. Again, hierarchical clustering showed better alignment.
- **Completeness Score**: Assessed whether all members of a class were assigned to the same cluster. Results were consistent with homogeneity.

---

## Challenges and Decisions

- **Parameter Tuning (DBSCAN)**: The selection of `eps` was not straightforward. We experimented with k-distance plots and multiple iterations to find a value that maintained structure without over-merging clusters or labeling too many points as noise.
  
- **High-Dimensional Visualization**: Visualizing 13-dimensional data required the use of Principal Component Analysis (PCA) to reduce the feature space to two dimensions. This allowed meaningful visual representations of clusters, although some fidelity was lost in the transformation.

- **Standardization Decision**: Early attempts at clustering without standardization led to skewed and misleading cluster formations. Deciding to standardize the dataset significantly improved the outcome and comparability of features.

- **Cluster Evaluation Without Labels**: Since clustering is unsupervised, true labels are not used during training. This posed challenges for evaluating clustering quality. However, since the Wine dataset does include ground truth labels, we were able to assess clustering effectiveness using homogeneity and completeness, which wouldn't always be available in a real-world scenario.

---

## Conclusion

This lab emphasized the importance of thoughtful data preprocessing, careful parameter tuning, and multiple forms of analysis in unsupervised learning. Each algorithm had distinct strengths:

- **Hierarchical Clustering**: Easy to interpret and effective at finding globally coherent clusters. Ideal when the number of clusters is known or can be inferred from a dendrogram.

- **DBSCAN**: Robust to outliers and capable of discovering clusters of arbitrary shape. Ideal when dealing with noisy data or when the number of clusters is unknown.

Ultimately, hierarchical clustering provided a better match to the known wine classes, but DBSCAN gave valuable insight into sample density and potential anomalies. The lab experience deepened our understanding of how to apply clustering techniques in practice and interpret their results beyond raw outputs.
