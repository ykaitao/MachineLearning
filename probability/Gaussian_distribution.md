The **Gaussian distribution**, also known as the **normal distribution**, is a continuous probability distribution characterized by its bell-shaped curve. The **probability density function (PDF)** of the Gaussian distribution describes the relative likelihood of a random variable taking on a specific value. Let’s derive the formula for the Gaussian PDF step by step.

---

### **1. Properties of the Gaussian Distribution**
The Gaussian distribution is defined by two parameters:
- **Mean (\( \mu \))**: The center of the distribution.
- **Variance (\( \sigma^2 \))**: The spread of the distribution.

The PDF of the Gaussian distribution must satisfy the following properties:
1. **Normalization**: The total area under the curve must equal 1.
2. **Symmetry**: The distribution is symmetric about the mean \( \mu \).
3. **Bell Shape**: The distribution has a single peak at \( \mu \) and decays exponentially as \( x \) moves away from \( \mu \).

---

### **2. Derivation of the Gaussian PDF**
We start by assuming the form of the Gaussian PDF and then use the properties of probability distributions to derive the exact formula.

#### **Step 1: Assume the Form of the PDF**
The Gaussian PDF is assumed to have the form:
\[
f(x) = A e^{-B(x - \mu)^2}
\]
where:
- \( A \) and \( B \) are constants to be determined.
- \( \mu \) is the mean of the distribution.

This form ensures that the PDF is symmetric about \( \mu \) and decays exponentially as \( x \) moves away from \( \mu \).

---

#### **Step 2: Normalize the PDF**
The total area under the PDF must equal 1:
\[
\int_{-\infty}^{\infty} f(x) \, dx = 1.
\]
Substitute the assumed form of \( f(x) \):
\[
\int_{-\infty}^{\infty} A e^{-B(x - \mu)^2} \, dx = 1.
\]

To solve this integral, use the substitution \( u = x - \mu \). Then \( du = dx \), and the limits of integration remain the same:
\[
A \int_{-\infty}^{\infty} e^{-B u^2} \, du = 1.
\]

The integral \( \int_{-\infty}^{\infty} e^{-B u^2} \, du \) is a Gaussian integral, and its value is:
\[
\int_{-\infty}^{\infty} e^{-B u^2} \, du = \sqrt{\frac{\pi}{B}}.
\]
Thus:
\[
A \sqrt{\frac{\pi}{B}} = 1.
\]
Solve for \( A \):
\[
A = \sqrt{\frac{B}{\pi}}.
\]

---

#### **Step 3: Relate \( B \) to the Variance \( \sigma^2 \)**
The variance \( \sigma^2 \) of the distribution is defined as:
\[
\sigma^2 = \int_{-\infty}^{\infty} (x - \mu)^2 f(x) \, dx.
\]
Substitute \( f(x) = A e^{-B(x - \mu)^2} \):
\[
\sigma^2 = A \int_{-\infty}^{\infty} (x - \mu)^2 e^{-B(x - \mu)^2} \, dx.
\]
Use the substitution \( u = x - \mu \):
\[
\sigma^2 = A \int_{-\infty}^{\infty} u^2 e^{-B u^2} \, du.
\]

The integral \( \int_{-\infty}^{\infty} u^2 e^{-B u^2} \, du \) can be evaluated using integration by parts or by differentiating the Gaussian integral. Its value is:
\[
\int_{-\infty}^{\infty} u^2 e^{-B u^2} \, du = \frac{\sqrt{\pi}}{2 B^{3/2}}.
\]
Thus:
\[
\sigma^2 = A \cdot \frac{\sqrt{\pi}}{2 B^{3/2}}.
\]
Substitute \( A = \sqrt{\frac{B}{\pi}} \):
\[
\sigma^2 = \sqrt{\frac{B}{\pi}} \cdot \frac{\sqrt{\pi}}{2 B^{3/2}}.
\]
Simplify:
\[
\sigma^2 = \frac{1}{2 B}.
\]
Solve for \( B \):
\[
B = \frac{1}{2 \sigma^2}.
\]

---

#### **Step 4: Substitute \( A \) and \( B \) into the PDF**
From Step 2, we have:
\[
A = \sqrt{\frac{B}{\pi}}.
\]
Substitute \( B = \frac{1}{2 \sigma^2} \):
\[
A = \sqrt{\frac{1}{2 \sigma^2 \pi}} = \frac{1}{\sqrt{2 \pi \sigma^2}}.
\]

Now, substitute \( A \) and \( B \) into the assumed form of \( f(x) \):
\[
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x - \mu)^2}{2 \sigma^2}}.
\]

---

### **3. Gaussian PDF Formula**
The PDF of the Gaussian distribution is:
\[
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x - \mu)^2}{2 \sigma^2}},
\]
where:
- \( \mu \): Mean of the distribution.
- \( \sigma^2 \): Variance of the distribution.
- \( \sigma \): Standard deviation of the distribution.

---

### **4. Summary**
The Gaussian PDF is derived by:
1. Assuming an exponential form for the PDF.
2. Normalizing the PDF to ensure the total area under the curve is 1.
3. Relating the constant \( B \) to the variance \( \sigma^2 \).
4. Substituting the constants \( A \) and \( B \) into the assumed form.

The resulting formula describes the probability density of a continuous random variable following a Gaussian distribution.

The **multivariate Gaussian distribution** is a generalization of the one-dimensional Gaussian distribution to higher dimensions. It describes the joint probability distribution of a random vector \( \mathbf{X} = (X_1, X_2, \dots, X_d)^T \) in \( d \)-dimensional space. The **probability density function (PDF)** of the multivariate Gaussian distribution is given by:

---

### **1. Multivariate Gaussian PDF Formula**
The PDF of a \( d \)-dimensional multivariate Gaussian distribution is:

\[
f(\mathbf{x}) = \frac{1}{(2\pi)^{d/2} |\mathbf{\Sigma}|^{1/2}} \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \mathbf{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right),
\]

where:
- \( \mathbf{x} = (x_1, x_2, \dots, x_d)^T \): A \( d \)-dimensional vector representing a point in the space.
- \( \boldsymbol{\mu} = (\mu_1, \mu_2, \dots, \mu_d)^T \): The **mean vector**, representing the center of the distribution.
- \( \mathbf{\Sigma} \): The **covariance matrix** (a \( d \times d \) symmetric positive definite matrix), describing the spread and correlation between the dimensions.
- \( |\mathbf{\Sigma}| \): The determinant of the covariance matrix.
- \( \mathbf{\Sigma}^{-1} \): The inverse of the covariance matrix.

---

### **2. Key Components of the Formula**

#### **Mean Vector \( \boldsymbol{\mu} \)**
The mean vector \( \boldsymbol{\mu} \) represents the expected value of the random vector \( \mathbf{X} \):
\[
\boldsymbol{\mu} = \mathbb{E}[\mathbf{X}] = (\mathbb{E}[X_1], \mathbb{E}[X_2], \dots, \mathbb{E}[X_d])^T.
\]

#### **Covariance Matrix \( \mathbf{\Sigma} \)**
The covariance matrix \( \mathbf{\Sigma} \) captures the variances and covariances between the components of \( \mathbf{X} \):
\[
\mathbf{\Sigma} = \mathbb{E}[(\mathbf{X} - \boldsymbol{\mu})(\mathbf{X} - \boldsymbol{\mu})^T].
\]
The diagonal elements \( \Sigma_{ii} \) represent the variances of the individual components:
\[
\Sigma_{ii} = \text{Var}(X_i).
\]
The off-diagonal elements \( \Sigma_{ij} \) represent the covariances between components \( X_i \) and \( X_j \):
\[
\Sigma_{ij} = \text{Cov}(X_i, X_j).
\]

#### **Normalization Constant**
The term \( \frac{1}{(2\pi)^{d/2} |\mathbf{\Sigma}|^{1/2}} \) ensures that the PDF integrates to 1 over the entire \( d \)-dimensional space:
\[
\int_{\mathbb{R}^d} f(\mathbf{x}) \, d\mathbf{x} = 1.
\]

#### **Exponential Term**
The term \( \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \mathbf{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right) \) determines the shape of the distribution:
- It is maximized when \( \mathbf{x} = \boldsymbol{\mu} \).
- It decays exponentially as \( \mathbf{x} \) moves away from \( \boldsymbol{\mu} \), with the rate of decay determined by the covariance matrix \( \mathbf{\Sigma} \).

---

### **3. Special Cases**

#### **Univariate Gaussian (\( d = 1 \))**
For \( d = 1 \), the multivariate Gaussian reduces to the one-dimensional Gaussian distribution:
\[
f(x) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp\left(-\frac{(x - \mu)^2}{2\sigma^2}\right),
\]
where \( \mu \) is the mean and \( \sigma^2 \) is the variance.

#### **Diagonal Covariance Matrix**
If the covariance matrix \( \mathbf{\Sigma} \) is diagonal (i.e., the components of \( \mathbf{X} \) are uncorrelated), the PDF simplifies to:
\[
f(\mathbf{x}) = \prod_{i=1}^d \frac{1}{\sqrt{2\pi \sigma_i^2}} \exp\left(-\frac{(x_i - \mu_i)^2}{2\sigma_i^2}\right),
\]
where \( \sigma_i^2 \) is the variance of the \( i \)-th component.

---

### **4. Geometric Interpretation**
- The level sets of the multivariate Gaussian PDF are ellipsoids centered at \( \boldsymbol{\mu} \).
- The shape and orientation of the ellipsoids are determined by the covariance matrix \( \mathbf{\Sigma} \).
- The axes of the ellipsoids correspond to the eigenvectors of \( \mathbf{\Sigma} \), and the lengths of the axes are proportional to the square roots of the eigenvalues of \( \mathbf{\Sigma} \).

---

### **5. Example: Bivariate Gaussian (\( d = 2 \))**
For a 2-dimensional Gaussian, the PDF is:
\[
f(x_1, x_2) = \frac{1}{2\pi |\mathbf{\Sigma}|^{1/2}} \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \mathbf{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right),
\]
where:
- \( \mathbf{x} = (x_1, x_2)^T \),
- \( \boldsymbol{\mu} = (\mu_1, \mu_2)^T \),
- \( \mathbf{\Sigma} = \begin{pmatrix} \sigma_1^2 & \rho \sigma_1 \sigma_2 \\ \rho \sigma_1 \sigma_2 & \sigma_2^2 \end{pmatrix} \),
- \( \rho \): Correlation coefficient between \( X_1 \) and \( X_2 \).

---

### **6. Summary**
The PDF of a multivariate Gaussian distribution is:
\[
f(\mathbf{x}) = \frac{1}{(2\pi)^{d/2} |\mathbf{\Sigma}|^{1/2}} \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \mathbf{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right).
\]
It generalizes the one-dimensional Gaussian to higher dimensions, with the covariance matrix \( \mathbf{\Sigma} \) capturing the relationships between the components of the random vector.
