[[Intro to DS]]

**PCA**: Unsupervised technique for extracting variance structure from high dimensional datasets

This helps reduce dimensions but keep key information about the data


### Covariance Matrix

### 1. Covariance (between two variables)

Covariance measures how two variables vary **together**.

For random variables XXX and YYY:

Cov(X,Y)=E[(X−μX)(Y−μY)]\text{Cov}(X,Y) = E[(X - \mu_X)(Y - \mu_Y)]Cov(X,Y)=E[(X−μX​)(Y−μY​)]

Sample version:

Cov(X,Y)=1n−1∑i=1n(xi−xˉ)(yi−yˉ)\text{Cov}(X,Y) = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})Cov(X,Y)=n−11​i=1∑n​(xi​−xˉ)(yi​−yˉ​)

Interpretation:

- Positive → move together
    
- Negative → move oppositely
    
- Near 0 → no linear relationship
    

---

### 2. Covariance Matrix

For data matrix X∈Rn×dX \in \mathbb{R}^{n \times d}X∈Rn×d:

- nnn samples
    
- ddd features
    

After **centering the data** (subtract mean from each feature):

Σ=1n−1XTX\Sigma = \frac{1}{n-1} X^T XΣ=n−11​XTX

Properties:

- Size: d×dd \times dd×d
    
- Symmetric
    
- Diagonal = variances of each feature
    
- Off-diagonal = covariances between features
    
- Positive semi-definite
    

Why important?  
→ It describes the **spread and orientation** of data in high-dimensional space.

---

# 📌 Principal Component Analysis (PCA)

### Goal:

Reduce dimensionality while preserving as much variance as possible.

---

### Core Idea

Find new orthogonal directions (principal components) that:

1. Capture maximum variance
    
2. Are uncorrelated
    

---

### Mathematical Definition

PCA finds eigenvectors of the covariance matrix:

Σv=λv\Sigma v = \lambda vΣv=λv

- vvv = principal component direction
    
- λ\lambdaλ = variance explained in that direction
    

Sort eigenvectors by descending eigenvalues.

---

### Geometric Interpretation

- First PC → direction of maximum variance
    
- Second PC → max variance orthogonal to first
    
- etc.
    

PCA = rotating the coordinate system to align with data spread.

---

### Projection

To reduce from ddd to kkk dimensions:

Z=XWkZ = X W_kZ=XWk​

- WkW_kWk​ = top kkk eigenvectors
    
- ZZZ = reduced representation
    

---

### Why PCA works

It minimizes reconstruction error:

min⁡∣∣X−Xk∣∣2\min ||X - X_k||^2min∣∣X−Xk​∣∣2

Equivalent to best rank-kkk approximation.

---

# 📌 Singular Value Decomposition (SVD)

For any matrix X∈Rn×dX \in \mathbb{R}^{n \times d}X∈Rn×d:

X=UΣVTX = U \Sigma V^TX=UΣVT

Where:

- U∈Rn×nU \in \mathbb{R}^{n \times n}U∈Rn×n → left singular vectors
    
- Σ∈Rn×d\Sigma \in \mathbb{R}^{n \times d}Σ∈Rn×d → diagonal matrix of singular values
    
- V∈Rd×dV \in \mathbb{R}^{d \times d}V∈Rd×d → right singular vectors
    

---

### Meaning of Each Part

- Columns of VVV → directions in feature space
    
- Columns of UUU → directions in data space
    
- Singular values → magnitude (importance)
    

---

### Key Properties

- Works for ANY matrix (not just square)
    
- Singular values ≥ 0
    
- Rank = number of nonzero singular values
    

---

# 📌 Connection Between PCA and SVD

If data is centered:

X=UΣVTX = U \Sigma V^TX=UΣVT

Then:

Σcov=1n−1XTX\Sigma_{cov} = \frac{1}{n-1} X^T XΣcov​=n−11​XTX

Substitute SVD:

XTX=VΣ2VTX^T X = V \Sigma^2 V^TXTX=VΣ2VT

This shows:

- Eigenvectors of covariance matrix = columns of VVV
    
- Eigenvalues = σi2n−1\frac{\sigma_i^2}{n-1}n−1σi2​​
    

👉 **PCA is SVD on centered data.**

That’s why in practice we compute PCA using SVD (more stable).

---

# 📌 Geometric Intuition of SVD

SVD decomposes a matrix into 3 transformations:

1. Rotate ( VTV^TVT )
    
2. Stretch ( Σ\SigmaΣ )
    
3. Rotate again ( UUU )
    

So any linear transformation = rotation + scaling + rotation.

---

# 📌 Dimensionality Reduction via SVD

Best rank-kkk approximation:

Xk=UkΣkVkTX_k = U_k \Sigma_k V_k^TXk​=Uk​Σk​VkT​

This minimizes Frobenius norm error.

Used in:

- PCA
    
- Image compression
    
- LSA (NLP)
    
- Recommendation systems
    

---