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


