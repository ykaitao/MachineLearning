The **Cauchy distribution** is a continuous probability distribution that is symmetric and has heavy tails. It is often used in physics, finance, and other fields to model phenomena with extreme values or outliers. Let’s derive its **probability density function (PDF)** step by step.

---

### **1. Definition of the Cauchy Distribution**
The Cauchy distribution is characterized by two parameters:
- **Location parameter (\( x_0 \))**: The peak of the distribution (median and mode).
- **Scale parameter (\( \gamma \))**: Controls the width of the distribution (\( \gamma > 0 \)).

The PDF of the Cauchy distribution is defined for \( x \in \mathbb{R} \).

---

### **2. Derivation of the PDF**
The Cauchy distribution can be derived as the ratio of two independent standard normal random variables. Here’s how:

#### **Step 1: Ratio of Two Standard Normal Random Variables**
Let \( Z_1 \) and \( Z_2 \) be two independent standard normal random variables:
\[
Z_1 \sim N(0, 1), \quad Z_2 \sim N(0, 1).
\]
Define the random variable \( X \) as:
\[
X = \frac{Z_1}{Z_2}.
\]
We want to find the PDF of \( X \).

#### **Step 2: Joint PDF of \( Z_1 \) and \( Z_2 \)**
Since \( Z_1 \) and \( Z_2 \) are independent, their joint PDF is the product of their individual PDFs:
\[
f_{Z_1, Z_2}(z_1, z_2) = f_{Z_1}(z_1) \cdot f_{Z_2}(z_2) = \frac{1}{\sqrt{2\pi}} e^{-z_1^2 / 2} \cdot \frac{1}{\sqrt{2\pi}} e^{-z_2^2 / 2}.
\]
Simplify:
\[
f_{Z_1, Z_2}(z_1, z_2) = \frac{1}{2\pi} e^{-(z_1^2 + z_2^2) / 2}.
\]

#### **Step 3: Transform to \( X \) and \( Z_2 \)**
Define the transformation:
\[
X = \frac{Z_1}{Z_2}, \quad Z_2 = Z_2.
\]
The inverse transformation is:
\[
Z_1 = X Z_2, \quad Z_2 = Z_2.
\]

The Jacobian determinant of this transformation is:
\[
J = \begin{vmatrix}
\frac{\partial z_1}{\partial x} & \frac{\partial z_1}{\partial z_2} \\
\frac{\partial z_2}{\partial x} & \frac{\partial z_2}{\partial z_2}
\end{vmatrix}
= \begin{vmatrix}
z_2 & x \\
0 & 1
\end{vmatrix}
= z_2.
\]

#### **Step 4: Joint PDF of \( X \) and \( Z_2 \)**
Using the transformation rule for PDFs, the joint PDF of \( X \) and \( Z_2 \) is:
\[
f_{X, Z_2}(x, z_2) = f_{Z_1, Z_2}(z_1, z_2) \cdot |J|.
\]
Substitute \( z_1 = x z_2 \) and \( |J| = |z_2| \):
\[
f_{X, Z_2}(x, z_2) = \frac{1}{2\pi} e^{-(x^2 z_2^2 + z_2^2) / 2} \cdot |z_2|.
\]
Simplify:
\[
f_{X, Z_2}(x, z_2) = \frac{1}{2\pi} |z_2| e^{-z_2^2 (1 + x^2) / 2}.
\]

#### **Step 5: Marginal PDF of \( X \)**
To find the marginal PDF of \( X \), integrate the joint PDF \( f_{X, Z_2}(x, z_2) \) over all possible values of \( Z_2 \):
\[
f_X(x) = \int_{-\infty}^\infty f_{X, Z_2}(x, z_2) \, dz_2.
\]
Substitute \( f_{X, Z_2}(x, z_2) \):
\[
f_X(x) = \frac{1}{2\pi} \int_{-\infty}^\infty |z_2| e^{-z_2^2 (1 + x^2) / 2} \, dz_2.
\]

#### **Step 6: Evaluate the Integral**
The integral can be split into two parts (for \( z_2 \geq 0 \) and \( z_2 \leq 0 \)):
\[
f_X(x) = \frac{1}{2\pi} \left( \int_0^\infty z_2 e^{-z_2^2 (1 + x^2) / 2} \, dz_2 + \int_{-\infty}^0 (-z_2) e^{-z_2^2 (1 + x^2) / 2} \, dz_2 \right).
\]
Both integrals are equal, so:
\[
f_X(x) = \frac{1}{\pi} \int_0^\infty z_2 e^{-z_2^2 (1 + x^2) / 2} \, dz_2.
\]
Let \( u = z_2^2 (1 + x^2) / 2 \), so \( du = z_2 (1 + x^2) \, dz_2 \). The integral becomes:
\[
f_X(x) = \frac{1}{\pi} \int_0^\infty \frac{e^{-u}}{1 + x^2} \, du = \frac{1}{\pi (1 + x^2)} \int_0^\infty e^{-u} \, du.
\]
Evaluate the integral:
\[
\int_0^\infty e^{-u} \, du = 1.
\]
Thus:
\[
f_X(x) = \frac{1}{\pi (1 + x^2)}.
\]

#### **Step 7: Generalize to Location and Scale Parameters**
To include the location parameter \( x_0 \) and scale parameter \( \gamma \), replace \( x \) with \( \frac{x - x_0}{\gamma} \):
\[
f_X(x) = \frac{1}{\pi \gamma \left(1 + \left(\frac{x - x_0}{\gamma}\right)^2\right)}.
\]

---

### **3. PDF Formula**
The PDF of the Cauchy distribution with location parameter \( x_0 \) and scale parameter \( \gamma \) is:
\[
f_X(x) = \frac{1}{\pi \gamma \left(1 + \left(\frac{x - x_0}{\gamma}\right)^2\right)}, \quad x \in \mathbb{R}.
\]

---

### **4. Key Properties**
- **Mean**: The mean is undefined (the integral diverges).
- **Variance**: The variance is undefined (the integral diverges).
- **Heavy Tails**: The Cauchy distribution has much heavier tails than the normal distribution.

---

### **5. Use Case**
The Cauchy distribution is used to model:
- Phenomena with extreme values or outliers (e.g., financial returns, resonance behavior in physics),
- Data with no well-defined mean or variance.

---

### **6. Example**
Suppose \( X \) follows a Cauchy distribution with \( x_0 = 0 \) and \( \gamma = 1 \). The PDF of \( X \) is:
\[
f_X(x) = \frac{1}{\pi (1 + x^2)}, \quad x \in \mathbb{R}.
\]

---

### **7. Connection to the Normal Distribution**
The Cauchy distribution arises as the ratio of two independent standard normal random variables, but it has much heavier tails and no finite moments.

---

### **Summary**
The PDF of the Cauchy distribution is:
\[
f_X(x) = \frac{1}{\pi \gamma \left(1 + \left(\frac{x - x_0}{\gamma}\right)^2\right)}, \quad x \in \mathbb{R}.
\]
It is a heavy-tailed distribution used to model extreme values and outliers. Let me know if you'd like further details!
