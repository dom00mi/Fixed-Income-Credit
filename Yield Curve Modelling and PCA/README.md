# Yield Curve Modelling and Principal Component Analysis

In this Jupyter notebook, I would like to show you how to show how PCA can enhance yield curve data analysis.

The main concept behind the PCA is to consider the correlation among features. If the correlation is very high among a subset of the features, PCA will attempt to combine the highly correlated features and represent this data with a smaller number of linearly uncorrelated features. The algorithm keeps performing this correlation reduction, finding the directions of maximum variance in the original high dimensional data and projecting them onto a smaller dimensional space. These newly derived components are known as principal components.
- Level
- Slope
- Curvature

PCA formalizes this viewpoint and allows us to evaluate when a segment of the yield curve has cheapened or richened beyond that prescribed by recent yield movements. The essence of PCA in the context of rates market is that most yield curve movements can be represented as a set of two to three independent driving factors the principal components (PCs) – along with their relative weightings. And, with these components, it is possible to reconstruct the original features.


## Short on PCA

One of the main difficulties in today’s environment is being able to visualize data easily. Dimensionality is the number of dimensions, features or input variables associated in a dataset and dimensionality reduction means reducing the number of features in a dataset. Principal component analysis (PCA) is a linear dimensionality reduction technique with applications in exploratory data analysis, visualization and data preprocessing.

The decomposition achieves three purposes:
- Decorrelation: factors are independent and their covariance is zero.
- Dimensionality reduction: a few factors explain the majority of the variance
- Data structure revealed: the analysis operates under the assumption of no hidden factors.

These advantages often come at the cost of loosing the information and difficulty to find the attribution. The Principal Component Analysis is not just a calibration exercise (i.e., factors and their loadings change and tell nothing), but the systematic application of the analysis allows to see its predictive powers. For example, rotation of factors reveals the change in behaviour of market participants or cyclicality.

##### Eigenvectors and Eigenvalues: their role in PCA

In linear algebra, an eigenvector or characteristic vector is a vector that has its direction unchanged (or reversed) by a given linear transformation. More precisely, an eigenvector, $\mathbf {v}$ of a linear tranformation $T$, is scaled by a constant factor, $\lambda$ (its corresponding eigenvalue) when the transformation is applied to it (i.e. ${\displaystyle T\mathbf {v} =\lambda \mathbf {v} }$).

To view the full code, please visit the Jupyter notebook!
