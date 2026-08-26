# image-color-clustering

This project explores image color reduction using unsupervised learning.

The image pixels are represented as RGB values and clustered using:

K-Means
DBSCAN
HDBSCAN

Each pixel is treated as a data point with three features: R, G and B.

Approach

The image is converted to a NumPy array and reshaped from:

(height, width, 3)

to:

(number_of_pixels, 3)

Clustering is then applied to group similar colors.

K-Means

K-Means was tested with different values of K.
The final version uses K=16, producing a reduced image with 16 representative colors.

DBSCAN

DBSCAN was tested with different eps values.
Since it does not provide centroids directly, the average RGB value of each cluster was used as its representative color.

HDBSCAN

HDBSCAN was tested with different min_cluster_size, min_samples, and cluster selection settings.
The experiments showed a trade-off between the number of clusters and the amount of noise.

Result

Among the tested approaches, K-Means gave the most suitable result for this color reduction task because the number of output colors can be controlled directly.

Tools

Python · NumPy · Matplotlib · Pillow · Scikit-learn · Google Colab
