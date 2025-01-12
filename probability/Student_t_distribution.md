The **Student's t-distribution** is a probability distribution that arises when estimating the mean of a normally distributed population with a small sample size and unknown variance. It is widely used in hypothesis testing and confidence interval estimation. Let’s derive the **probability density function (PDF)** of the Student's t-distribution step by step.

---

### **1. Background**
The t-distribution is derived from the ratio of a standard normal random variable to the square root of a chi-squared random variable divided by its degrees of freedom. Specifically, if:
- \( Z \) is a standard normal random variable (\( Z \sim N(0, 1) \)),
- \( V \) is a chi-squared random variable with \( \nu \) degrees of freedom (\( V \sim \chi^2_\nu \)),
- \( Z \) and \( V \) are independent,

then the random variable:
\[
T = \frac{Z}{\sqrt{V / \nu}}
\]
follows a **Student's t-distribution** with \( \nu \) degrees of freedom.

---

### **2. Derivation of the PDF**
To derive the PDF of the t-distribution, we start with the joint distribution of \( Z \) and \( V \), and then transform to the distribution of \( T \).

#### **Step 1: Joint Distribution of \( Z \) and \( V \)**
- The PDF of \( Z \) (standard normal) is:
  \[
  f_Z(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2 / 2}.
  \]
- The PDF of \( V \) (chi-squared with \( \nu \) degrees of freedom) is:
  \[
  f_V(v) = \frac{v^{\nu/2 - 1} e^{-v/2}}{2^{\nu/2} \Gamma(\nu/2)}, \quad v > 0,
  \]
  where \( \Gamma(\cdot) \) is the gamma function.

Since \( Z \) and \( V \) are independent, their joint PDF is the product of their individual PDFs:
\[
f_{Z,V}(z, v) = f_Z(z) \cdot f_V(v) = \frac{1}{\sqrt{2\pi}} e^{-z^2 / 2} \cdot \frac{v^{\nu/2 - 1} e^{-v/2}}{2^{\nu/2} \Gamma(\nu/2)}.
\]

#### **Step 2: Transform to \( T \) and \( V \)**
Define the transformation:
\[
T = \frac{Z}{\sqrt{V / \nu}}, \quad V = V.
\]
The inverse transformation is:
\[
Z = T \sqrt{V / \nu}, \quad V = V.
\]

The Jacobian determinant of this transformation is:
\[
J = \begin{vmatrix}
\frac{\partial z}{\partial t} & \frac{\partial z}{\partial v} \\
\frac{\partial v}{\partial t} & \frac{\partial v}{\partial v}
\end{vmatrix}
= \begin{vmatrix}
\sqrt{v / \nu} & \frac{t}{2\sqrt{v \nu}} \\
0 & 1
\end{vmatrix}
= \sqrt{v / \nu}.
\]

#### **Step 3: Joint PDF of \( T \) and \( V \)**
Using the transformation rule for PDFs, the joint PDF of \( T \) and \( V \) is:
\[
f_{T,V}(t, v) = f_{Z,V}(z, v) \cdot |J|.
\]
Substitute \( z = t \sqrt{v / \nu} \) and \( |J| = \sqrt{v / \nu} \):
\[
f_{T,V}(t, v) = \frac{1}{\sqrt{2\pi}} e^{-(t \sqrt{v / \nu})^2 / 2} \cdot \frac{v^{\nu/2 - 1} e^{-v/2}}{2^{\nu/2} \Gamma(\nu/2)} \cdot \sqrt{v / \nu}.
\]
Simplify the expression:
\[
f_{T,V}(t, v) = \frac{1}{\sqrt{2\pi}} e^{-t^2 v / (2\nu)} \cdot \frac{v^{\nu/2 - 1} e^{-v/2}}{2^{\nu/2} \Gamma(\nu/2)} \cdot \sqrt{v / \nu}.
\]

#### **Step 4: Marginal PDF of \( T \)**
To find the marginal PDF of \( T \), integrate the joint PDF \( f_{T,V}(t, v) \) over all possible values of \( V \):
\[
f_T(t) = \int_0^\infty f_{T,V}(t, v) \, dv.
\]
Substitute \( f_{T,V}(t, v) \):
\[
f_T(t) = \int_0^\infty \frac{1}{\sqrt{2\pi}} e^{-t^2 v / (2\nu)} \cdot \frac{v^{\nu/2 - 1} e^{-v/2}}{2^{\nu/2} \Gamma(\nu/2)} \cdot \sqrt{v / \nu} \, dv.
\]
Combine terms:
\[
f_T(t) = \frac{1}{\sqrt{2\pi} \cdot 2^{\nu/2} \Gamma(\nu/2) \sqrt{\nu}} \int_0^\infty v^{(\nu + 1)/2 - 1} e^{-v(1 + t^2 / \nu)/2} \, dv.
\]

#### **Step 5: Evaluate the Integral**
The integral is a gamma function integral of the form:
\[
\int_0^\infty x^{k-1} e^{-ax} \, dx = \frac{\Gamma(k)}{a^k}.
\]
Here, \( k = (\nu + 1)/2 \) and \( a = (1 + t^2 / \nu)/2 \). Thus:
\[
\int_0^\infty v^{(\nu + 1)/2 - 1} e^{-v(1 + t^2 / \nu)/2} \, dv = \frac{\Gamma((\nu + 1)/2)}{[(1 + t^2 / \nu)/2]^{(\nu + 1)/2}}.
\]

#### **Step 6: Simplify the PDF**
Substitute the integral result back into \( f_T(t) \):
\[
f_T(t) = \frac{1}{\sqrt{2\pi} \cdot 2^{\nu/2} \Gamma(\nu/2) \sqrt{\nu}} \cdot \frac{\Gamma((\nu + 1)/2)}{[(1 + t^2 / \nu)/2]^{(\nu + 1)/2}}.
\]
Simplify the expression:
\[
f_T(t) = \frac{\Gamma((\nu + 1)/2)}{\sqrt{\nu \pi} \cdot \Gamma(\nu/2)} \cdot \left(1 + \frac{t^2}{\nu}\right)^{-(\nu + 1)/2}.
\]

---

### **3. Student's t-Distribution PDF**
The PDF of the Student's t-distribution with \( \nu \) degrees of freedom is:
\[
f_T(t) = \frac{\Gamma\left(\frac{\nu + 1}{2}\right)}{\sqrt{\nu \pi} \cdot \Gamma\left(\frac{\nu}{2}\right)} \cdot \left(1 + \frac{t^2}{\nu}\right)^{-(\nu + 1)/2},
\]
where:
- \( \nu \): Degrees of freedom (\( \nu > 0 \)),
- \( \Gamma(\cdot) \): Gamma function,
- \( t \): Real-valued random variable.

---

### **4. Summary**
The PDF of the Student's t-distribution is derived by:
1. Starting with the joint distribution of a standard normal random variable and a chi-squared random variable.
2. Transforming to the t-distribution and integrating out the chi-squared variable.
3. Simplifying the result using properties of the gamma function.

The resulting PDF describes the probability density of the t-distribution, which is used in statistical inference for small sample sizes.
