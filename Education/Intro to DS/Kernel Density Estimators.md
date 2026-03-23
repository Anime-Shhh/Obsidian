#### **Kernel Density Estimation (KDE)**
- **Definition:** A non-parametric method to estimate the Probability Density Function (PDF) of a random variable.
- **Goal:** To smooth out a finite data sample into a continuous curve, effectively "smoothing" a histogram.
- **Requirement:** The area under the KDE curve must always sum to **1**.

**The Formula**

$$\hat{f}(x) = \frac{1}{nh} \sum_{i=1}^{n} K\left(\frac{x - x_i}{h}\right)$$
**Key Components**
1. **Kernel ($K$):**
    - The shape function placed over each data point.
    - Must be symmetric and integrate to 1.
    - _Common types:_ Gaussian (Normal distribution), Top-hat (uniform), Epanechnikov (parabolic).
    - _Note:_ The choice of kernel shape usually has a minor impact on the final result.
2. **Bandwidth ($h$):**
    - The "smoothing" parameter (like bin width in a histogram).
    - **Small $h$:** High variance, low bias (Curve is jagged/noisy).
    - **Large $h$:** Low variance, high bias (Curve is over-smoothed/washed out).
    - _Note:_ Choosing the right $h$ is critical. Common method: "Scott's Rule" or "Silverman's Rule."
**KDE vs. Histogram**
- **Histogram:** Discrete (bins), dependent on bin origin and width, discontinuous.
- **KDE:** Continuous, smooth, highlights the shape of the distribution better for small datasets.
![[Pasted image 20260212164513.png]]