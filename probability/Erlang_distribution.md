The **Erlang distribution** is a continuous probability distribution that generalizes the **Exponential distribution**. It models the time until \( k \) events occur in a Poisson process, where events occur continuously and independently at a constant average rate. Let’s derive the **probability density function (PDF)** of the Erlang distribution step by step.

---

### **1. Background**
The Erlang distribution is characterized by two parameters:
- **Shape parameter (\( k \))**: The number of events to occur (must be a positive integer).
- **Rate parameter (\( \lambda \))**: The average rate at which events occur. Alternatively, the **scale parameter** \( \theta = \frac{1}{\lambda} \) represents the mean time between events.

The PDF of the Erlang distribution is:
\[
f(x) = \frac{\lambda^k x^{k-1} e^{-\lambda x}}{(k-1)!}, \quad x \geq 0.
\]

---

### **2. Derivation of the PDF**
The Erlang distribution can be derived as the sum of \( k \) independent and identically distributed (i.i.d.) exponential random variables. Here’s how:

#### **Step 1: Exponential Distribution**
The exponential distribution with rate parameter \( \lambda \) has the PDF:
\[
f_X(x) = \lambda e^{-\lambda x}, \quad x \geq 0.
\]

#### **Step 2: Sum of \( k \) Exponential Random Variables**
Let \( X_1, X_2, \dots, X_k \) be \( k \) independent exponential random variables, each with rate parameter \( \lambda \). Define:
\[
Y = X_1 + X_2 + \dots + X_k.
\]
We want to find the PDF of \( Y \).

#### **Step 3: Convolution of PDFs**
The PDF of the sum of independent random variables is the convolution of their individual PDFs. For \( k = 1 \), the PDF of \( Y \) is simply the exponential PDF:
\[
f_Y(y) = \lambda e^{-\lambda y}, \quad y \geq 0.
\]

For \( k = 2 \), the PDF of \( Y = X_1 + X_2 \) is the convolution of two exponential PDFs:
\[
f_Y(y) = \int_0^y f_{X_1}(x) f_{X_2}(y - x) \, dx.
\]
Substitute the exponential PDFs:
\[
f_Y(y) = \int_0^y \lambda e^{-\lambda x} \cdot \lambda e^{-\lambda (y - x)} \, dx.
\]
Simplify the integrand:
\[
f_Y(y) = \lambda^2 e^{-\lambda y} \int_0^y 1 \, dx.
\]
Evaluate the integral:
\[
f_Y(y) = \lambda^2 e^{-\lambda y} \cdot y.
\]

For general \( k \), the convolution of \( k \) exponential PDFs leads to the Erlang PDF.

#### **Step 4: Generalize to \( k \) Variables**
The PDF of the sum of \( k \) independent exponential random variables is:
\[
f_Y(y) = \frac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}, \quad y \geq 0.
\]
This is the PDF of the Erlang distribution with shape parameter \( k \) and rate parameter \( \lambda \).

---

### **3. Erlang PDF Formula**
The PDF of the Erlang distribution with shape parameter \( k \) and rate parameter \( \lambda \) is:
\[
f_Y(y) = \frac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}, \quad y \geq 0.
\]

---

### **4. Alternative Parameterization (Scale Parameter)**
The Erlang distribution is often parameterized using the **scale parameter** \( \theta = \frac{1}{\lambda} \), which represents the mean time between events. In this case, the PDF becomes:
\[
f_Y(y) = \frac{y^{k-1} e^{-y / \theta}}{\theta^k (k-1)!}, \quad y \geq 0.
\]

---

### **5. Summary**
The PDF of the Erlang distribution is derived by:
1. Starting with the exponential distribution.
2. Using convolution to find the PDF of the sum of \( k \) independent exponential random variables.
3. Generalizing the result to \( k \) variables.

The resulting PDF describes the probability density of the time until \( k \) events occur in a Poisson process.
