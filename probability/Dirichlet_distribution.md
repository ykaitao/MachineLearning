The **Dirichlet distribution** is a multivariate generalization of the **Beta distribution**. It is a continuous probability distribution defined over the **simplex**, meaning it models random vectors whose components are non-negative and sum to 1. The Dirichlet distribution is often used in Bayesian statistics, particularly in the context of **categorical distributions** and **topic modeling**. Let’s derive the **probability density function (PDF)** of the Dirichlet distribution step by step.

---

### **1. Background**
The Dirichlet distribution is characterized by a vector of parameters:
- **Concentration parameters (\( \alpha_1, \alpha_2, \dots, \alpha_K \))**: These control the shape of the distribution. Each \( \alpha_i > 0 \).

The PDF of the Dirichlet distribution is:
\[
f(\mathbf{x}) = \frac{1}{B(\boldsymbol{\alpha})} \prod_{i=1}^K x_i^{\alpha_i - 1},
\]
where:
- \( \mathbf{x} = (x_1, x_2, \dots, x_K) \): A random vector on the simplex (i.e., \( x_i \geq 0 \) and \( \sum_{i=1}^K x_i = 1 \)),
- \( B(\boldsymbol{\alpha}) \): The **multivariate Beta function**, which serves as a normalization constant.

---

### **2. Derivation of the PDF**
The Dirichlet distribution can be derived as the distribution of the ratios of independent gamma-distributed random variables. Here’s how:

#### **Step 1: Gamma Distribution**
The gamma distribution with shape parameter \( \alpha_i \) and scale parameter \( \theta = 1 \) has the PDF:
\[
f_{Y_i}(y_i) = \frac{y_i^{\alpha_i - 1} e^{-y_i}}{\Gamma(\alpha_i)}, \quad y_i > 0.
\]

#### **Step 2: Sum of Gamma Random Variables**
Let \( Y_1, Y_2, \dots, Y_K \) be \( K \) independent gamma-distributed random variables with shape parameters \( \alpha_1, \alpha_2, \dots, \alpha_K \), respectively, and scale parameter \( \theta = 1 \). Define:
\[
S = Y_1 + Y_2 + \dots + Y_K.
\]
The sum \( S \) follows a gamma distribution with shape parameter \( \alpha_0 = \sum_{i=1}^K \alpha_i \) and scale parameter \( \theta = 1 \):
\[
f_S(s) = \frac{s^{\alpha_0 - 1} e^{-s}}{\Gamma(\alpha_0)}, \quad s > 0.
\]

#### **Step 3: Ratios of Gamma Random Variables**
Define the random vector \( \mathbf{X} = (X_1, X_2, \dots, X_K) \) as:
\[
X_i = \frac{Y_i}{S}, \quad i = 1, 2, \dots, K.
\]
The components of \( \mathbf{X} \) satisfy \( x_i \geq 0 \) and \( \sum_{i=1}^K x_i = 1 \), meaning \( \mathbf{X} \) lies on the simplex.

#### **Step 4: Joint PDF of \( Y_1, Y_2, \dots, Y_K \)**
Since \( Y_1, Y_2, \dots, Y_K \) are independent, their joint PDF is the product of their individual PDFs:
\[
f_{Y_1, Y_2, \dots, Y_K}(y_1, y_2, \dots, y_K) = \prod_{i=1}^K \frac{y_i^{\alpha_i - 1} e^{-y_i}}{\Gamma(\alpha_i)}.
\]

#### **Step 5: Transform to \( \mathbf{X} \) and \( S \)**
Define the transformation:
\[
X_i = \frac{Y_i}{S}, \quad i = 1, 2, \dots, K, \quad S = Y_1 + Y_2 + \dots + Y_K.
\]
The inverse transformation is:
\[
Y_i = X_i S, \quad i = 1, 2, \dots, K.
\]

The Jacobian determinant of this transformation is:
\[
J = \begin{vmatrix}
\frac{\partial y_1}{\partial x_1} & \frac{\partial y_1}{\partial x_2} & \cdots & \frac{\partial y_1}{\partial x_K} & \frac{\partial y_1}{\partial s} \\
\frac{\partial y_2}{\partial x_1} & \frac{\partial y_2}{\partial x_2} & \cdots & \frac{\partial y_2}{\partial x_K} & \frac{\partial y_2}{\partial s} \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
\frac{\partial y_K}{\partial x_1} & \frac{\partial y_K}{\partial x_2} & \cdots & \frac{\partial y_K}{\partial x_K} & \frac{\partial y_K}{\partial s} \\
\frac{\partial s}{\partial x_1} & \frac{\partial s}{\partial x_2} & \cdots & \frac{\partial s}{\partial x_K} & \frac{\partial s}{\partial s}
\end{vmatrix}.
\]
The Jacobian simplifies to:
\[
J = s^{K-1}.
\]

#### **Step 6: Joint PDF of \( \mathbf{X} \) and \( S \)**
Using the transformation rule for PDFs, the joint PDF of \( \mathbf{X} \) and \( S \) is:
\[
f_{\mathbf{X}, S}(\mathbf{x}, s) = f_{Y_1, Y_2, \dots, Y_K}(y_1, y_2, \dots, y_K) \cdot |J|.
\]
Substitute \( y_i = x_i s \) and \( |J| = s^{K-1} \):
\[
f_{\mathbf{X}, S}(\mathbf{x}, s) = \prod_{i=1}^K \frac{(x_i s)^{\alpha_i - 1} e^{-x_i s}}{\Gamma(\alpha_i)} \cdot s^{K-1}.
\]
Simplify the expression:
\[
f_{\mathbf{X}, S}(\mathbf{x}, s) = \left( \prod_{i=1}^K \frac{x_i^{\alpha_i - 1}}{\Gamma(\alpha_i)} \right) s^{\alpha_0 - 1} e^{-s}.
\]

#### **Step 7: Marginal PDF of \( \mathbf{X} \)**
To find the marginal PDF of \( \mathbf{X} \), integrate the joint PDF \( f_{\mathbf{X}, S}(\mathbf{x}, s) \) over all possible values of \( S \):
\[
f_{\mathbf{X}}(\mathbf{x}) = \int_0^\infty f_{\mathbf{X}, S}(\mathbf{x}, s) \, ds.
\]
Substitute \( f_{\mathbf{X}, S}(\mathbf{x}, s) \):
\[
f_{\mathbf{X}}(\mathbf{x}) = \left( \prod_{i=1}^K \frac{x_i^{\alpha_i - 1}}{\Gamma(\alpha_i)} \right) \int_0^\infty s^{\alpha_0 - 1} e^{-s} \, ds.
\]

#### **Step 8: Evaluate the Integral**
The integral is a gamma function integral:
\[
\int_0^\infty s^{\alpha_0 - 1} e^{-s} \, ds = \Gamma(\alpha_0).
\]

#### **Step 9: Simplify the PDF**
Substitute the integral result back into \( f_{\mathbf{X}}(\mathbf{x}) \):
\[
f_{\mathbf{X}}(\mathbf{x}) = \left( \prod_{i=1}^K \frac{x_i^{\alpha_i - 1}}{\Gamma(\alpha_i)} \right) \Gamma(\alpha_0).
\]
Simplify the expression:
\[
f_{\mathbf{X}}(\mathbf{x}) = \frac{\Gamma(\alpha_0)}{\prod_{i=1}^K \Gamma(\alpha_i)} \prod_{i=1}^K x_i^{\alpha_i - 1}.
\]

#### **Step 10: Multivariate Beta Function**
The **multivariate Beta function** \( B(\boldsymbol{\alpha}) \) is defined as:
\[
B(\boldsymbol{\alpha}) = \frac{\prod_{i=1}^K \Gamma(\alpha_i)}{\Gamma(\alpha_0)}.
\]
Thus, the PDF of the Dirichlet distribution is:
\[
f_{\mathbf{X}}(\mathbf{x}) = \frac{1}{B(\boldsymbol{\alpha})} \prod_{i=1}^K x_i^{\alpha_i - 1}.
\]

---

### **3. Dirichlet PDF Formula**
The PDF of the Dirichlet distribution with concentration parameters \( \alpha_1, \alpha_2, \dots, \alpha_K \) is:
\[
f(\mathbf{x}) = \frac{1}{B(\boldsymbol{\alpha})} \prod_{i=1}^K x_i^{\alpha_i - 1}, \quad \mathbf{x} \in \text{simplex},
\]
where:
- \( \mathbf{x} = (x_1, x_2, \dots, x_K) \): A random vector on the simplex,
- \( B(\boldsymbol{\alpha}) \): The multivariate Beta function.

---

### **4. Summary**
The PDF of the Dirichlet distribution is derived by:
1. Starting with the ratios of independent gamma-distributed random variables.
2. Using transformation and integration to find the marginal PDF.
3. Introducing the multivariate Beta function as a normalization constant.

The resulting PDF describes the probability density of a random vector on the simplex, making it a key distribution in Bayesian statistics and machine learning.
