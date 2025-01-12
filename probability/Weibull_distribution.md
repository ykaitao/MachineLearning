The **Weibull distribution** is a continuous probability distribution widely used in reliability engineering, survival analysis, and extreme value theory. It is flexible and can model a variety of data shapes, including increasing, decreasing, and constant failure rates. Let’s derive its **probability density function (PDF)** step by step.

---

### **1. Definition of the Weibull Distribution**
The Weibull distribution is characterized by two parameters:
- **Shape parameter (\( k \))**: Controls the shape of the distribution (\( k > 0 \)).
- **Scale parameter (\( \lambda \))**: Controls the scale of the distribution (\( \lambda > 0 \)).

The PDF of the Weibull distribution is defined for \( x \geq 0 \).

---

### **2. Derivation of the PDF**
The PDF of the Weibull distribution can be derived from its **cumulative distribution function (CDF)**. Here’s how:

#### **Step 1: Define the CDF**
The CDF of the Weibull distribution is:
\[
F(x) = 1 - \exp\left(-\left(\frac{x}{\lambda}\right)^k\right), \quad x \geq 0.
\]

#### **Step 2: Derive the PDF**
The PDF is the derivative of the CDF with respect to \( x \):
\[
f(x) = \frac{d}{dx} F(x).
\]
Differentiate the CDF:
\[
f(x) = \frac{d}{dx} \left[ 1 - \exp\left(-\left(\frac{x}{\lambda}\right)^k\right) \right].
\]
Using the chain rule:
\[
f(x) = -\exp\left(-\left(\frac{x}{\lambda}\right)^k\right) \cdot \frac{d}{dx} \left[ -\left(\frac{x}{\lambda}\right)^k \right].
\]
Simplify the derivative:
\[
\frac{d}{dx} \left[ -\left(\frac{x}{\lambda}\right)^k \right] = -k \left(\frac{x}{\lambda}\right)^{k-1} \cdot \frac{1}{\lambda}.
\]
Thus:
\[
f(x) = \exp\left(-\left(\frac{x}{\lambda}\right)^k\right) \cdot k \left(\frac{x}{\lambda}\right)^{k-1} \cdot \frac{1}{\lambda}.
\]

#### **Step 3: Simplify the PDF**
Combine the terms to write the PDF:
\[
f(x) = \frac{k}{\lambda} \left(\frac{x}{\lambda}\right)^{k-1} \exp\left(-\left(\frac{x}{\lambda}\right)^k\right), \quad x \geq 0.
\]

---

### **3. PDF Formula**
The PDF of the Weibull distribution with shape parameter \( k \) and scale parameter \( \lambda \) is:
\[
f(x) = \frac{k}{\lambda} \left(\frac{x}{\lambda}\right)^{k-1} \exp\left(-\left(\frac{x}{\lambda}\right)^k\right), \quad x \geq 0.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = \lambda \Gamma\left(1 + \frac{1}{k}\right) \),
- **Variance**: \( \text{Var}(X) = \lambda^2 \left[ \Gamma\left(1 + \frac{2}{k}\right) - \Gamma^2\left(1 + \frac{1}{k}\right) \right] \),
- **Support**: \( X \geq 0 \).

Here, \( \Gamma(\cdot) \) is the gamma function.

---

### **5. Use Case**
The Weibull distribution is used to model:
- Failure times in reliability engineering,
- Wind speed distributions in meteorology,
- Survival times in medical research.

---

### **6. Example**
Suppose \( X \) follows a Weibull distribution with \( k = 2 \) and \( \lambda = 10 \). The PDF of \( X \) is:
\[
f(x) = \frac{2}{10} \left(\frac{x}{10}\right)^{2-1} \exp\left(-\left(\frac{x}{10}\right)^2\right), \quad x \geq 0.
\]

---

### **7. Special Cases**
- **Exponential Distribution**: When \( k = 1 \), the Weibull distribution reduces to the exponential distribution:
  \[
  f(x) = \frac{1}{\lambda} \exp\left(-\frac{x}{\lambda}\right).
  \]
- **Rayleigh Distribution**: When \( k = 2 \), the Weibull distribution reduces to the Rayleigh distribution.

---

### **Summary**
The PDF of the Weibull distribution is:
\[
f(x) = \frac{k}{\lambda} \left(\frac{x}{\lambda}\right)^{k-1} \exp\left(-\left(\frac{x}{\lambda}\right)^k\right), \quad x \geq 0.
\]
It is a flexible distribution used to model a wide range of phenomena. Let me know if you'd like further details!
