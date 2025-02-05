<h1>Theory of popular Machine Learning algorithms</h1>

Author: [Kaitao Yang](https://www.linkedin.com/in/kaitaoyang/), founder of [DL-APPLIED](https://dlapplied.com/deep-learning-training/), VP of Machine Learning at [Epicore Biosystems, Inc.](https://www.epicorebiosystems.com/)

<h1> Table of Contents </h1>

- [Notation](#notation)
- [Linear models](#linear-models)
  - [Linear regression](#linear-regression)
  - [Logistic regression (for classification)](#logistic-regression-for-classification)
  - [Softmax regression, or maximum entropy model (for classification)](#softmax-regression-or-maximum-entropy-model-for-classification)
    - [Proof that softmax regression and logistic regression are equivalent](#proof-that-softmax-regression-and-logistic-regression-are-equivalent)
- [Support vector machine (SVM)](#support-vector-machine-svm)
  - [Linear SVM in linearly separable case (hard margin)](#linear-svm-in-linearly-separable-case-hard-margin)
  - [Linear SVM (soft margin)](#linear-svm-soft-margin)
  - [Non-linear SVM (kernel tricks)](#non-linear-svm-kernel-tricks)
- [Decision trees](#decision-trees)
  - [ID3 (Iterative Dichotomiser 3)](#id3-iterative-dichotomiser-3)
  - [C4.5 (Successor of ID3)](#c45-successor-of-id3)
  - [CART (Classification And Regression Trees)](#cart-classification-and-regression-trees)
  - [Comparison](#comparison)
- [Boosting](#boosting)
  - [Adaboost for binary classification](#adaboost-for-binary-classification)
  - [Gradient boosting for regression (simple algorithm)](#gradient-boosting-for-regression-simple-algorithm)
  - [XGBoost for regression](#xgboost-for-regression)
- [Naive Bayes for classification](#naive-bayes-for-classification)
  - [Train](#train)
    - [`P(Y)`](#py)
    - [`P(X|Y)` for discrete X](#pxy-for-discrete-x)
      - [Avoid zero value of probability](#avoid-zero-value-of-probability)
    - [`P(X|Y)` for continuous X](#pxy-for-continuous-x)
  - [Test](#test)
- [EM algorithm](#em-algorithm)
  - [Gaussian Mixture Model (GMM) using EM](#gaussian-mixture-model-gmm-using-em)
- [Variance-bias tradeoff](#variance-bias-tradeoff)

# Notation

$$
\begin{aligned}
&(\mathbf{x},y)\quad &\text{ a data point with input feature: } \mathbf{x}, \text{ and label: } y.\\
&D\quad &\text{ a set of data points.}\\
&\mathbb{D}\quad &\text{ a collection of datasets.}\\
&N\quad &\text{ number of data points.}\\
&C\quad &\text{ number of classes.}\\
&\mathbf{R}^{m \times n}\quad &\text{ an } m \text{-by-} n \text{ matrix of real numbers.}\\
&\mathbf{X}\quad &\text{ a feature matrix (design matrix) of dimension: } \mathbf{R}^{N \times M}\\
&\mathbf{1}_{\{condition\}}\quad &\text{ indicator function: 1 if condition is true, 0 otherwise.}\\
&{\mathcal {N}}(x;\mu,\sigma ^{2})\quad & \text{Gaussian distribution with mean and variance: } \mu,\;\sigma^2\\
&\mathbf{w} \cdot \mathbf{x}\quad & \text{inner product between two vectors: } \mathbf{w} \text{ and } \mathbf{x}.\\
\end{aligned}
$$

# Linear models

## Linear regression

$$
\begin{aligned}
&y = f(\mathbf{x};{\theta}) = f(\mathbf{x};\mathbf{w},b) = \mathbf{w} \cdot \mathbf{x} + b \\
\text{where} \\
&\theta \text{ represents the model parameters, which include } \mathbf{w} \text{ (weights) and } b \text{ (bias).}
\end{aligned}
$$

## Logistic regression (for classification)

$$
\begin{aligned}
P(Y=c|\mathbf{X}=\mathbf{x}) &=
\begin{cases}
    \frac{e^{f(\mathbf{x};\theta_c)}}{1+\sum_{c'=1}^{C-1}e^{f(\mathbf{x};\theta_{c'})}}, & \text{if } c=1,2,\dots,C-1 \\
    \frac{1}{1+\sum_{c'=1}^{C-1}e^{f(\mathbf{x};\theta_{c'})}}, & \text{if } c=C
\end{cases} \\
\text{where} \\
&C \text{ is the number of classes.}
\end{aligned}
$$

## Softmax regression, or maximum entropy model (for classification)

$$
\begin{aligned}
P(Y=c|\mathbf{X}=\mathbf{x})=\frac{e^{f(\mathbf{x};\theta_c)}}{\sum_{c'=1}^{C}e^{f(\mathbf{x};\theta_{c'})}},\;c=1,2,\dots,C
\end{aligned}
$$

### Proof that softmax regression and logistic regression are equivalent
Starts from softmax regression:

$$
\begin{aligned}
P(Y=c|\mathbf{X}=\mathbf{x})&=\frac{e^{f(\mathbf{x};\theta_c)}}{\sum_{c'=1}^{C}e^{f(\mathbf{x};\theta_{c'})}},\\
&=\frac{e^{-f(\mathbf{x};\theta_C)} e^{f(\mathbf{x};\theta_c)}}{e^{-f(\mathbf{x};\theta_C)} \sum_{c'=1}^{C}e^{f(\mathbf{x};\theta_{c'})}},\\
&=\frac{e^{[f(\mathbf{x};\theta_c)-f(\mathbf{x};\theta_C)]}}{\sum_{c'=1}^{C}e^{[f(\mathbf{x};\theta_{c'})-f(\mathbf{x};\theta_C)]}},\\
&=\frac{e^{[f(\mathbf{x};\theta_c)-f(\mathbf{x};\theta_C)]}}{e^{[f(\mathbf{x};\theta_{C})-f(\mathbf{x};\theta_C)]} + \sum_{c'=1}^{C-1}e^{[f(\mathbf{x};\theta_{c'})-f(\mathbf{x};\theta_C)]}},\\
&=\frac{e^{[f(\mathbf{x};\theta_c)-f(\mathbf{x};\theta_C)]}}{e^{0} + \sum_{c'=1}^{C-1}e^{[f(\mathbf{x};\theta_{c'})-f(\mathbf{x};\theta_C)]}},\\
& f(\mathbf{x};\theta_{c}) \leftarrow f(\mathbf{x};\theta_{c})-f(\mathbf{x};\theta_C)\\
&=\begin{cases}
    \frac{e^{f(\mathbf{x};\theta_c)}}{1+\sum_{c'=1}^{C-1}e^{f(\mathbf{x};\theta_{c'})}}, & \text{if } c=1,2,\dots,C-1 \\
    \frac{1}{1+\sum_{c'=1}^{C-1}e^{f(\mathbf{x};\theta_{c'})}}, & \text{if } c=C
\end{cases} \\
\end{aligned}
$$

# Support vector machine (SVM)

## Linear SVM in linearly separable case (hard margin)

The distance $d_n$ from each data point $(\mathbf{x}_n, y_n), n=1,2,\dots,N$ to the hyperplane $\mathbf{w\cdot x}+b=0$ is as follows (we need to maximize these distances):

$$
\begin{aligned}
d_n&=\frac{|\mathbf{w} \cdot \mathbf{x}_n + b|}{||\mathbf{w}||}, \quad n=1,2,\dots,N\\
&=\frac{y_n(\mathbf{w} \cdot \mathbf{x}_n + b)}{||\mathbf{w}||}, \quad y_n \in \{-1, 1\}.
\end{aligned}
$$

Which is equivalent to:

$$
\begin{aligned}
&\min_{\mathbf{w}, b}\; \frac{1}{2}||\mathbf{w}||^2\\
& \text{s.t.}\; y_n(\mathbf{w} \cdot \mathbf{x}_n + b) \geq 1.
\end{aligned}
$$

Whose Lagrange form is:

$$
\begin{aligned}
&\max_\alpha\; \min_{\mathbf{w}, b}\; J(\mathbf{w}, b, \mathbf{\alpha})=\frac{1}{2}||\mathbf{w}||^2+\sum_{n=1}^{N}\alpha_n[1-y_n(\mathbf{w} \cdot \mathbf{x}_n+b)],\\
&\text{s.t.}\; \alpha_n\geq0, \;n=1,2,\dots,N.
\end{aligned}
$$

Solve $\min\limits_{w,b}$

$$
\begin{aligned}
&\nabla_{\mathbf{w}} J(\mathbf{w}, b, \alpha)&=\mathbf{w}-\sum_{n=1}^{N}\alpha_n y_n \mathbf{x}_n=0\\
&\nabla_b J(\mathbf{w}, b, \alpha)&=-\sum_{n=1}^{N}\alpha_n y_n=0
\end{aligned}
$$

Solve $\max\limits_{\alpha}$

$$
\begin{aligned}
&\max_\alpha\; -\frac{1}{2}\sum_{n=1}^{N}\sum_{n'=1}^{N}\alpha_n\alpha_{n'}y_ny_{n'}(\mathbf{x}_n\cdot \mathbf{x}_{n'})+\sum_{n=1}^{N}\alpha_n\\
&\text{s.t.}\; \sum_{n=1}^{N}\alpha_ny_n=0, \alpha_n\geq0,\; n=1,2,\dots,N.
\end{aligned}
$$

## Linear SVM (soft margin)

$$
\begin{aligned}
&\min_{\mathbf{w}, b}\; \frac{1}{2}||\mathbf{w}||^2+C\sum_{n=1}^{N}\xi_n\\
& \text{s.t.}\; y_n(\mathbf{w} \cdot \mathbf{x}_n + b)\geq1-\xi_n,\; \xi_n\geq0,\; n=1,2,\dots,N.
\end{aligned}
$$

Whose Lagrange form is:

$$
\begin{aligned}
&\max_{\alpha,\mu}\; \min_{\mathbf{w}, b, \xi}\; J(\mathbf{w}, b, \xi, \alpha, \mu)=\frac{1}{2}||\mathbf{w}||^2+\sum_{n=1}^{N}\alpha_n[1-\xi_n-y_n(\mathbf{w}\cdot \mathbf{x}_n+b)]+\sum_{n=1}^{N}\mu_n(-\xi_n),\\
&\text{s.t.}\; \alpha_n\geq0,\; \mu_n\geq0,\; n=1,2,\dots,N.
\end{aligned}
$$

Solve $\min_{w,b,\xi}$

$$
\begin{aligned}
&\nabla_{\mathbf{w}} J(\mathbf{w}, b, \xi, \alpha, \mu)&=\mathbf{w}-\sum_{n=1}^{N}\alpha_n y_n \mathbf{x}_n=0\\
&\nabla_b J(\mathbf{w}, b, \xi, \alpha, \mu)&=-\sum_{n=1}^{N}\alpha_n y_n=0\\
&\nabla_{\xi_n} J(\mathbf{w}, b, \xi, \alpha, \mu)&=C-\alpha_n-\mu_n=0
\end{aligned}
$$

Solve $\max_{\alpha}$

$$
\begin{aligned}
&\max_\alpha\; -\frac{1}{2}\sum_{n=1}^{N}\sum_{n'=1}^{N}\alpha_n\alpha_{n'}y_ny_{n'}(\mathbf{x}_n\cdot \mathbf{x}_{n'})+\sum_{n=1}^{N}\alpha_n\\
&\text{s.t.}\; \sum_{n=1}^{N}\alpha_ny_n=0,\; 0\leq \alpha_n\leq C,\; n=1,2,\dots,N.
\end{aligned}
$$

Another explanation (hinge loss with L2 regularization):

$$
\begin{aligned}
&\xi_n\geq{1-y_n(\mathbf{w}\cdot \mathbf{x}_n+b)}\\
&\lambda=\frac{1}{2C}\\
&L_{hinge+regL2}(\mathbf{w}, b, \lambda)=\sum_{n=1}^{N}[1-y_n(\mathbf{w}\cdot \mathbf{x}_n+b)]_{+}+\lambda||\mathbf{w}||^2.
\end{aligned}
$$

## Non-linear SVM (kernel tricks)

Replace the inner product $(x_n \cdot x_{n'})$ by a Kernel function $K(x_n,x_{n'})$

$$
\begin{aligned}
&\max_\alpha\; -\frac{1}{2}\sum_{n=1}^{N}\sum_{n'=1}^{N}\alpha_n\alpha_{n'}y_ny_{n'}K(\mathbf{x_n},\mathbf{x_{n'}})+\sum_{n=1}^{N}\alpha_n\\
&\text{s.t.}\; \sum_{n=1}^{N}\alpha_ny_n=0,\; 0\leq \alpha_n\leq C,\; n=1,2,\dots,N.
\end{aligned}
$$

Kernel examples:

$$
\begin{aligned}
&K(\mathbf{x_n}, \mathbf{x_{n'}}) = (\mathbf{x_n} \cdot \mathbf{x_{n'}} + 1)^p\; \text{(Polynomial)}\\
&K(\mathbf{x_n}, \mathbf{x_{n'}}) = \exp\left(-\frac{||\mathbf{x_n}-\mathbf{x_{n'}}||^2}{2\sigma^2}\right)\; \text{(Gaussian)}
\end{aligned}
$$

# Decision trees

The **entropy** at one node (the smaller, the purer):

$$
\begin{aligned}
&Ent(D)=-\sum_{c=1}^{C}p_clog_2p_c\;
\\ \text{where}\\
&D\text{ is the data points of the node.}\\
&C\text{ is the number of classes of }D\\
&p_c\text{ is the ratio of class c in }D
\end{aligned}
$$

The **information gain** after splitting by attribute $a$ (ID3):

$$
\begin{aligned}
&Gain(D,a)=Ent(D)-\sum_{v=1}^{V}\frac{|D^v|}{|D|}Ent(D^v)\;\\
\text{where}\\
&V\text{ is the number of unique values of attribute }a
\end{aligned}
$$

The **information gain ratio** after splitting by attribute $a$ (C4.5):

$$
\begin{aligned}
&Gain_{ratio}(D,a)=\frac{Gain(D,a)}{-\sum_{v=1}^{V}p_v log_2 p_v}\;\\
\text{where}\\
&p_v=\frac{|D^v|}{|D|}
\end{aligned}
$$

The **Gini** at one node (the smaller, the purer):

$$
\begin{aligned}
&Gini(D)=1-\sum_{c=1}^{C}p_c^2
\end{aligned}
$$

The **Gini index** after splitting by attribute $a$ (CART):

$$
\begin{aligned}
&Gini_{index}(D,a)=\sum_{v=1}^{V}\frac{|D^v|}{|D|}Gini(D^v)
\end{aligned}
$$

## ID3 (Iterative Dichotomiser 3)
- **Selection Criterion**: Information Gain
- **Features**: Handles only categorical features
- **Algorithm Steps**:
  1. Calculate entropy of dataset
  2. Split on attribute with highest information gain
  3. Repeat recursively until:
     - All samples belong to same class
     - No attributes remain
     - No samples remain

## C4.5 (Successor of ID3)
- **Selection Criterion**: Gain Ratio
- **Improvements over ID3**:
  1. Handles continuous attributes (using threshold)
  2. Handles missing values
  3. Supports attribute costs
  4. Post-pruning using error rates
- **Algorithm Steps**:
  1. Calculate gain ratio for each attribute
  2. Choose best split using gain ratio
  3. Create decision rules
  4. Prune tree using pessimistic error rates

## CART (Classification And Regression Trees)
- **Selection Criterion**: 
  - Classification: Gini index
  - Regression: MSE reduction
- **Key Features**:
  1. Binary splits only
  2. Handles both classification and regression
  3. Built-in handling of missing values
  4. Cost-complexity pruning
- **Algorithm Steps**:
  1. Find best binary split
  2. Grow maximum tree
  3. Prune using cost-complexity metric
  4. Select best sub-tree using cross-validation

## Comparison

| Feature | ID3 | C4.5 | CART |
|---------|-----|------|------|
| Split Criterion | Information Gain | Gain Ratio | Gini/MSE |
| Feature Types | Categorical | Both | Both |
| Split Type | Multi-way | Multi-way | Binary |
| Missing Values | No | Yes | Yes |
| Pruning | No | Yes | Yes |
| Output | Classification | Classification | Both |

# Boosting

## Adaboost for binary classification

$$
\begin{aligned}
f_M(\mathbf{x})=\sum_{m=1}^{M}\beta_mb_m(\mathbf{x}) \\
\text{where}\; b_m(\mathbf{x})\in\{-1,1\}
\end{aligned}
$$

Exponential loss:

$$
\begin{aligned}
L(\beta_m, b_m) &= \sum_{n=1}^{N}e^{(-y_nf_m(\mathbf{x}_n))},\; y\in\{-1,1\}\\
&=\sum_{n=1}^{N}e^{-y_n[f_{m-1}(\mathbf{x}_n)+\beta_mb_m(\mathbf{x}_n)]}\\
&=\sum_{n=1}^{N}w_{m-1,n}e^{-y_n\beta_mb_m(\mathbf{x}_n)},\; \text{where } w_{m-1,n}=e^{-y_nf_{m-1}(\mathbf{x}_n)}\\
&=\sum_{y_n=b_m(\mathbf{x}_n)}w_{m-1,n}e^{-\beta_m}+\sum_{y_n\neq b_m(\mathbf{x}_n)}w_{m-1,n}e^{\beta_m}\\
&=\sum_{y_n=b_m(\mathbf{x}_n) \cup y_n\neq b_m(\mathbf{x}_n)}w_{m-1,n}e^{-\beta_m}+
\sum_{y_n\neq b_m(\mathbf{x}_n)}w_{m-1,n}e^{\beta_m}-
\sum_{y_n\neq b_m(\mathbf{x}_n)}w_{m-1,n}e^{-\beta_m}\\
&=e^{-\beta_m}\sum_{n=1}^{N}w_{m-1,n}+(e^{\beta_m}-e^{-\beta_m})
\sum_{n=1}^{N}w_{m-1,n}\mathbf{1}_{\{y_n \neq b_m(\mathbf{x}_n)\}}\\
&\propto e^{-\beta_m}+(e^{\beta_m}-e^{-\beta_m})\epsilon_m,\;\\ 
\text{where }\\
& \epsilon_m = \frac{\sum_{n=1}^{N}w_{m-1,n}\mathbf{1}_{\{y_n \neq b_m(\mathbf{x}_n)\}}}{\sum_{n=1}^{N}w_{m-1,n}}=\sum_{n=1}^{N}\bar{w}_{m-1,n}\mathbf{1}_{\{y_n \neq b_m(\mathbf{x}_n)\}}
\end{aligned}
$$

Solution:

$$
\begin{aligned}
&\bar{w}_{0,n}=1/N,\; n=1,2,\dots,N\\
\text{For m=1, 2, ..., M:}\\
&\epsilon_m(b_m)=\sum_{n=1}^{N}\bar{w}_{m-1,n}\mathbf{1}_{\{y_n \neq b_m(\mathbf{x}_n)\}}\\
&b_m^* = \arg \min_{b_m}\epsilon_m(b_m)\\
&\epsilon_m^*=\epsilon_m(b_m^*)\\
&\nabla_{\beta_m}L(\beta_m, b_m^*)\propto-1+(e^{2\beta_m}+1)\epsilon_m^*=0\\
&\beta_m^* = \frac{1}{2}\log\frac{1-\epsilon_m^*}{\epsilon_m^*}\\
&\bar{w}_{m,n} =
\begin{cases}
    \frac{\bar{w}_{m-1,n}}{2(1-\epsilon_m^*)}, & \text{if } y_n=b_m^*(\mathbf{x}_n)\\
    \frac{\bar{w}_{m-1,n}}{2\epsilon_m^*}, & \text{if } y_n \neq b_m^*(\mathbf{x}_n)\\
\end{cases}
\end{aligned}
$$

Proof:

$$
\begin{aligned}
&\bar{w}_{m,n}=\frac{w_{m,n}}{\sum_{n=1}^{N}w_{m,n}},\\
&=\frac{e^{-y_nf_{m}(\mathbf{x}_n)}}{Z_{m}},\; \text{where } Z_{m}=\sum_{n=1}^{N}w_{m,n}\\
&=\frac{w_{m-1,n}e^{-y_n\beta_m^* b_m^*(\mathbf{x}_n)}}{Z_{m}}\\
&=\frac{w_{m-1,n}e^{\beta_m^*(2*\mathbf{1}_{\{y_n \neq b_m^*(\mathbf{x}_n)\}})-1)}}{Z_{m}}\\
&=\frac{\bar{w}_{m-1,n}\sum_{j=1}^{N}w_{m-1,j}e^{2\beta_m^*\mathbf{1}_{\{y_n \neq b_m^*(\mathbf{x}_n)\}}}e^{-\beta_m^*}}{Z_{m}}\\
&=\frac{\bar{w}_{m-1,n}e^{2\beta_m^*\mathbf{1}_{\{y_n \neq b_m^*(\mathbf{x}_n)\}}}C}{Z_{m}},\; \text{where } C=e^{-\beta_m^*}\sum_{j=1}^{N}w_{m-1,j}\\
&=\frac{\bar{w}_{m-1,n}e^{2\beta_m^*\mathbf{1}_{\{y_n \neq b_m^*(\mathbf{x}_n)\}}}}{\sum_{n'=1}^{N}\bar{w}_{m-1,n'}e^{2\beta_m^*\mathbf{1}_{\{y_{n'} \neq b_m^*(\mathbf{x}_{n'})\}}}},\\
&=\frac{\bar{w}_{m-1,n} e^{2\beta_m^*\mathbf{1}_{\{y_n \neq b_m^*(\mathbf{x}_n)\}}}}{\sum_{y_n \neq b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}e^{2\beta_m^*}+
\sum_{y_n = b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}
}, \\
&\text{making use of }\\
    &\qquad e^{2\beta_m^*} =e^{2\frac{1}{2}log\frac{1-\epsilon_m^*}{\epsilon_m^*}}=\frac{1-\epsilon_m^*}{\epsilon_m^*}\\
    &\qquad {\epsilon_m^*}={\sum_{y_n \neq b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}}\\
    &\qquad 1 = {\sum_{n}\bar{w}_{m-1,n}} = {\sum_{y_n \neq b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}} + {\sum_{y_n = b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}} \\
    &\qquad {\sum_{y_n = b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}} = 1-{\sum_{y_n \neq b_m^*(\mathbf{x}_n)}\bar{w}_{m-1,n}}=1-{\epsilon_m^*}\\
&=\frac{\bar{w}_{m-1,n}(\frac{1-\epsilon_m^*}{\epsilon_m^*})^{\mathbf{1}_{\{y_n \neq b_m^*(\mathbf{x}_n)\}}}}{\epsilon_m^*\frac{1-\epsilon_m^*}{\epsilon_m^*}+(1-\epsilon_m^*)
},\\
&=
\begin{cases}
    \frac{\bar{w}_{m-1,n}}{2(1-\epsilon_m^*)}, & \text{if } y_n=b_m^*(\mathbf{x}_n)\\
    \frac{\bar{w}_{m-1,n}}{2\epsilon_m^*}, & \text{if } y_n \neq b_m^*(\mathbf{x}_n)
\end{cases}
\end{aligned}
$$

## Gradient boosting for regression (simple algorithm)

$$
\begin{aligned}
f_M(\mathbf{x})=\sum_{m=1}^{M}b_m(\mathbf{x}) \\
\text{where } b_m(\mathbf{x})\text{ is a regressor.}
\end{aligned}
$$

Square loss:

$$
\begin{aligned}
L(b_m) &= \sum_{n=1}^{N}[y_n-f_m(\mathbf{x}_n)]^2\\
&=\sum_{n=1}^{N}[y_n-f_{m-1}(\mathbf{x}_n)-b_m(\mathbf{x}_n)]^2\\
&=\sum_{n=1}^{N}[r_{m,n}-b_m(\mathbf{x}_n)]^2,\; \text{where } r_{m,n}=y_n-f_{m-1}(\mathbf{x}_n)
\end{aligned}
$$

Solution:

$$
\begin{aligned}
&\text{For m=1:}\\
&\quad f_1(\mathbf{x})=\bar{y} \quad \text{(initialize with mean target value)}\\
&\text{For m=2, 3, ..., M:}\\
&\quad r_{m,n}=y_n-f_{m-1}(\mathbf{x}_n)\\
&\quad \text{fit a regression tree } b_m \text{ to } r_{m,n}
\end{aligned}
$$

## XGBoost for regression

Reference

- [XGBoost: A scalable tree boosting system](https://www.kdd.org/kdd2016/papers/files/rfp0697-chenAemb.pdf)

$$
\begin{aligned}
f_M(\mathbf{x})=\sum_{m=1}^{M}b_m(\mathbf{x}) \\
\text{where } b_m(\mathbf{x})\text{ is a regression tree.}
\end{aligned}
$$

General loss:

$$
\begin{aligned}
L(b_m) &= \sum_{n=1}^{N}l(y_n,f_{m-1}(\mathbf{x}_n)+b_m(\mathbf{x}_n))+\Omega(b_m),\\
\text{where}\\
&\Omega(b_m)=\gamma T_m+\frac{1}{2}\lambda||\mathbf{v_m}||^2\\
&T_m\text{ is the number of leaf nodes of tree }b_m,\\
&\mathbf{v_m}\text{ are the values of leaf nodes of tree }b_m.
\end{aligned}
$$

Make use of Taylor's theorem: 
$$
\begin{aligned}
\qquad f(x) &\approx f(a) + f'(a)(x-a) + \frac{f''(a)}{2}(x-a)^2
\end{aligned}
$$

$$
\begin{aligned}
L(b_m) &\approx \sum_{n=1}^{N}[l(y_n,f_{m-1}(\mathbf{x}_n)+g_{m-1, n}b_m(\mathbf{x}_n)+\frac{1}{2}h_{m-1, n}b_m^2(\mathbf{x}_n)]+\Omega(b_m),\\
&\text{where } g_{m-1, n}=\nabla_{f_{m-1}}l(y_n, f_{m-1})，h_{m-1, n}=\nabla^2_{f_{m-1}}l(y_n, f_{m-1})\\
&= \sum_{n=1}^{N}[g_{m-1, n}b_m(\mathbf{x}_n)+\frac{1}{2}h_{m-1, n}b_m^2(\mathbf{x}_n)]+\gamma T_m+\frac{1}{2}\lambda||\mathbf{v_m}||^2+constant,\;\\
&\text{where } constant=\sum_{n=1}^{N}l(y_n,f_{m-1}(\mathbf{x}_n))\text{ is irrelevant to }b_m\text{, and can be dropped.}\\
&\approx \sum_{t=1}^{T_m}\left[v_{m,t}\sum_{n\in R_t}g_{m-1, n}+\frac{1}{2}v_{m,t}^2\sum_{n\in R_t}h_{m-1, n}\right]+\gamma T_m+\frac{1}{2}\lambda\sum_{t=1}^{T_m}v_{m,t}^2,\\
&\text{where } R_t \text{ are those data points fall into the leaf node t}.\\
&= \sum_{t=1}^{T_m}\left[v_{m,t}\sum_{n\in R_t}g_{m-1, n}+\frac{1}{2}v_{m,t}^2(\sum_{n\in R_t}h_{m-1, n}+\lambda)\right]+\gamma T_m.
\end{aligned}
$$

Solution:

$$
\begin{aligned}
&\nabla_{v_{m,t}} L(b_m) = \sum_{n\in R_t}g_{m-1, n}+v_{m,t}(\sum_{n\in R_t}h_{m-1, n}+\lambda)=0\\
&v_{m,t}^*=-\frac{\sum_{n\in R_t}g_{m-1, n}}{\sum_{n\in R_t}h_{m-1, n}+\lambda}\\
&L^*(b_m)=\sum_{t=1}^{T_m}\frac{-(\sum_{n\in R_t}g_{m-1, n})^2}{2(\sum_{n\in R_t}h_{m-1, n}+\lambda)}+\gamma T_m.
\end{aligned}
$$

Loss reduction after each split ($R=R_L\bigcup R_R$, only binary split):

$$
\begin{aligned}
&L_{split}=\frac{1}{2}\left[\frac{(\sum_{n\in R_L}g_{m-1, n})^2}{(\sum_{n\in R_L}h_{m-1, n}+\lambda)}+\frac{(\sum_{n\in R_R}g_{m-1, n})^2}{(\sum_{n\in R_R}h_{m-1, n}+\lambda)}-\frac{(\sum_{n\in R}g_{m-1, n})^2}{(\sum_{n\in R}h_{m-1, n}+\lambda)}\right]-\gamma.
\end{aligned}
$$

As long as the loss reduction $L_{split}$ is above some threshold, the split will be conducted.

# Naive Bayes for classification

Reference:

- [Chapter 3, Machine Learning, Tom M. Mithell](http://www.cs.cmu.edu/~tom/mlbook/NBayesLogReg.pdf)

## Train

### `P(Y)`

$$
\begin{aligned}
P(Y=c)&=\frac{\sum_{n=1}^{N}\mathbf{1}_{\{y_n=c\}}}{N},\;c=1,2,\dots,C\\
\text{where}\\
&C\text{ is the number of classes.}\\
&N\text{ is the number of data points for training.}
\end{aligned}
$$

### `P(X|Y)` for discrete X

$$
\begin{aligned}
P(X^{(j)} = \mathbb{X}^{(jk)} | Y=c) &= \frac{\sum_{n=1}^{N} \mathbf{1}_{\{x_n^{(j)} = \mathbb{X}^{(jk)}, y_n = c\}}}{\sum_{n=1}^{N} \mathbf{1}_{\{y_n = c\}}}, \\
&j=1,2,\dots,J_d, \\
&k=1,2,\dots,K_j \\
\text{where} \\
&J_d \text{ is the number of discrete attributes}, \\
&K_j \text{ is the number of unique values of attribute } x^{(j)}, \\
&\mathbb{X}^j \text{ is the value set of attribute } x^{(j)}.
\end{aligned}
$$

#### Avoid zero value of probability

$$
\begin{aligned}
P_{\lambda}(X^{(j)}=\mathbb{X}^{(jk)}|Y=c) &= \frac{\sum_{n=1}^{N} \mathbf{1}_{\{x_n^{(j)}=\mathbb{X}^{(jk)}, y_n=c\}} + \lambda}{\sum_{n=1}^{N} \mathbf{1}_{\{y_n=c\}} + K_j \lambda}, \quad \lambda > 0
\end{aligned}
$$

### `P(X|Y)` for continuous X

$$
\begin{aligned}
P(X^{(j)}=\mathbf{x}^{(j)}|Y=c) &= {\mathcal {N}}(\mathbf{x}^{(j)}; \mu_{jc}, \sigma_{jc}^2), \\
&j=1,2,\dots,J_c, \\
\text{where} \\
&J_c \text{ is the number of continuous attributes}, \\
&\mu_{jc} = \frac{\sum_{n=1}^{N} \mathbf{1}_{\{y_n=c\}} \mathbf{x}_n^{(j)}}{\sum_{n=1}^{N} \mathbf{1}_{\{y_n=c\}}}, \\
&\sigma_{jc}^2 = \frac{\sum_{n=1}^{N} \mathbf{1}_{\{y_n=c\}} (\mathbf{x}_n^{(j)} - \mu_{jc})^2}{\sum_{n=1}^{N} \mathbf{1}_{\{y_n=c\}}}.
\end{aligned}
$$

## Test

$$
\begin{aligned}
y=arg \max_{c}P(Y=c)\prod_{j=1}^{J_d}\prod_{k=1}^{K_j}P(X^{(j)}=\mathbb{X}^{(jk)}|Y=c)\prod_{j=1}^{J_c}P(X^{(j)}=\mathbf{x}^{(j)}|Y=c)
\end{aligned}
$$

# EM algorithm

Q function

$$
\begin{aligned}
Q(\theta^{(t+1)},\theta^{(t)})&=E_{z\sim P(Z|X,\theta^{(t)})}[logP(X,Z|\theta^{(t+1)})],\\
\text{where}\\
&\theta^{(t+1)}\text{ is the model parameters to be optimized.}\\
&\theta^{(t)}\text{ is the model parameters of the previous time step.}\\
&X\text{ is visible variable.}\\
&Z\text{ is latent variable.}\\
\end{aligned}
$$

Derive Q function from log likelihood:

$$
\begin{aligned}
L(\theta^{(t+1)})&=logP(X|\theta^{(t+1)})\\
&=log\sum_ZP(X,Z|\theta^{(t+1)})\\
&=log\sum_ZP(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})\\
\end{aligned}
$$

$$
\begin{aligned}
L(\theta^{(t+1)})-L(\theta^{(t)})&=log\sum_ZP(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})-log(X|\theta^{(t)})\\
&=log\sum_ZP(Z|X,\theta^{(t)})\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})}-log(X|\theta^{(t)})\\
&\text{The convex property of log leads to the following inequality:}\\
&\geq\sum_ZP(Z|X,\theta^{(t)})log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})}-log(X|\theta^{(t)})\\
&\text{Make use of }1=\sum_ZP(Z|X,\theta^{(t)})\\
&=\sum_ZP(Z|X,\theta^{(t)})log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})}-\\
&\;\;\;\;\;log(P(X|\theta^{(t)}))\sum_ZP(Z|X,\theta^{(t)})\\
&=\sum_ZP(Z|X,\theta^{(t)})log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})}-\\
&\;\;\;\:\sum_ZP(Z|X,\theta^{(t)})log(P(X|\theta^{(t)}))\\
&=\sum_ZP(Z|X,\theta^{(t)})\left[log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})})-log(P(X|\theta^{(t)})\right]\\
&=\sum_ZP(Z|X,\theta^{(t)})log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})P(X|\theta^{(t)})}\\
\end{aligned}
$$

We define:

$$
\begin{aligned}
B(\theta^{(t+1)},\theta^{(t)})&=L(\theta^{(t)})+\sum_ZP(Z|X,\theta^{(t)})log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})P(X|\theta^{(t)})}\\
\end{aligned}
$$

It can be seen that:

$$
\begin{aligned}
    L(\theta^{(t+1)})\geq B(\theta^{(t+1)},\theta^{(t)})
\end{aligned}
$$

Maximizing $L(\theta^{(t+1)})$ is equivalent as maximizing $B(\theta^{(t+1)},\theta^{(t)})$.

Solution:

$$
\begin{aligned}
\theta^{(t+1)*}&=arg \max_{\theta^{(t+1)}}B(\theta^{(t+1)},\theta^{(t)})\\
&=arg \max_{\theta^{(t+1)}}\left(L(\theta^{(t)})+\sum_ZP(Z|X,\theta^{(t)})log\frac{P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})}{P(Z|X,\theta^{(t)})P(X|\theta^{(t)})}\right)\\
&\text{drop those terms which are un-related to } \theta^{(t+1)}\\
&=arg \max_{\theta^{(t+1)}}\sum_ZP(Z|X,\theta^{(t)})log\left[P(X|Z,\theta^{(t+1)})P(Z|\theta^{(t+1)})\right]\\
&=arg \max_{\theta^{(t+1)}}\sum_ZP(Z|X,\theta^{(t)})logP(X,Z|\theta^{(t+1)})\\
&=arg \max_{\theta^{(t+1)}}Q(\theta^{(t+1)},\theta^{(t)})
\end{aligned}
$$

## Gaussian Mixture Model (GMM) using EM

$$
\begin{aligned}
P(\mathbf{x}|\theta)&=\sum_{k=1}^{K}\alpha_k\phi(\mathbf{x}|\mathbf{\mu}_k, \mathbf{\sigma}_k)\\
&\text{s.t.}\;\sum_{k=1}^{K}\alpha_k=1\\
\text{where}\\
&K\text{ is the number of Gaussian mixtures.}\\
&\phi(\mathbf{x}|\mathbf{\mu}_k, \mathbf{\sigma}_k)\text{ is the kth Gaussian mixture.}\\
&\alpha_k\text{ is the coefficient of the kth Gaussian mixture.}\\
&\theta=[\alpha,\mathbf{\mu},\mathbf{\sigma}]\text{ is the collection of all model parameters.}\\
\end{aligned}
$$

Latent variable

$$
\begin{aligned}
Z_{nk}=
\begin{cases}
    1, & \text{if the nth data point comes from the kth Gaussian mixture}\\
    0, & \text{otherwise}
\end{cases}
\end{aligned}
$$

Conditional distribution of $Z_{nk}$

$$
\begin{aligned}
P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})&=P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})\\
&=\frac{\alpha_k^{(t)}\phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t)}, \mathbf{\sigma}_k^{(t)})}{\sum_{l=1}^{K}\alpha_l\phi(\mathbf{x}_n|\mathbf{\mu}_l^{(t)}, \mathbf{\sigma}_l^{(t)})}
\end{aligned}
$$

Log likelihood

$$
\begin{aligned}
\log P(X, Z|\theta^{(t+1)}) &= \log \prod_{n=1}^{N} P(\mathbf{x}_n, Z_n|\theta^{(t+1)}) \\
&= \log \prod_{n=1}^{N} \prod_{k=1}^{K} \left[ \alpha_k^{(t+1)} \phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t+1)}, \mathbf{\sigma}_k^{(t+1)}) \right]^{Z_{nk}} \\
&= \sum_{n=1}^{N} \sum_{k=1}^{K} Z_{nk} \log \left[ \alpha_k^{(t+1)} \phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t+1)}, \mathbf{\sigma}_k^{(t+1)}) \right] \\
&= \sum_{k=1}^{K} \sum_{n=1}^{N} Z_{nk} \left[ \log \alpha_k^{(t+1)} + \log \phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t+1)}, \mathbf{\sigma}_k^{(t+1)}) \right] \\
\end{aligned}
$$

Q function

$$
\begin{aligned}
Q(\theta^{(t+1)},\theta^{(t)})&=E_{Z\sim P(Z_{nk}|\mathbf{x}_n,\theta^{(t)})}log P(X, Z|\theta^{(t+1)})\\
&=P(Z_{nk}=0|\mathbf{x}_n,\theta^{(t)})log P(X, Z|\theta^{(t+1)})+\\
&\;\;\;\;P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})log P(X, Z|\theta^{(t+1)})\\
&=P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})log P(X, Z|\theta^{(t+1)})\\
&=\sum_{k=1}^{K}\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})\{log \alpha_k^{(t+1)}+log[\phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t+1)}, \mathbf{\sigma}_k^{(t+1)})]\}\\
&\text{s.t.}\;\sum_{k=1}^{K}a_k^{(t+1)}=1
\end{aligned}
$$

Whose Lagrange form is:

$$
\begin{aligned}
Q_{\lambda}(\theta^{(t+1)},\theta^{(t)})&=\sum_{k=1}^{K}\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})\{log \alpha_k^{(t+1)}+log[\phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t+1)}, \mathbf{\sigma}_k^{(t+1)})]\}\\
&\;\;\;\;+\lambda(\sum_{k=1}^{K}a_k^{(t+1)}-1)
\end{aligned}
$$

Solution

$$
\begin{aligned}
&\nabla_{\alpha_k^{(t+1)}}Q_{\lambda}(\theta^{(t+1)},\theta^{(t)})=\frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}{\alpha_k^{(t+1)}}+\lambda=0
\end{aligned}
$$

Make use of $\sum_{k=1}^{K}a_k^{(t+1)}=1$, we get:

$$
\begin{aligned}
\lambda=-\sum_{k=1}^{K}\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})
\end{aligned}
$$

Therefore:

$$
\begin{aligned}
\alpha_k^{(t+1)}&=\frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}{-\lambda}\\
&=\frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}{\sum_{k=1}^{K}\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}\\
&=\frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}{\sum_{n=1}^{N}\sum_{k=1}^{K}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}\\
&=\frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}{\sum_{n=1}^{N}1}\\
&=\frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\alpha^{(t)},\mathbf{\mu}^{(t)},\mathbf{\sigma}^{(t)})}{N}
\end{aligned}
$$

Solution for $\mu_k^{(t+1)}$ and $(\sigma_k^{(t+1)})^2$:
1. **Expand Gaussian term**:
  $$
  \begin{aligned}
  \phi(\mathbf{x}_n|\theta_k)=\phi(\mathbf{x}_n|\mathbf{\mu}_k, \mathbf{\sigma}_k) = \frac{1}{\sqrt{2\pi}\mathbf{\sigma}_k}\exp\left(-\frac{(\mathbf{x}_n-\mathbf{\mu}_k)^2}{2\mathbf{\sigma}_k^2}\right)
  \end{aligned}
  $$

2. **Taking the logarithm of the Gaussian term, we get**:

\[
\log \phi(\mathbf{x}_n|\mathbf{\mu}_k^{(t+1)}, \mathbf{\sigma}_k^{(t+1)}) = -\frac{1}{2} \log(2\pi (\sigma_k^{(t+1)})^2) - \frac{(\mathbf{x}_n - \mu_k^{(t+1)})^2}{2 (\sigma_k^{(t+1)})^2}
\]


2. **Take derivative of Q with respect to $\mu_k^{(t+1)}$**:
  $$
  \begin{aligned}
  &\frac{\partial}{\partial \mu_k^{(t+1)}} Q_{\lambda} = \sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})\frac{\partial}{\partial \mu_k^{(t+1)}}[-\frac{(\mathbf{x}_n-\mu_k^{(t+1)})^2}{2(\sigma_k^{(t+1)})^2}]\\
  &= \sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})\frac{(\mathbf{x}_n-\mu_k^{(t+1)})}{(\sigma_k^{(t+1)})^2} = 0
  \end{aligned}
  $$

3. **Solve for $\mu_k^{(t+1)}$**:
  $$
  \begin{aligned}
  \mu_k^{(t+1)} &= \frac{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})\mathbf{x}_n}{\sum_{n=1}^{N}P(Z_{nk}=1|\mathbf{x}_n,\theta^{(t)})}
  \end{aligned}
  $$

4. **Take derivative of Q with respect to $(\sigma_k^{(t+1)})^2$**:
$$
\begin{aligned}
&\frac{\partial}{\partial (\sigma_k^{(t+1)})^2} Q(\theta^{(t+1)}, \theta^{(t)}) \\
&= \sum_{n=1}^{N} P(Z_{nk} = 1|\mathbf{x}_n, \theta^{(t)}) \frac{\partial}{\partial (\sigma_k^{(t+1)})^2} \left[ -\frac{1}{2} \log(2\pi (\sigma_k^{(t+1)})^2) - \frac{(\mathbf{x}_n - \mu_k^{(t+1)})^2}{2 (\sigma_k^{(t+1)})^2} \right] \\
&= \sum_{n=1}^{N} P(Z_{nk} = 1|\mathbf{x}_n, \theta^{(t)}) \left[ -\frac{1}{2 (\sigma_k^{(t+1)})^2} + \frac{(\mathbf{x}_n - \mu_k^{(t+1)})^2}{2 (\sigma_k^{(t+1)})^4} \right] = 0 \\
&= \sum_{n=1}^{N} P(Z_{nk} = 1|\mathbf{x}_n, \theta^{(t)}) \frac{-(\sigma_k^{(t+1)})^2 + (\mathbf{x}_n - \mu_k^{(t+1)})^2}{2 (\sigma_k^{(t+1)})^4} = 0 \\
&\implies \sum_{n=1}^{N} P(Z_{nk} = 1|\mathbf{x}_n, \theta^{(t)}) \left[ -(\sigma_k^{(t+1)})^2 + (\mathbf{x}_n - \mu_k^{(t+1)})^2 \right] = 0 \\
&\implies (\sigma_k^{(t+1)})^2 = \frac{\sum_{n=1}^{N} P(Z_{nk} = 1|\mathbf{x}_n, \theta^{(t)}) (\mathbf{x}_n - \mu_k^{(t+1)})^2}{\sum_{n=1}^{N} P(Z_{nk} = 1|\mathbf{x}_n, \theta^{(t)})}.
\end{aligned}
$$


# Variance-bias tradeoff

**Reference:**

- [Cornell lectures](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/)
- [Bias-Variance Tradeoff Explained](https://blog.insightdatascience.com/bias-variance-tradeoff-explained-fa2bc28174c4)

Decomposition of Expected Test Error

$$
\begin{aligned}
E_{\mathbf{x}\sim X,D\sim \mathbb{D}}&\left[\left[h_{D}(\mathbf{x}) - (f(\mathbf{x})+\epsilon)\right]^{2}\right] \\
&= E_{\mathbf{x}\sim X,D\sim \mathbb{D}}\left[\left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right) + \left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon)\right)\right]^{2}\right] \\
&= E_{\mathbf{x}\sim X,D\sim \mathbb{D}}\left[(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x}))^{2}\right] \\
&\quad + E_{\mathbf{x}\sim X} \left[\left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon)\right)^{2}\right] \\
&\quad + 2 E_{\mathbf{x}\sim X,D\sim \mathbb{D}} \left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right)\left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon)\right)\right] \\
\text{where} \\
&X\text{ is a set of input features for testing.}\\
&\mathbb{D}\text{ is a collection of datasets for training.}\\
&\mathbf{x}\text{ is an input feature sampled from }X\\
&D\text{ is a training data set sampled from }\mathbb{D}\\
&h_{D}(\mathbf{x})\text{ is a model trained on }D\\
&\bar{h}(\mathbf{x})=E_{D\sim \mathbb{D}}\left[h_{D}(\mathbf{x})\right]\\
&f(\mathbf{x})\text{ is the true function to be estimated.}\\
&\epsilon \sim \text{Noise}(\mu=0, \sigma^2)\text{ is a noise of zero mean and variance }\sigma^2.
\end{aligned}
$$

The covariance term (third term) of the above equation is $0$ as we show below, which leads to the bias-variance decomposition

$$
\begin{aligned}
E_{\mathbf{x}\sim X,D\sim \mathbb{D}}& \left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right) \left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon)\right)\right] \\
&= E_{\mathbf{x}\sim X} \left[E_{D\sim \mathbb{D}} \left[ h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right] \left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon)\right) \right] \\
&= E_{\mathbf{x}\sim X} \left[ \left( E_{D\sim \mathbb{D}} \left[ h_{D}(\mathbf{x}) \right] - \bar{h}(\mathbf{x}) \right) \left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon) \right)\right] \\
&= E_{\mathbf{x}\sim X} \left[ \left(\bar{h}(\mathbf{x}) - \bar{h}(\mathbf{x}) \right) \left(\bar{h}(\mathbf{x}) - (f(\mathbf{x})+\epsilon) \right)\right] \\
&= E_{\mathbf{x}\sim X} \left[ 0 \right] \\
&= 0
\end{aligned}
$$

Returning to the earlier expression, we're left with the variance and another term

$$
\begin{aligned}
E_{\mathbf{x}\sim X,D\sim \mathbb{D}} &\left[ \left( h_{D}(\mathbf{x}) - (f(\mathbf{x})+\epsilon) \right)^{2} \right] \\
&= \underbrace{E_{\mathbf{x}\sim X,D\sim \mathbb{D}} \left[ \left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x}) \right)^{2} \right]}_\mathrm{Variance} \\
&\quad + \underbrace{E_{\mathbf{x}\sim X}\left[ \left( \bar{h}(\mathbf{x}) - f(\mathbf{x}) \right)^{2} \right]}_\mathrm{Bias^2} \\
&\quad + \underbrace{\sigma^{2}}_\mathrm{Noise}
\end{aligned}
$$

<b>Variance</b>:
Captures how much your classifier changes if you train on a different training set. How "over-specialized" is your classifier to a particular training set (overfitting)? If we have the best possible model for our training data, how far off are we from the average classifier?
<br><br/>
<b>Bias</b>:
What is the inherent error that you obtain from your classifier even with infinite training data? This is due to your classifier being "biased" to a particular kind of solution (e.g. linear classifier). In other words, bias is inherent to your model.
<br/><br/>
<b>Noise</b>:
How big is the data-intrinsic noise? This error measures ambiguity due to your data distribution and feature representation. You can never beat this, it is an aspect of the data.
<br><br/>

<blockquote>
    <center>
    <img src="http://scott.fortmann-roe.com/docs/docs/BiasVariance/biasvariance.png" />
	<p>Fig 2: The variation of Bias and Variance with the model complexity. This is similar to the concept of overfitting and underfitting. More complex models overfit while the simplest models underfit.</p>
    </center>
</blockquote>

