The **Hypergeometric distribution** is a discrete probability distribution that models the number of successes in a fixed number of draws from a finite population without replacement. It is widely used in quality control, sampling, and other fields. Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Hypergeometric Distribution**
The Hypergeometric distribution is characterized by three parameters:
- \( N \): The population size,
- \( K \): The number of successes in the population,
- \( n \): The number of draws (sample size).

The random variable \( X \) represents the number of successes in the sample. It takes values \( X = 0, 1, 2, \dots, \min(n, K) \).

---

### **2. Derivation of the PMF**
The PMF of the Hypergeometric distribution gives the probability of observing exactly \( k \) successes in \( n \) draws from a population of size \( N \) containing \( K \) successes. Here’s how it is derived:

#### **Step 1: Total Number of Possible Samples**
The total number of ways to draw \( n \) items from a population of size \( N \) is given by the binomial coefficient:
\[
\binom{N}{n}.
\]

#### **Step 2: Number of Ways to Choose \( k \) Successes**
The number of ways to choose \( k \) successes from the \( K \) successes in the population is:
\[
\binom{K}{k}.
\]

#### **Step 3: Number of Ways to Choose \( n - k \) Failures**
The number of ways to choose \( n - k \) failures from the \( N - K \) failures in the population is:
\[
\binom{N - K}{n - k}.
\]

#### **Step 4: Probability of \( k \) Successes in \( n \) Draws**
The probability of observing exactly \( k \) successes in \( n \) draws is the ratio of the number of favorable outcomes to the total number of possible outcomes:
\[
P(X = k) = \frac{\binom{K}{k} \binom{N - K}{n - k}}{\binom{N}{n}}.
\]

---

### **3. PMF Formula**
The PMF of the Hypergeometric distribution is:
\[
P(X = k) = \frac{\binom{K}{k} \binom{N - K}{n - k}}{\binom{N}{n}}, \quad k = \max(0, n + K - N), \dots, \min(n, K).
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = n \cdot \frac{K}{N} \),
- **Variance**: \( \text{Var}(X) = n \cdot \frac{K}{N} \cdot \frac{N - K}{N} \cdot \frac{N - n}{N - 1} \),
- **Support**: \( X \in \{\max(0, n + K - N), \dots, \min(n, K)\} \).

---

### **5. Use Case**
The Hypergeometric distribution is used to model:
- Sampling without replacement (e.g., quality control, lotteries),
- Experiments with finite populations,
- Situations where the probability of success changes with each draw.

---

### **6. Example**
Suppose a population of \( N = 20 \) items contains \( K = 7 \) defective items. If \( n = 5 \) items are drawn without replacement, the probability of observing exactly \( k = 2 \) defective items is:
\[
P(X = 2) = \frac{\binom{7}{2} \binom{13}{3}}{\binom{20}{5}}.
\]
Calculate:
\[
\binom{7}{2} = 21, \quad \binom{13}{3} = 286, \quad \binom{20}{5} = 15504.
\]
Thus:
\[
P(X = 2) = \frac{21 \cdot 286}{15504} \approx 0.387.
\]

---

### **7. Connection to the Binomial Distribution**
When the population size \( N \) is large compared to the sample size \( n \), the Hypergeometric distribution approximates the **Binomial distribution**:
\[
P(X = k) \approx \binom{n}{k} \left(\frac{K}{N}\right)^k \left(1 - \frac{K}{N}\right)^{n - k}.
\]

---

### **Summary**
The PMF of the Hypergeometric distribution is:
\[
P(X = k) = \frac{\binom{K}{k} \binom{N - K}{n - k}}{\binom{N}{n}}, \quad k = \max(0, n + K - N), \dots, \min(n, K).
\]
It models the number of successes in a sample drawn without replacement from a finite population and is widely used in probability and statistics. Let me know if you'd like further details!
