
## Chapter 2 Overview of Supervised Learning

### Types of supervised learning
- Quantitative (Regression)
- Qualitative (Classification)

### Types of Input
- Can be both Qualitative and Quantitative
- Some algorithms are more natural for **Qualitive** inputs, some are more for **Quantitative** and some are for **both**

#### Simplest approaches to prediction
- They can be used either for regression or classification
1) Linear Regression
2) K-nearest neighbour

### Linear Regression
#### Regression Context
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
       -  Note to self: *Does this mean that the solution space is not exactly a subspace?*
 - The entire fitted surface is chraracterized by the $p$ parameters
   - Do not really need a lot of data to fit the model

#### Classification Context
- **Consider 2 possible DGP process:**
  1) The training data in each class is generated from bivariate gaussian distributions with **uncorrelated components** and **different means.**
  2)  The training data in each class came from a mixture of 10 low-variance gaussian distributions, with individuals means, and these means are themselves distributed as gaussian.

- A **mixture of gaussian** is best described in terms of the **generative model. **
  - One first **generates a discrete variable** that determines which of the component Gaussians to use, **then** generate an observation from the chosen density. 
- In the case of **one Gaussian per class**, *linear decision boundary* is the best.
- In the case of a **mixture tightly clustered gaussian**, a *disjoint and non-linear decision boundary* is more likely to be optimal
  - Harder to obtain as compared to linear decision boundary

- Linear regression is more suited for the 1st scenario
  > The training data in each class is generated from bivariate gaussian distributions with **uncorrelated components** and **different means.**
### Neareset Neighbour method













