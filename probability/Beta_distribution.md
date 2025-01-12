The **Beta distribution** is a continuous probability distribution defined on the interval \([0, 1]\). It is often used to model random variables that represent proportions or probabilities. Let’s derive the **probability density function (PDF)** of the Beta distribution step by step.

---

### **1. Background**
The Beta distribution is characterized by two parameters:
- **Shape parameter (\( \alpha \))**: Controls the shape of the distribution.
- **Shape parameter (\( \beta \))**: Controls the shape of the distribution.

The PDF of the Beta distribution is:
\[
f(x) = \frac{x^{\alpha-1} (1-x)^{\beta-1}}{B(\alpha, \beta)}, \quad 0 \leq x \leq 1,
\]
where \( B(\alpha, \beta) \) is the **Beta function**, which serves as a normalization constant.

---

### **2. Derivation of the PDF**
The Beta distribution can be derived as the distribution of the ratio of two independent gamma-distributed random variables. Here’s how:

#### **Step 1: Gamma Distribution**
The gamma distribution with shape parameter \( k \) and scale parameter \( \theta \) has the PDF:
\[
f_Y(y) = \frac{y^{k-1} e^{-y / \theta}}{\theta^k \Gamma(k)}, \quad y > 0.
\]

#### **Step 2: Ratio of Two Gamma Random Variables**
Let \( Y_1 \) and \( Y_2 \) be two independent gamma-distributed random variables with shape parameters \( \alpha \) and \( \beta \), respectively, and scale parameter \( \theta = 1 \). Define:
\[
X = \frac{Y_1}{Y_1 + Y_2}.
\]
We want to find the PDF of \( X \).

#### **Step 3: Joint PDF of \( Y_1 \) and \( Y_2 \)**
Since \( Y_1 \) and \( Y_2 \) are independent, their joint PDF is the product of their individual PDFs:
\[
f_{Y_1, Y_2}(y_1, y_2) = f_{Y_1}(y_1) \cdot f_{Y_2}(y_2) = \frac{y_1^{\alpha-1} e^{-y_1}}{\Gamma(\alpha)} \cdot \frac{y_2^{\beta-1} e^{-y_2}}{\Gamma(\beta)}.
\]

#### **Step 4: Transform to \( X \) and \( Y_2 \)**
Define the transformation:
\[
X = \frac{Y_1}{Y_1 + Y_2}, \quad Y_2 = Y_2.
\]
The inverse transformation is:
\[
Y_1 = \frac{X Y_2}{1 - X}, \quad Y_2 = Y_2.
\]

The Jacobian determinant of this transformation is:
\[
J = \begin{vmatrix}
\frac{\partial y_1}{\partial x} & \frac{\partial y_1}{\partial y_2} \\
\frac{\partial y_2}{\partial x} & \frac{\partial y_2}{\partial y_2}
\end{vmatrix}
= \begin{vmatrix}
\frac{y_2}{(1 - x)^2} & \frac{x}{1 - x} \\
0 & 1
\end{vmatrix}
= \frac{y_2}{(1 - x)^2}.
\]

#### **Step 5: Joint PDF of \( X \) and \( Y_2 \)**
Using the transformation rule for PDFs, the joint PDF of \( X \) and \( Y_2 \) is:
\[
f_{X, Y_2}(x, y_2) = f_{Y_1, Y_2}(y_1, y_2) \cdot |J|.
\]
Substitute \( y_1 = \frac{x y_2}{1 - x} \) and \( |J| = \frac{y_2}{(1 - x)^2} \):
\[
f_{X, Y_2}(x, y_2) = \frac{\left(\frac{x y_2}{1 - x}\right)^{\alpha-1} e^{-x y_2 / (1 - x)}}{\Gamma(\alpha)} \cdot \frac{y_2^{\beta-1} e^{-y_2}}{\Gamma(\beta)} \cdot \frac{y_2}{(1 - x)^2}.
\]

#### **Step 6: Marginal PDF of \( X \)**
To find the marginal PDF of \( X \), integrate the joint PDF \( f_{X, Y_2}(x, y_2) \) over all possible values of \( Y_2 \):
\[
f_X(x) = \int_0^\infty f_{X, Y_2}(x, y_2) \, dy_2.
\]
Substitute \( f_{X, Y_2}(x, y_2) \):
\[
f_X(x) = \int_0^\infty \frac{\left(\frac{x y_2}{1 - x}\right)^{\alpha-1} e^{-x y_2 / (1 - x)}}{\Gamma(\alpha)} \cdot \frac{y_2^{\beta-1} e^{-y_2}}{\Gamma(\beta)} \cdot \frac{y_2}{(1 - x)^2} \, dy_2.
\]
Simplify the integrand:
\[
f_X(x) = \frac{x^{\alpha-1} (1 - x)^{-(\alpha + \beta)}}{\Gamma(\alpha) \Gamma(\beta)} \int_0^\infty y_2^{\alpha + \beta - 1} e^{-y_2 / (1 - x)} \, dy_2.
\]

#### **Step 7: Evaluate the Integral**
The integral is a gamma function integral of the form:
\[
\int_0^\infty t^{k-1} e^{-a t} \, dt = \frac{\Gamma(k)}{a^k}.
\]
Here, \( k = \alpha + \beta \) and \( a = \frac{1}{1 - x} \). Thus:
\[
\int_0^\infty y_2^{\alpha + \beta - 1} e^{-y_2 / (1 - x)} \, dy_2 = \Gamma(\alpha + \beta) (1 - x)^{\alpha + \beta}.
\]

#### **Step 8: Simplify the PDF**
Substitute the integral result back into \( f_X(x) \):
\[
f_X(x) = \frac{x^{\alpha-1} (1 - x)^{-(\alpha + \beta)}}{\Gamma(\alpha) \Gamma(\beta)} \cdot \Gamma(\alpha + \beta) (1 - x)^{\alpha + \beta}.
\]
Simplify the expression:
\[
f_X(x) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} x^{\alpha-1} (1 - x)^{\beta-1}.
\]

#### **Step 9: Beta Function**
The **Beta function** \( B(\alpha, \beta) \) is defined as:
\[
B(\alpha, \beta) = \frac{\Gamma(\alpha) \Gamma(\beta)}{\Gamma(\alpha + \beta)}.
\]
Thus, the PDF of the Beta distribution is:
\[
f_X(x) = \frac{x^{\alpha-1} (1 - x)^{\beta-1}}{B(\alpha, \beta)}.
\]

---

### **3. Beta PDF Formula**
The PDF of the Beta distribution with shape parameters \( \alpha \) and \( \beta \) is:
\[
f_X(x) = \frac{x^{\alpha-1} (1 - x)^{\beta-1}}{B(\alpha, \beta)}, \quad 0 \leq x \leq 1,
\]
where \( B(\alpha, \beta) \) is the Beta function.

---

### **4. Summary**
The PDF of the Beta distribution is derived by:
1. Starting with the ratio of two independent gamma-distributed random variables.
2. Using transformation and integration to find the marginal PDF.
3. Introducing the Beta function as a normalization constant.

The resulting PDF describes the probability density of a random variable that represents proportions or probabilities.
