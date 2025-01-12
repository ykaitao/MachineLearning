The **chi-squared distribution** is a continuous probability distribution that arises in statistics, particularly in hypothesis testing and confidence interval estimation. It is the distribution of the sum of the squares of independent standard normal random variables. Let’s derive the **probability density function (PDF)** of the chi-squared distribution step by step.

---

### **1. Background**
The chi-squared distribution with \( \nu \) degrees of freedom is the distribution of the sum:
\[
X = Z_1^2 + Z_2^2 + \dots + Z_\nu^2,
\]
where \( Z_1, Z_2, \dots, Z_\nu \) are independent standard normal random variables (\( Z_i \sim N(0, 1) \)).

---

### **2. Derivation of the PDF**
To derive the PDF of the chi-squared distribution, we start with the PDF of a single standard normal random variable and use the properties of transformations of random variables.

#### **Step 1: PDF of a Single Standard Normal Variable**
The PDF of a standard normal random variable \( Z \) is:
\[
f_Z(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2 / 2}.
\]

#### **Step 2: PDF of \( Z^2 \)**
Let \( Y = Z^2 \). To find the PDF of \( Y \), we use the transformation method for random variables.

- The transformation is \( Y = Z^2 \), so \( Z = \sqrt{Y} \) or \( Z = -\sqrt{Y} \).
- The Jacobian of the transformation is:
  \[
  \left| \frac{dz}{dy} \right| = \frac{1}{2\sqrt{y}}.
  \]

The PDF of \( Y \) is:
\[
f_Y(y) = f_Z(\sqrt{y}) \cdot \left| \frac{dz}{dy} \right| + f_Z(-\sqrt{y}) \cdot \left| \frac{dz}{dy} \right|.
\]
Substitute \( f_Z(z) \):
\[
f_Y(y) = \frac{1}{\sqrt{2\pi}} e^{-y / 2} \cdot \frac{1}{2\sqrt{y}} + \frac{1}{\sqrt{2\pi}} e^{-y / 2} \cdot \frac{1}{2\sqrt{y}}.
\]
Combine the terms:
\[
f_Y(y) = \frac{1}{\sqrt{2\pi}} e^{-y / 2} \cdot \frac{1}{\sqrt{y}}.
\]

#### **Step 3: PDF of the Sum of \( \nu \) Independent \( Z_i^2 \)**
The chi-squared distribution with \( \nu \) degrees of freedom is the distribution of the sum:
\[
X = Y_1 + Y_2 + \dots + Y_\nu,
\]
where \( Y_i = Z_i^2 \) and each \( Y_i \) has the PDF derived in Step 2.

The sum of independent random variables corresponds to the convolution of their PDFs. However, for the chi-squared distribution, we can use the **gamma distribution** to simplify the derivation.

#### **Step 4: Relate to the Gamma Distribution**
The gamma distribution has the PDF:
\[
f(x; k, \theta) = \frac{x^{k-1} e^{-x / \theta}}{\theta^k \Gamma(k)}, \quad x > 0,
\]
where:
- \( k \): Shape parameter,
- \( \theta \): Scale parameter,
- \( \Gamma(k) \): Gamma function.

The chi-squared distribution is a special case of the gamma distribution with:
- Shape parameter \( k = \nu / 2 \),
- Scale parameter \( \theta = 2 \).

Thus, the PDF of the chi-squared distribution with \( \nu \) degrees of freedom is:
\[
f_X(x) = \frac{x^{\nu/2 - 1} e^{-x / 2}}{2^{\nu/2} \Gamma(\nu/2)}, \quad x > 0.
\]

---

### **3. Chi-Squared PDF Formula**
The PDF of the chi-squared distribution with \( \nu \) degrees of freedom is:
\[
f_X(x) = \frac{x^{\nu/2 - 1} e^{-x / 2}}{2^{\nu/2} \Gamma(\nu/2)}, \quad x > 0,
\]
where:
- \( \nu \): Degrees of freedom (\( \nu > 0 \)),
- \( \Gamma(\cdot) \): Gamma function,
- \( x \): Real-valued random variable (\( x > 0 \)).

---

### **4. Summary**
The PDF of the chi-squared distribution is derived by:
1. Starting with the PDF of a standard normal random variable.
2. Transforming to the distribution of \( Z^2 \).
3. Recognizing that the sum of \( \nu \) independent \( Z_i^2 \) variables follows a gamma distribution with specific parameters.

The resulting PDF describes the probability density of the chi-squared distribution, which is widely used in statistical inference.
