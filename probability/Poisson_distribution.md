The **Poisson Distribution** is a discrete probability distribution that models the number of events occurring in a fixed interval of time or space, given a constant average rate of occurrence. Let’s derive the **probability mass function (PMF)** for the Poisson distribution step by step.

---

### **1. Assumptions of the Poisson Distribution**
The Poisson distribution is based on the following assumptions:
1. Events occur independently of each other.
2. The average rate of occurrence (\( \lambda \)) is constant.
3. The probability of more than one event occurring in an infinitesimally small interval is negligible.

---

### **2. Derivation of the Poisson PMF**
The PMF of the Poisson distribution gives the probability of observing exactly \( k \) events in a fixed interval. To derive it, we start with the **Binomial distribution** and take the limit as the number of trials \( n \) approaches infinity.

#### **Step 1: Start with the Binomial Distribution**
The Binomial PMF is:
\[
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
\]
where:
- \( n \): Number of trials.
- \( k \): Number of successes.
- \( p \): Probability of success in a single trial.

#### **Step 2: Relate \( p \) to \( \lambda \)**
In the Poisson distribution, the average rate of occurrence is \( \lambda \). If we divide the interval into \( n \) sub-intervals, the probability of an event occurring in each sub-interval is:
\[
p = \frac{\lambda}{n}
\]

#### **Step 3: Substitute \( p \) into the Binomial PMF**
Substitute \( p = \frac{\lambda}{n} \) into the Binomial PMF:
\[
P(X = k) = \binom{n}{k} \left(\frac{\lambda}{n}\right)^k \left(1 - \frac{\lambda}{n}\right)^{n-k}
\]

#### **Step 4: Take the Limit as \( n \to \infty \)**
To derive the Poisson PMF, we take the limit of the Binomial PMF as \( n \to \infty \):
\[
P(X = k) = \lim_{n \to \infty} \binom{n}{k} \left(\frac{\lambda}{n}\right)^k \left(1 - \frac{\lambda}{n}\right)^{n-k}
\]

#### **Step 5: Simplify the Limit**
Break the limit into three parts:
1. **Binomial Coefficient**:
   \[
   \binom{n}{k} = \frac{n!}{k!(n-k)!} \approx \frac{n^k}{k!} \quad \text{(for large \( n \))}
   \]
2. **First Term**:
   \[
   \left(\frac{\lambda}{n}\right)^k = \frac{\lambda^k}{n^k}
   \]
3. **Second Term**:
   \[
   \left(1 - \frac{\lambda}{n}\right)^{n-k} \approx \left(1 - \frac{\lambda}{n}\right)^n \quad \text{(for large \( n \))}
   \]
   Using the limit definition of the exponential function:
   \[
   \lim_{n \to \infty} \left(1 - \frac{\lambda}{n}\right)^n = e^{-\lambda}
   \]

Combine these results:
\[
P(X = k) = \lim_{n \to \infty} \frac{n^k}{k!} \cdot \frac{\lambda^k}{n^k} \cdot e^{-\lambda}
\]
\[
P(X = k) = \frac{\lambda^k}{k!} e^{-\lambda}
\]

---

### **3. Poisson PMF Formula**
The PMF of the Poisson distribution is:
\[
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \dots
\]
where:
- \( \lambda \): Average rate of occurrence (mean number of events in the interval).
- \( k \): Number of events.
- \( e \): Base of the natural logarithm (\( e \approx 2.71828 \)).

---

### **4. Poisson PDF**
The Poisson distribution is a **discrete distribution**, so it does not have a probability density function (PDF). Instead, it has a **probability mass function (PMF)** as derived above. The term "PDF" is typically used for continuous distributions, while "PMF" is used for discrete distributions.

---

### **5. Example**
Suppose the average number of emails you receive per hour is \( \lambda = 5 \). What is the probability of receiving exactly 3 emails in the next hour?

Using the Poisson PMF:
\[
P(X = 3) = \frac{5^3 e^{-5}}{3!}
\]
\[
P(X = 3) = \frac{125 \cdot e^{-5}}{6}
\]
\[
P(X = 3) \approx \frac{125 \cdot 0.0067}{6} \approx 0.140
\]

So, the probability of receiving exactly 3 emails in the next hour is approximately 14.0%.

---

### **Summary**
- The **PMF of the Poisson distribution** is derived by taking the limit of the Binomial PMF as the number of trials \( n \) approaches infinity.
- The formula is:
  \[
  P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \dots
  \]
- The Poisson distribution is discrete, so it has a PMF, not a PDF.

