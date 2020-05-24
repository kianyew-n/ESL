
## Chapter 2 Overview of Supervised Learning

### Types of supervised learning
- Quantitative (Regression)
- Qualitative (Classification)

### Types of Input
- Can be both Qualitative and Quantitative
- Some algorithms are more natural for **Qualitive** inputs, some are more for **Quantitative** and some are for **both**

#### Simplest approaches to prediction
- They can be used either for regression or classification

- **Linear Regression**
  - $\hat{Y}$ can be:
    -  **scalar** 
    -  or a **K-vector**, and as a result, $\beta$ is a p x K matrix of coefficients 
  - The input-output space of $(X, \hat{Y})$ is a **hyperplane**.
  - Linear regression has a difference "with" and  "without" constant
  - **With constant**
     - Then the **hyperplane includes the origin, and then is a subspace**
  - **Without constant**
    -  it cuts through the Y-axis at the point $(0, \hat{\beta_{0}})$
       -  Note to self: *Does this mean that it is not exactly a subspace?*









