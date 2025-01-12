The **gamma distribution** is a continuous probability distribution that generalizes the exponential and chi-squared distributions. It is widely used in statistics, particularly for modeling waiting times, reliability, and Bayesian inference. Let’s derive the **probability density function (PDF)** of the gamma distribution step by step.

---

### **1. Background**
The gamma distribution is defined by two parameters:
- **Shape parameter (\( k \))**: Controls the shape of the distribution.
- **Scale parameter (\( \theta \))**: Controls the spread of the distribution.

The gamma distribution is often used to model the sum of \( k \) independent exponential random variables, each with mean \( \theta \).

---

### **2. Derivation of the PDF**
To derive the PDF of the gamma distribution, we start with the properties of the exponential distribution and use the concept of convolution for sums of random variables.

#### **Step 1: PDF of an Exponential Distribution**
The exponential distribution with rate parameter \( \lambda = \frac{1}{\theta} \) has the PDF:
\[
f_X(x) = \frac{1}{\theta} e^{-x / \theta}, \quad x > 0.
\]

#### **Step 2: Sum of \( k \) Independent Exponential Random Variables**
Let \( X_1, X_2, \dots, X_k \) be independent exponential random variables, each with mean \( \theta \). The sum:
\[
Y = X_1 + X_2 + \dots + X_k
\]
follows a gamma distribution with shape parameter \( k \) and scale parameter \( \theta \).

#### **Step 3: Convolution of PDFs**
The PDF of the sum of independent random variables is the convolution of their individual PDFs. For \( k = 1 \), the PDF of \( Y \) is simply the exponential PDF:
\[
f_Y(y) = \frac{1}{\theta} e^{-y / \theta}, \quad y > 0.
\]

For \( k = 2 \), the PDF of \( Y = X_1 + X_2 \) is the convolution of two exponential PDFs:
\[
f_Y(y) = \int_0^y f_{X_1}(x) f_{X_2}(y - x) \, dx.
\]
Substitute the exponential PDFs:
\[
f_Y(y) = \int_0^y \frac{1}{\theta} e^{-x / \theta} \cdot \frac{1}{\theta} e^{-(y - x) / \theta} \, dx.
\]
Simplify the integrand:
\[
f_Y(y) = \frac{1}{\theta^2} e^{-y / \theta} \int_0^y 1 \, dx.
\]
Evaluate the integral:
\[
f_Y(y) = \frac{1}{\theta^2} e^{-y / \theta} \cdot y.
\]

For general \( k \), the convolution of \( k \) exponential PDFs leads to the gamma PDF.

#### **Step 4: Generalize to \( k \) Variables**
The PDF of the sum of \( k \) independent exponential random variables is:
\[
f_Y(y) = \frac{y^{k-1} e^{-y / \theta}}{\theta^k (k-1)!}, \quad y > 0.
\]
This is the PDF of the gamma distribution with shape parameter \( k \) and scale parameter \( \theta \).

#### **Step 5: Replace Factorial with Gamma Function**
The factorial \( (k-1)! \) can be generalized to non-integer values of \( k \) using the **gamma function**:
\[
\Gamma(k) = \int_0^\infty t^{k-1} e^{-t} \, dt.
\]
For integer \( k \), \( \Gamma(k) = (k-1)! \). Thus, the PDF of the gamma distribution is:
\[
f_Y(y) = \frac{y^{k-1} e^{-y / \theta}}{\theta^k \Gamma(k)}, \quad y > 0.
\]

---

### **3. Gamma PDF Formula**
The PDF of the gamma distribution with shape parameter \( k \) and scale parameter \( \theta \) is:
\[
f_Y(y) = \frac{y^{k-1} e^{-y / \theta}}{\theta^k \Gamma(k)}, \quad y > 0,
\]
where:
- \( k \): Shape parameter (\( k > 0 \)),
- \( \theta \): Scale parameter (\( \theta > 0 \)),
- \( \Gamma(k) \): Gamma function,
- \( y \): Real-valued random variable (\( y > 0 \)).

---

### **4. Special Cases**

#### **Exponential Distribution**
When \( k = 1 \), the gamma distribution reduces to the exponential distribution:
\[
f_Y(y) = \frac{1}{\theta} e^{-y / \theta}, \quad y > 0.
\]

#### **Chi-Squared Distribution**
When \( k = \nu / 2 \) and \( \theta = 2 \), the gamma distribution reduces to the chi-squared distribution with \( \nu \) degrees of freedom:
\[
f_Y(y) = \frac{y^{\nu/2 - 1} e^{-y / 2}}{2^{\nu/2} \Gamma(\nu/2)}, \quad y > 0.
\]

---

### **5. Summary**
The PDF of the gamma distribution is derived by:
1. Starting with the exponential distribution.
2. Using convolution to find the PDF of the sum of \( k \) independent exponential random variables.
3. Generalizing the factorial to the gamma function for non-integer values of \( k \).

The resulting PDF describes the probability density of the gamma distribution, which is widely used in statistics and probability.

The statement that **the factorial \( (k-1)! \) can be generalized to non-integer values of \( k \) using the gamma function** is a fundamental result in mathematics. The **gamma function** \( \Gamma(k) \) is a generalization of the factorial function to real (and complex) numbers. Let’s break this down step by step to understand why and how this works.

---

### **1. Factorial Function**
The factorial of a non-negative integer \( n \) is defined as:
\[
n! = n \cdot (n-1) \cdot (n-2) \cdots 2 \cdot 1.
\]
For example:
- \( 4! = 4 \cdot 3 \cdot 2 \cdot 1 = 24 \),
- \( 1! = 1 \),
- By convention, \( 0! = 1 \).

The factorial function is only defined for non-negative integers.

---

### **2. Gamma Function**
The **gamma function** \( \Gamma(k) \) is defined for all real (and complex) numbers \( k \) except for non-positive integers. It is defined by the integral:
\[
\Gamma(k) = \int_0^\infty t^{k-1} e^{-t} \, dt, \quad k > 0.
\]

#### **Key Properties of the Gamma Function**:
1. **Recurrence Relation**:
   \[
   \Gamma(k + 1) = k \Gamma(k).
   \]
   This property generalizes the factorial recurrence relation \( n! = n \cdot (n-1)! \).

2. **Factorial Connection**:
   For positive integers \( n \), the gamma function satisfies:
   \[
   \Gamma(n) = (n-1)!.
   \]
   For example:
   - \( \Gamma(4) = 3! = 6 \),
   - \( \Gamma(5) = 4! = 24 \).

3. **Extension to Non-Integer Values**:
   The gamma function is defined for all real numbers \( k > 0 \), not just integers. For example:
   - \( \Gamma(1/2) = \sqrt{\pi} \),
   - \( \Gamma(3/2) = \frac{1}{2} \sqrt{\pi} \).

---

### **3. Why the Gamma Function Generalizes the Factorial**
The gamma function \( \Gamma(k) \) generalizes the factorial function because:
1. It satisfies the same recurrence relation as the factorial:
   \[
   \Gamma(k + 1) = k \Gamma(k).
   \]
2. For positive integers \( n \), it matches the factorial:
   \[
   \Gamma(n) = (n-1)!.
   \]
3. It is defined for all real (and complex) numbers \( k > 0 \), allowing us to compute "factorials" of non-integer values.

---

### **4. Derivation of the Gamma Function**
The gamma function is derived from the integral:
\[
\Gamma(k) = \int_0^\infty t^{k-1} e^{-t} \, dt.
\]
This integral converges for all \( k > 0 \), and it generalizes the factorial function because:
- For \( k = 1 \):
  \[
  \Gamma(1) = \int_0^\infty t^{0} e^{-t} \, dt = \int_0^\infty e^{-t} \, dt = 1 = 0!.
  \]
- For \( k = 2 \):
  \[
  \Gamma(2) = \int_0^\infty t^{1} e^{-t} \, dt = \int_0^\infty t e^{-t} \, dt = 1 = 1!.
  \]
- For \( k = n + 1 \), integration by parts shows:
  \[
  \Gamma(n + 1) = n \Gamma(n),
  \]
  which matches the factorial recurrence relation.

---

### **5. Example: Gamma Function for Non-Integer Values**
The gamma function allows us to compute "factorials" of non-integer values. For example:
- \( \Gamma(1/2) = \sqrt{\pi} \),
- \( \Gamma(3/2) = \frac{1}{2} \sqrt{\pi} \),
- \( \Gamma(5/2) = \frac{3}{4} \sqrt{\pi} \).

These values are not factorials in the traditional sense, but they are consistent with the recurrence relation \( \Gamma(k + 1) = k \Gamma(k) \).

---

### **6. Summary**
The gamma function \( \Gamma(k) \) generalizes the factorial function to non-integer values of \( k \) because:
1. It satisfies the same recurrence relation as the factorial: \( \Gamma(k + 1) = k \Gamma(k) \).
2. For positive integers \( n \), it matches the factorial: \( \Gamma(n) = (n-1)! \).
3. It is defined for all real (and complex) numbers \( k > 0 \), allowing us to compute "factorials" of non-integer values.

The gamma function is a powerful tool in mathematics, statistics, and physics, enabling us to extend the concept of factorials beyond integers.

To prove that the **gamma function** satisfies the recurrence relation:

\[
\Gamma(k) = (k-1) \Gamma(k-1),
\]

for positive integers \( k \), we will use the definition of the gamma function and integration by parts. This recurrence relation is key to showing that the gamma function generalizes the factorial function.

---

### **1. Definition of the Gamma Function**
The gamma function is defined for \( k > 0 \) as:
\[
\Gamma(k) = \int_0^\infty t^{k-1} e^{-t} \, dt.
\]

---

### **2. Integration by Parts**
To prove the recurrence relation, we use **integration by parts**, which states:
\[
\int u \, dv = uv - \int v \, du.
\]

Let:
- \( u = t^{k-1} \), so \( du = (k-1) t^{k-2} \, dt \),
- \( dv = e^{-t} \, dt \), so \( v = -e^{-t} \).

---

### **3. Apply Integration by Parts**
Substitute \( u \), \( du \), \( dv \), and \( v \) into the integration by parts formula:
\[
\Gamma(k) = \int_0^\infty t^{k-1} e^{-t} \, dt = \left[ -t^{k-1} e^{-t} \right]_0^\infty + (k-1) \int_0^\infty t^{k-2} e^{-t} \, dt.
\]

---

### **4. Evaluate the Boundary Terms**
The boundary term \( \left[ -t^{k-1} e^{-t} \right]_0^\infty \) evaluates to:
- At \( t = 0 \): \( -0^{k-1} e^{-0} = 0 \),
- At \( t \to \infty \): \( -\infty^{k-1} e^{-\infty} = 0 \) (because \( e^{-t} \) decays faster than \( t^{k-1} \) grows).

Thus, the boundary term vanishes:
\[
\left[ -t^{k-1} e^{-t} \right]_0^\infty = 0.
\]

---

### **5. Simplify the Integral**
The remaining term is:
\[
\Gamma(k) = (k-1) \int_0^\infty t^{k-2} e^{-t} \, dt.
\]

By definition, the integral \( \int_0^\infty t^{k-2} e^{-t} \, dt \) is \( \Gamma(k-1) \). Therefore:
\[
\Gamma(k) = (k-1) \Gamma(k-1).
\]

---

### **6. Connection to Factorials**
For positive integers \( k \), we can repeatedly apply the recurrence relation:
\[
\Gamma(k) = (k-1) \Gamma(k-1),
\]
\[
\Gamma(k-1) = (k-2) \Gamma(k-2),
\]
\[
\vdots
\]
\[
\Gamma(2) = 1 \cdot \Gamma(1).
\]

Since \( \Gamma(1) = 1 \), we have:
\[
\Gamma(k) = (k-1) \cdot (k-2) \cdot \cdots \cdot 1 \cdot \Gamma(1) = (k-1)!.
\]

---

### **7. Summary**
The recurrence relation \( \Gamma(k) = (k-1) \Gamma(k-1) \) is proven using integration by parts. For positive integers \( k \), this relation shows that:
\[
\Gamma(k) = (k-1)!.
\]

Thus, the gamma function generalizes the factorial function to non-integer values of \( k \).
