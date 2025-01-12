The **Log-Normal distribution** is a continuous probability distribution of a random variable whose logarithm is normally distributed. It is widely used in finance, biology, and other fields to model variables that are positively skewed. Let’s derive its **probability density function (PDF)** step by step.

---

### **1. Definition of the Log-Normal Distribution**
A random variable \( X \) is said to follow a Log-Normal distribution if its natural logarithm \( \ln X \) follows a normal distribution. Formally:
\[
\ln X \sim N(\mu, \sigma^2),
\]
where:
- \( \mu \): The mean of \( \ln X \),
- \( \sigma^2 \): The variance of \( \ln X \).

The Log-Normal distribution is defined for \( x > 0 \).

---

### **2. Derivation of the PDF**
To derive the PDF of the Log-Normal distribution, we start with the normal distribution of \( \ln X \) and use the change of variables technique.

#### **Step 1: Normal Distribution of \( \ln X \)**
The PDF of \( \ln X \) is given by the normal distribution:
\[
f_{\ln X}(y) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp\left(-\frac{(y - \mu)^2}{2\sigma^2}\right), \quad y \in \mathbb{R}.
\]

#### **Step 2: Change of Variables**
Let \( y = \ln x \), so \( x = e^y \). The relationship between the PDFs of \( X \) and \( \ln X \) is:
\[
f_X(x) = f_{\ln X}(y) \cdot \left| \frac{dy}{dx} \right|.
\]
Compute the derivative:
\[
\frac{dy}{dx} = \frac{d}{dx} (\ln x) = \frac{1}{x}.
\]
Thus:
\[
\left| \frac{dy}{dx} \right| = \frac{1}{x}.
\]

#### **Step 3: Substitute into the PDF**
Substitute \( y = \ln x \) and \( \left| \frac{dy}{dx} \right| = \frac{1}{x} \) into the PDF of \( \ln X \):
\[
f_X(x) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp\left(-\frac{(\ln x - \mu)^2}{2\sigma^2}\right) \cdot \frac{1}{x}.
\]

#### **Step 4: Simplify the PDF**
The PDF of the Log-Normal distribution is:
\[
f_X(x) = \frac{1}{x \sqrt{2\pi \sigma^2}} \exp\left(-\frac{(\ln x - \mu)^2}{2\sigma^2}\right), \quad x > 0.
\]

---

### **3. PDF Formula**
The PDF of the Log-Normal distribution with parameters \( \mu \) and \( \sigma^2 \) is:
\[
f_X(x) = \frac{1}{x \sqrt{2\pi \sigma^2}} \exp\left(-\frac{(\ln x - \mu)^2}{2\sigma^2}\right), \quad x > 0.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = e^{\mu + \sigma^2 / 2} \),
- **Variance**: \( \text{Var}(X) = e^{2\mu + \sigma^2} (e^{\sigma^2} - 1) \),
- **Support**: \( X > 0 \).

---

### **5. Use Case**
The Log-Normal distribution is used to model:
- Variables that are positively skewed (e.g., income, stock prices),
- Quantities that are the product of many small independent factors (e.g., particle sizes, biological measurements),
- Failure times in reliability analysis.

---

### **6. Example**
Suppose \( \ln X \sim N(0, 1) \). The PDF of \( X \) is:
\[
f_X(x) = \frac{1}{x \sqrt{2\pi}} \exp\left(-\frac{(\ln x)^2}{2}\right), \quad x > 0.
\]

---

### **7. Connection to the Normal Distribution**
The Log-Normal distribution is closely related to the normal distribution:
- If \( \ln X \sim N(\mu, \sigma^2) \), then \( X \) follows a Log-Normal distribution.
- Conversely, if \( X \) is Log-Normally distributed, then \( \ln X \) is normally distributed.

---

### **Summary**
The PDF of the Log-Normal distribution is:
\[
f_X(x) = \frac{1}{x \sqrt{2\pi \sigma^2}} \exp\left(-\frac{(\ln x - \mu)^2}{2\sigma^2}\right), \quad x > 0.
\]
It models positively skewed variables and is widely used in various fields. Let me know if you'd like further details!
