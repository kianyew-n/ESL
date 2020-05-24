# Chapter 2 Overview of Supervised Learning
*until line 91, the delivery of the content will be some parts on theory, and some parts on practical*

*After which, the content will just be subpoints that follows in a chapter.*

## Types of supervised learning
- Quantitative (Regression)
- Qualitative (Classification)

### Types of Input
- Can be both Qualitative and Quantitative
- Some algorithms are more natural for **Qualitive** inputs, some are more for **Quantitative** and some are for **both**

#### Simplest approaches to prediction
- They can be used either for regression $Y$ or classification $G$
1) Linear Regression
2) K-nearest neighbour

### Linear regression
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

### Nearset Neighbour method
#### Regression Context
- Nearest neighbours use those observations in the training set $T$ closest in input space to $x$ to form $\hat{Y}$
> $$ \hat{Y}(x)=  \frac{1}{k}  \sum_{x_{i} \in N_{k}(x)} y_{i} $$
- Closeness is measured by many different kinds of metric, the most common being the euclidean distance.
- For a prediction, we find the k observations that are closest to a particular x and just take the average of their responses.
  - **Can change closeness metric to discover different nearest neighbours and hence responses.**

#### Classification context
- For classification, we still take the **average response of the k nearest neighbours**.
  - Thus $\hat{G}$ is the **proportion of the target class in the neighbourhood**
- **Decision boundaries are more irregular, and responds to local clusters where one class dominates**
  - while Linear decision boundaries produced are rigid

- Note that the error will always be 0 for k = 1, and the training error is approximately an increasing function of k.
- An independent test set should be used to test the algorithm.


- **The effective number of parameters of KNN is actually $\frac{N}{k}$ instead of K**
  - It is **generally larger than $p$ as in the case of least squares**, and **decreases with increasing values of k**
  - Assuming that the neighbourhoods are non-overlapping, there would be **$\frac{N}{k}$ neighbourhoods**, and we need to have **parameter(mean in the case of gaussian) in each neighbourhood.**

- We should use **KNN methods for sceneario 2:**
>   2)  The training data in each class came from a mixture of 10 low-variance gaussian distributions, with individuals means, and these means are themselves distributed as gaussian.

- For scenario 1 , the gaussian data, decision boundaries of KNN will be unnecessarily noisy.

#### Comparing linear and nonlinear decision boundaries
- Linear decision boundaries are smooth and apparently stable to fit
  - But then **rely heavily on the assumption that a linear decision boundary is appropriate.**
  > **low variance and potentially high bias**
- **Nonlinear decision boundaries has no strict assumptions about the underlying data, and can adapt to any situation**.
  - any particular subregion of the decision boundary depends on a handful of input points and their particular positions, and thus is wriggly and unstablwe
  > **High variance and low bias**

**- 1-D KNN is the most popular for low-dimensional problems**
- To improve on KNN, we can do:
  - **Kernel methods** to give more weights to closer neighbouring points
  - Give **more weights to a particular feature** in $x_{i} \in [x_{1},x_{2},...,x_{p}]$

- To improve on LR
  - local regression using **locally weighted least squares**
  - **basis expansions** of original inputs
  - projection pursuit and NN; **sum of non-linearly transformed linear models**.

## 2.1 Statistical Decision Boundary
### Linear regression
- When we use Mean Squared Error:
  - The conditional expectation: $f(x) = E(Y|X = x)$ is the best prediction of $Y$ at any point $x \in X$

### KNN
- KNN directly implement this in the training data by making two approximations
  - Expectation is approximated by averaging over sample data
  - conditioning at a point is realized to conditioning on some region "close" to the target point
- For large training size, the points in the neighbourhood are close to the actual value of $x \in X$
- When k increases, the average will become more stable
> When we have infinite training data $n \rightarrow \infty$ *and* set k to be infinite $k \rightarrow \infty$ we have a universal approximator, since (1)all neighbours are the point $x$ itself and (2)the average is extremely stable, the number of parameters for KNN: $\frac{k}{n} \approx 0$

-  But doesnt happen because
-  1) we do not have infinite samples
   -  **For small samples, linear models perform better since we get a more stable estimate than KNN, although KNN can learn the linear structure can be learned by KNN from the data as well.**
-  2) When dimension $p$ or **equivalently in the case of KNN : $\frac{k}{n}$** increases, the metric size increases
-  The convergence of the rule still golds, but then the rate of convergence decreases with as the dimension increases. 
> $\frac{k}{n}$, if k increases, then we need a larger N to force this fraction to 0.

- Both KNN and linear regression end up approximating conditional expectation by takign the averages, but they differ in terms of model assuptions.
  - LR assumes that target function is approximated by a globally linear function
  - KNN assumes that target function is well approximateed by a locally constant function.

- Additive models ; sort of a combination of LR and KNN
  - It is a linear model, but then the optimal estimate for the additive model uses techniques such as KNN to approximate ***univariate*** conditional expectations simultaneously for each of the coordinate functions.
    - Takes away the problem of estimating a conditional expectation in high dimensions.

#### Alternate error function: L1 and 0-1 loss
##### Regression L1
- the optimal solution for L1: MAE is the conditional mean
  - L1 is has discontinuity in their derivatives and thus not used.
##### Classification 0-1
- The optimal solution for the 0-1 loss function ofr both **linear regression and KNN** is the **same as the Bayes classifier**
  - The probabilties are approximated by training sample proportions.















