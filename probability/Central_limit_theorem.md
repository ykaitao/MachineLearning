The **Central Limit Theorem (CLT)** is one of the most fundamental results in probability and statistics. It states that the sum (or average) of a large number of independent and identically distributed (i.i.d.) random variables, each with finite mean and variance, will approximately follow a **normal distribution**, regardless of the underlying distribution of the individual variables. The CLT does not directly provide a PDF formula, but it explains why the normal distribution arises as the limiting distribution. Let’s explore the intuition and mathematics behind the CLT.

---

### **1. Statement of the Central Limit Theorem**
Let \( X_1, X_2, \dots, X_n \) be \( n \) i.i.d. random variables with:
- Mean \( \mu = \mathbb{E}[X_i] \),
- Variance \( \sigma^2 = \text{Var}(X_i) \).

Define the **sample mean** as:
\[
\bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i.
\]

The Central Limit Theorem states that, as \( n \to \infty \), the distribution of \( \bar{X}_n \) converges to a normal distribution with mean \( \mu \) and variance \( \frac{\sigma^2}{n} \). Mathematically:
\[
\sqrt{n} \left( \bar{X}_n - \mu \right) \xrightarrow{d} N(0, \sigma^2),
\]
where \( \xrightarrow{d} \) denotes convergence in distribution, and \( N(0, \sigma^2) \) is the normal distribution with mean 0 and variance \( \sigma^2 \).

---

### **2. Intuition Behind the CLT**
The CLT arises because:
1. The sum of many small, independent random effects tends to be normally distributed.
2. The normal distribution is stable under addition, meaning the sum of independent normal random variables is also normal.
3. The CLT holds regardless of the shape of the original distribution, as long as the random variables are i.i.d. with finite mean and variance.

---

### **3. Derivation of the CLT**
The CLT can be derived using the **characteristic function** (or moment-generating function) of the random variables. Here’s a sketch of the derivation:

#### **Step 1: Standardize the Random Variables**
Define the standardized random variable:
\[
Z_n = \frac{\bar{X}_n - \mu}{\sigma / \sqrt{n}}.
\]
The CLT states that \( Z_n \xrightarrow{d} N(0, 1) \) as \( n \to \infty \).

#### **Step 2: Characteristic Function of \( Z_n \)**
The characteristic function of \( Z_n \) is:
\[
\phi_{Z_n}(t) = \mathbb{E}\left[ e^{it Z_n} \right],
\]
where \( i = \sqrt{-1} \) is the imaginary unit.

#### **Step 3: Expand the Characteristic Function**
Using the Taylor expansion of \( e^{it Z_n} \), we can write:
\[
\phi_{Z_n}(t) = \mathbb{E}\left[ 1 + it Z_n - \frac{t^2 Z_n^2}{2} + \cdots \right].
\]
For large \( n \), the higher-order terms become negligible, and the characteristic function simplifies to:
\[
\phi_{Z_n}(t) \approx 1 - \frac{t^2}{2n} \mathbb{E}[Z_n^2].
\]

#### **Step 4: Compute \( \mathbb{E}[Z_n^2] \)**
Since \( Z_n \) is standardized, \( \mathbb{E}[Z_n] = 0 \) and \( \text{Var}(Z_n) = 1 \). Thus:
\[
\mathbb{E}[Z_n^2] = \text{Var}(Z_n) + (\mathbb{E}[Z_n])^2 = 1.
\]

#### **Step 5: Characteristic Function of the Normal Distribution**
The characteristic function of a standard normal random variable \( Z \sim N(0, 1) \) is:
\[
\phi_Z(t) = e^{-t^2 / 2}.
\]

#### **Step 6: Convergence to the Normal Distribution**
As \( n \to \infty \), the characteristic function of \( Z_n \) converges to the characteristic function of \( Z \):
\[
\phi_{Z_n}(t) \approx 1 - \frac{t^2}{2n} \to e^{-t^2 / 2}.
\]
This shows that \( Z_n \xrightarrow{d} N(0, 1) \).

---

### **4. PDF of the Limiting Normal Distribution**
The PDF of the standard normal distribution \( N(0, 1) \) is:
\[
f_Z(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2 / 2}.
\]

For the sample mean \( \bar{X}_n \), the limiting distribution is \( N(\mu, \frac{\sigma^2}{n}) \), and its PDF is:
\[
f_{\bar{X}_n}(x) = \frac{1}{\sqrt{2\pi (\sigma^2 / n)}} \exp\left( -\frac{(x - \mu)^2}{2 (\sigma^2 / n)} \right).
\]

---

### **5. Summary**
The Central Limit Theorem explains why the normal distribution arises as the limiting distribution of the sum (or average) of a large number of i.i.d. random variables. The key steps in the derivation are:
1. Standardizing the random variables.
2. Using the characteristic function to show convergence to the normal distribution.
3. Recognizing that the normal distribution is stable under addition.

The PDF of the limiting normal distribution is:
\[
f_{\bar{X}_n}(x) = \frac{1}{\sqrt{2\pi (\sigma^2 / n)}} \exp\left( -\frac{(x - \mu)^2}{2 (\sigma^2 / n)} \right).
\]
