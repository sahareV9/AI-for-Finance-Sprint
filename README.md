# AI-for-Finance-Sprint
## Day 1:Completed Focused on the geometry of linear systems with finance-specific implementations.

## Day 2: Matrix Mechanics & The Cubic Wall $O(n^3)$
### **Objective**
Moving beyond geometry to computational efficiency—mastering Gaussian Elimination (LU Decomposition) and understanding why **Matrix Inversion** is a "production sin" for bank-scale data.
### **Key Insights**
*   **LU Decomposition:** Breaking down matrix $A$ into Lower ($L$) and Upper ($U$) triangular matrices. This is the engine behind `np.linalg.solve`.
*   **The Inversion Trap:** $A^{-1}$ is computationally expensive and numerically unstable. In a banking context, we solve for $Ax=b$ directly to preserve precision.
*   **Computational Complexity $O(n^3)$:** If my data size doubles, my computation time increases **8x**. This "Cubic Wall" is why efficient algorithm choice is critical at HCL/Citi scales.
### **The Lab**
- **Speed Test:** Compared `inv()` vs `solve()`.
- **Stress Test:** Visualized the scaling wall using matrices up to 4000x4000.

## Day 3: The Big Picture & Projections (Lec 10, 14-16)
### **The Fundamental Subspaces (Lec 10)**
Today I learned the "Fundamental Theorem of Linear Algebra." In my HCL/Citi experience, we dealt with massive datasets. Understanding the **Nullspace** allows me to identify redundant data points mathematically. If a risk factor falls in the Nullspace of our model, it has zero impact on the outcome.
### **Projections & OLS (Lec 14-16)**
When data is messy (which it always is in Finance), $Ax=b$ has no solution. 
- **Solution:** Project $b$ onto the Column Space of $A$. 
- **Application:** Built a **Linear Regression from scratch** using the Normal Equation: $(A^T A)x = A^T b$.

# Day 4: Spectral Theory & Singular Value Decomposition (SVD)
## 🎯 Objective
To master the "King of Dimensionality Reduction"—**SVD**. In this module, I moved beyond standard matrix solving to **Matrix Decomposition**, learning how to strip away noise and isolate the core "signals" within high-dimensional financial data.
## 🏦 Finance Context (The HCL/Citi Perspective)
During my 4 years at **HCLTech** supporting **Citi**, I managed systems dealing with massive, interconnected datasets. Today’s math provides the solution to the "Curse of Dimensionality":
*   **Principal Component Analysis (PCA):** SVD is the mathematical engine behind PCA. It allows us to take 100+ correlated market variables and compress them into 3-5 "Principal Components" that explain ~95% of market movement.
*   **Noise Reduction:** By truncating "Singular Values," we can filter out idiosyncratic market noise, leaving only the systematic risk factors (the "Eigen-risk").
## 🛠️ Technical Implementation: Market Signal Extraction
Instead of using black-box libraries, I implemented SVD-based noise reduction from scratch in **Google Colab**.
### **Key Steps:**
1.  **Data Generation:** Simulated a 10-stock banking sector portfolio with shared market trends and random noise.
2.  **Decomposition:** Deconstructed the covariance matrix into $U, \Sigma, V^T$.
3.  **Signal Isolation:** Identified the **Principal Component** (the largest Singular Value in $\Sigma$).
4.  **Reconstruction:** Rebuilt the "Clean" market trend by zeroing out low-value singular components (Noise).
### **Results:**
*   **Variance Explained:** My first Principal Component explained over **90% of the sector's movement**, significantly reducing the data dimensions needed for forecasting.
*   **Efficiency:** Proved that dimensionality reduction can bypass the $O(n^3)$ computational wall for large-scale risk engines.
## 📚 MIT OCW Reference
*   **Lecture 21 & 22:** Eigenvalues and Eigenvectors.
*   **Lecture 29:** Singular Value Decomposition (The "Fundamental Theorem of Linear Algebra").

# Day 5: Matrix Calculus & The Gradient
### **Concepts**
Mastered the **Jacobian Matrix** and **Partial Derivatives** in a vector space. If Linear Algebra is about 'state,' Calculus is about 'change.'
### **Finance Application (HCL/Citi Context)**
In banking, we call these 'Greeks' (Delta, Gamma). Matrix Calculus allows us to calculate how a complex portfolio of 1,000+ assets reacts to a 1bp shift in market volatility. This is the foundation of **Backpropagation** in Neural Networks.
### **The Lab**
Implemented a **Manual Gradient Descent** optimizer. Proved that by following the negative gradient, a model can 'learn' to minimize error iteratively.




