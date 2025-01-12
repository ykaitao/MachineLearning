The **Laplace distribution**, also known as the **double exponential distribution**, is a continuous probability distribution that is symmetric and has sharp peaks. It is often used in statistics and signal processing. Let’s derive the **probability density function (PDF)** of the Laplace distribution step by step.

---

### **1. Definition of the Laplace Distribution**
The Laplace distribution is characterized by two parameters:
- **Location parameter (\( \mu \))**: The mean (and median) of the distribution.
- **Scale parameter (\( b \))**: Controls the spread of the distribution.

The PDF of the Laplace distribution is given by:
\[
f(x) = \frac{1}{2b} \exp\left(-\frac{|x - \mu|}{b}\right), \quad x \in \mathbb{R}.
\]

---

### **2. Derivation of the PDF**
The Laplace distribution can be derived as the difference of two independent and identically distributed (i.i.d.) exponential random variables. Here’s how:

#### **Step 1: Exponential Distribution**
The exponential distribution with rate parameter \( \lambda = \frac{1}{b} \) has the PDF:
\[
f_Y(y) = \frac{1}{b} e^{-y / b}, \quad y > 0.
\]

#### **Step 2: Difference of Two Exponential Random Variables**
Let \( Y_1 \) and \( Y_2 \) be two independent exponential random variables with the same rate parameter \( \lambda = \frac{1}{b} \). Define:
\[
X = Y_1 - Y_2.
\]
We want to find the PDF of \( X \).

#### **Step 3: Joint PDF of \( Y_1 \) and \( Y_2 \)**
Since \( Y_1 \) and \( Y_2 \) are independent, their joint PDF is the product of their individual PDFs:
\[
f_{Y_1, Y_2}(y_1, y_2) = f_{Y_1}(y_1) \cdot f_{Y_2}(y_2) = \frac{1}{b} e^{-y_1 / b} \cdot \frac{1}{b} e^{-y_2 / b} = \frac{1}{b^2} e^{-(y_1 + y_2) / b}.
\]

#### **Step 4: Transform to \( X \) and \( Y_2 \)**
Define the transformation:
\[
X = Y_1 - Y_2, \quad Y_2 = Y_2.
\]
The inverse transformation is:
\[
Y_1 = X + Y_2, \quad Y_2 = Y_2.
\]

The Jacobian determinant of this transformation is:
\[
J = \begin{vmatrix}
\frac{\partial y_1}{\partial x} & \frac{\partial y_1}{\partial y_2} \\
\frac{\partial y_2}{\partial x} & \frac{\partial y_2}{\partial y_2}
\end{vmatrix}
= \begin{vmatrix}
1 & 1 \\
0 & 1
\end{vmatrix}
= 1.
\]

#### **Step 5: Joint PDF of \( X \) and \( Y_2 \)**
Using the transformation rule for PDFs, the joint PDF of \( X \) and \( Y_2 \) is:
\[
f_{X, Y_2}(x, y_2) = f_{Y_1, Y_2}(y_1, y_2) \cdot |J|.
\]
Substitute \( y_1 = x + y_2 \) and \( |J| = 1 \):
\[
f_{X, Y_2}(x, y_2) = \frac{1}{b^2} e^{-(x + y_2 + y_2) / b} = \frac{1}{b^2} e^{-(x + 2y_2) / b}.
\]

#### **Step 6: Marginal PDF of \( X \)**
To find the marginal PDF of \( X \), integrate the joint PDF \( f_{X, Y_2}(x, y_2) \) over all possible values of \( Y_2 \):
\[
f_X(x) = \int_{-\infty}^{\infty} f_{X, Y_2}(x, y_2) \, dy_2.
\]
Since \( Y_2 > 0 \), the limits of integration are \( y_2 = 0 \) to \( y_2 = \infty \):
\[
f_X(x) = \int_0^\infty \frac{1}{b^2} e^{-(x + 2y_2) / b} \, dy_2.
\]

#### **Step 7: Evaluate the Integral**
Factor out the terms not depending on \( y_2 \):
\[
f_X(x) = \frac{1}{b^2} e^{-x / b} \int_0^\infty e^{-2y_2 / b} \, dy_2.
\]
The integral is:
\[
\int_0^\infty e^{-2y_2 / b} \, dy_2 = \frac{b}{2}.
\]
Thus:
\[
f_X(x) = \frac{1}{b^2} e^{-x / b} \cdot \frac{b}{2} = \frac{1}{2b} e^{-x / b}.
\]

#### **Step 8: Symmetry and Generalization**
The above derivation assumes \( x > 0 \). For \( x < 0 \), the symmetry of the Laplace distribution implies:
\[
f_X(x) = \frac{1}{2b} e^{x / b}.
\]
Combining both cases, the PDF of the Laplace distribution is:
\[
f_X(x) = \frac{1}{2b} \exp\left(-\frac{|x|}{b}\right).
\]

#### **Step 9: Include the Location Parameter \( \mu \)**
To generalize the distribution to include a location parameter \( \mu \), replace \( x \) with \( x - \mu \):
\[
f_X(x) = \frac{1}{2b} \exp\left(-\frac{|x - \mu|}{b}\right).
\]

---

### **3. Laplace PDF Formula**
The PDF of the Laplace distribution with location parameter \( \mu \) and scale parameter \( b \) is:
\[
f_X(x) = \frac{1}{2b} \exp\left(-\frac{|x - \mu|}{b}\right), \quad x \in \mathbb{R}.
\]

---

### **4. Summary**
The PDF of the Laplace distribution is derived by:
1. Starting with the difference of two independent exponential random variables.
2. Using transformation and integration to find the marginal PDF.
3. Generalizing the result to include a location parameter \( \mu \).

The resulting PDF describes the probability density of the Laplace distribution, which is symmetric and has sharp peaks.
