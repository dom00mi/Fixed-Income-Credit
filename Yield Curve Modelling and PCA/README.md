# Yield Curve Modelling and Principal Component Analysis

In this Jupyter notebook, I would like to show you how to show how PCA can enhance yield curve data analysis.

The main concept behind the PCA is to consider the correlation among features. If the correlation is very high among a subset of the features, PCA will attempt to combine the highly correlated features and represent this data with a smaller number of linearly uncorrelated features. The algorithm keeps performing this correlation reduction, finding the directions of maximum variance in the original high dimensional data and projecting them onto a smaller dimensional space. These newly derived components are known as principal components.
- Level
- Slope
- Curvature

PCA formalizes this viewpoint and allows us to evaluate when a segment of the yield curve has cheapened or richened beyond that prescribed by recent yield movements. The essence of PCA in the context of rates market is that most yield curve movements can be represented as a set of two to three independent driving factors the principal components (PCs) – along with their relative weightings. And, with these components, it is possible to reconstruct the original features.

To view the full code, please visit the Jupyter notebook!


## PCA

One of the main difficulties in today’s environment is being able to visualize data easily. Dimensionality is the number of dimensions, features or input variables associated in a dataset and dimensionality reduction means reducing the number of features in a dataset. Principal component analysis (PCA) is a linear dimensionality reduction technique with applications in exploratory data analysis, visualization and data preprocessing.

The decomposition achieves three purposes:
- Decorrelation: factors are independent and their covariance is zero.
- Dimensionality reduction: a few factors explain the majority of the variance
- Data structure revealed: the analysis operates under the assumption of no hidden factors.

These advantages often come at the cost of loosing the information and difficulty to find the attribution. The Principal Component Analysis is not just a calibration exercise (i.e., factors and their loadings change and tell nothing), but the systematic application of the analysis allows to see its predictive powers. For example, rotation of factors reveals the change in behaviour of market participants or cyclicality.

##### Eigenvectors and Eigenvalues: their role in PCA

In linear algebra, an eigenvector or characteristic vector is a vector that has its direction unchanged (or reversed) by a given linear transformation. More precisely, an eigenvector, $\mathbf {v}$ of a linear tranformation $T$, is scaled by a constant factor, $\lambda$ (its corresponding eigenvalue) when the transformation is applied to it (i.e. ${\displaystyle T\mathbf {v} =\lambda \mathbf {v} }$).

Eigenvalues and eigenvectors can be utilised to decomposed a matrix. Indeed, by the Spectral Theorem, the Covariance Matrix can be decomposed in:

$\Sigma = V\Lambda V^T$

where

- $\Lambda$ is a diagonal matrix with eigenvalues $\lambda _1 > \lambda _2 > ....> \lambda _n > 0 $, that we can write as:

${\displaystyle \operatorname {\Lambda} ={\begin{bmatrix}\lambda _{1}&&&0\\&\lambda _{2}\\&&\ddots \\0&&&\lambda _{n}\end{bmatrix}}}$


- $\operatorname {V}$ is a vectorised matrix of eigenvectors as:

${\displaystyle \operatorname {V} ={\begin{bmatrix} e _{1}& e _{2}\dots \ &e _{n}\end{bmatrix}}}$

- The eigenvectors $e(i)$ are orthogonal projections of the changes in data in directions of minimum variance, defined to the nearest sign (see Inverted Signs section below).2 Being orthogonal means that their covariance is zero: $Cov[e^{(i)}, e^{(j)}] = 0$. This property is the strength as well as weakness of the analysis.

Several properties below:

- Multiplying $VV^T = I$ gives an identity matrix, this applies to normalised eigenvectors.
- Confirmation of zero covariance:

$Cov[e^{(i)^T} \operatorname {X}, e^{(j)^T}\operatorname {X}] = e^{(i)^T} V\Lambda V^T e^{(j)^T} = [\Lambda]_{ij} = 0$

The fact that covariance of eigenvectors is zero makes it difficult (if not impossible) to create
analysis (strategies) that are based on simultaneous changes in several eigenmodes. This is a
problem in the light of the empirical phenomena of eigenvector rotation, for example.

##### Variance Explanation

Eigenvalue $\lambda_i$ is variance of the movements of a curve in each eigendirection. For example, the first factor explains:

$\displaystyle{\frac{\lambda_1}{\Sigma ^n _{i=1} \lambda _i}}$ of the total variance.

We would like to identify a few factors k that drive the evolution of the whole curve. To do this, just take eigenvectors with the largest corresponding eigenvalues. 

The goodness of fit statistic for the k-factor model is:

$\displaystyle{R^2 = \frac{\Sigma ^k _{i=1} \lambda _i}{\Sigma ^n _{i=1} \lambda _i}}$

##### Issues with PCA and its Numerical Methods

The same orthogonal basis can be represented by several combinations of eigenvectors that are linearly dependent. Therefore, numerical methods of matrix decomposition can produce seemingly different results. A few checks must be made:

- All eigenvalues must be positive and ranked.
- Some decompositions (e.g. QR) do not standardise eigenvectors (i.e. we would like $\sqrt{\Sigma _{k=1} e^2_{k}} = 1$)


We would like to represent the change as a combination of the PCA factors (i.e. $ \forall i: PC_i  $)

$\Delta f_j = PC_1 + PC_2 + ... + PC_i$
