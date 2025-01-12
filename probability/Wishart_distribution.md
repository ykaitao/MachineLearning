The **Wishart distribution** is a continuous probability distribution defined over symmetric, positive definite matrices. It is the multivariate generalization of the **Gamma distribution** and is widely used in multivariate statistics, particularly in the analysis of covariance matrices. Let’s derive its **probability density function (PDF)** step by step.

---

### **1. Definition of the Wishart Distribution**
The Wishart distribution is characterized by two parameters:
- \( n \): The degrees of freedom (\( n \geq p \), where \( p \) is the dimension of the matrix),
- \( \mathbf{V} \): The scale matrix (a \( p \times p \) symmetric, positive definite matrix).

The random variable \( \mathbf{X} \) is a \( p \times p \) symmetric, positive definite matrix.

---

### **2. Derivation of the PDF**
The PDF of the Wishart distribution is derived from the properties of multivariate normal distributions and the definition of the Gamma distribution. Here’s how it works:

#### **Step 1: Multivariate Normal Distribution**
Let \( \mathbf{Z}_1, \mathbf{Z}_2, \dots, \mathbf{Z}_n \) be \( n \) independent \( p \)-dimensional random vectors, each following a multivariate normal distribution:
\[
\mathbf{Z}_i \sim N_p(\mathbf{0}, \mathbf{V}), \quad i = 1, 2, \dots, n.
\]

#### **Step 2: Sum of Outer Products**
Define the random matrix \( \mathbf{X} \) as the sum of the outer products of the \( \mathbf{Z}_i \):
\[
\mathbf{X} = \sum_{i=1}^n \mathbf{Z}_i \mathbf{Z}_i^T.
\]
The matrix \( \mathbf{X} \) follows a Wishart distribution:
\[
\mathbf{X} \sim W_p(n, \mathbf{V}).
\]

#### **Step 3: PDF of the Wishart Distribution**
The PDF of the Wishart distribution is given by:
\[
f(\mathbf{X} | n, \mathbf{V}) = \frac{|\mathbf{X}|^{(n - p - 1)/2} \exp\left(-\frac{1}{2} \text{tr}(\mathbf{V}^{-1} \mathbf{X})\right)}{2^{np/2} |\mathbf{V}|^{n/2} \Gamma_p(n/2)},
\]
where:
- \( |\mathbf{X}| \): The determinant of \( \mathbf{X} \),
- \( \text{tr}(\cdot) \): The trace of a matrix,
- \( \Gamma_p(\cdot) \): The multivariate gamma function.

#### **Step 4: Multivariate Gamma Function**
The multivariate gamma function \( \Gamma_p(n/2) \) is defined as:
\[
\Gamma_p(n/2) = \pi^{p(p-1)/4} \prod_{j=1}^p \Gamma\left(\frac{n + 1 - j}{2}\right).
\]

---

### **3. PDF Formula**
The PDF of the Wishart distribution with degrees of freedom \( n \) and scale matrix \( \mathbf{V} \) is:
\[
f(\mathbf{X} | n, \mathbf{V}) = \frac{|\mathbf{X}|^{(n - p - 1)/2} \exp\left(-\frac{1}{2} \text{tr}(\mathbf{V}^{-1} \mathbf{X})\right)}{2^{np/2} |\mathbf{V}|^{n/2} \Gamma_p(n/2)}.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[\mathbf{X}] = n \mathbf{V} \),
- **Variance**: \( \text{Var}(X_{ij}) = n (V_{ij}^2 + V_{ii} V_{jj}) \),
- **Support**: \( \mathbf{X} \) is a symmetric, positive definite matrix.

---

### **5. Use Case**
The Wishart distribution is used to model:
- Covariance matrices in multivariate statistics,
- Bayesian inference for multivariate normal distributions,
- Random matrices in machine learning and signal processing.

---

### **6. Example**
Suppose \( \mathbf{X} \sim W_2(3, \mathbf{V}) \), where:
\[
\mathbf{V} = \begin{pmatrix} 1 & 0.5 \\ 0.5 & 1 \end{pmatrix}.
\]
The PDF of \( \mathbf{X} \) is:
\[
f(\mathbf{X} | 3, \mathbf{V}) = \frac{|\mathbf{X}|^{(3 - 2 - 1)/2} \exp\left(-\frac{1}{2} \text{tr}(\mathbf{V}^{-1} \mathbf{X})\right)}{2^{3 \cdot 2/2} |\mathbf{V}|^{3/2} \Gamma_2(3/2)}.
\]

---

### **7. Connection to the Gamma Distribution**
When \( p = 1 \), the Wishart distribution reduces to the **Gamma distribution**:
\[
f(x | n, v) = \frac{x^{(n - 2)/2} \exp\left(-\frac{x}{2v}\right)}{2^{n/2} v^{n/2} \Gamma(n/2)}.
\]

---

### **Summary**
The PDF of the Wishart distribution is:
\[
f(\mathbf{X} | n, \mathbf{V}) = \frac{|\mathbf{X}|^{(n - p - 1)/2} \exp\left(-\frac{1}{2} \text{tr}(\mathbf{V}^{-1} \mathbf{X})\right)}{2^{np/2} |\mathbf{V}|^{n/2} \Gamma_p(n/2)}.
\]
It models symmetric, positive definite matrices and is widely used in multivariate statistics. Let me know if you'd like further details!
