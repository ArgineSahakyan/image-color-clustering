# Image Color Reducer

This project explores how **unsupervised learning** can be used to reduce the number of colors in an image while preserving its overall visual appearance.

Three clustering algorithms are compared: **K-Means, DBSCAN, and HDBSCAN**.

## How it works

1. **Pixel Representation:** The image is converted into RGB format and represented as a NumPy array. Each pixel becomes a data point with three features: Red, Green, and Blue.

2. **Reshaping:** The original image shape `(height, width, 3)` is reshaped into `(number_of_pixels, 3)` so that clustering algorithms can process individual pixels.

3. **Clustering:** Similar RGB colors are grouped using:

   * **K-Means:** Groups pixels around a predefined number of cluster centers.
   * **DBSCAN:** Finds dense groups of similar colors without specifying the number of clusters in advance.
   * **HDBSCAN:** Builds on density-based clustering and detects clusters at different density levels.

4. **Reconstruction:** Representative colors are assigned back to the pixels and the data is reshaped to the original image dimensions.

## Algorithms and Parameters

### K-Means

* **Number of Clusters (`n_clusters`):** Defines the final number of representative colors.
* **Random State:** Keeps the result reproducible between runs.
* Several values of `K` were tested, with **K = 16** giving a good balance between color reduction and visual detail.

### DBSCAN

* **Epsilon (`eps`):** Defines how close two RGB points must be to be considered neighbors.
* **Min Samples:** Defines the minimum number of neighboring points needed to form a dense region.
* A random sample of **10,000 pixels** was used to make clustering more computationally manageable.
* Different `eps` values were tested to observe changes in the number of clusters and noise points.

### HDBSCAN

* **Min Cluster Size:** Defines the minimum size of a valid cluster.
* **Min Samples:** Controls how conservative the algorithm is when identifying dense regions.
* **Cluster Selection Method:** Both broader and more fine-grained cluster selection were explored.
* Different parameter combinations produced a clear trade-off between the number of detected color clusters and noise.

## Main Observation

For this image color reduction task, **K-Means produced the most practical result** because the final number of colors can be controlled directly.

DBSCAN and HDBSCAN were useful for exploring density-based clustering, but their results were more sensitive to parameter selection and the treatment of noise.

## Tools

**Python · NumPy · Matplotlib · Pillow · Scikit-learn · Google Colab · GitHub**
