The **Negative Binomial distribution** is a discrete probability distribution that models the number of failures before achieving a specified number of successes in a sequence of independent Bernoulli trials. It is widely used in reliability engineering, queuing theory, and other fields. Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Negative Binomial Distribution**
The Negative Binomial distribution is characterized by two parameters:
- \( r \): The number of successes (\( r \geq 1 \)),
- \( p \): The probability of success in a single trial (\( 0 < p \leq 1 \)).

The random variable \( X \) represents the number of failures before achieving \( r \) successes. It takes values \( X = 0, 1, 2, \dots \).

---

### **2. Derivation of the PMF**
The PMF of the Negative Binomial distribution gives the probability of observing \( k \) failures before achieving \( r \) successes. Here’s how it is derived:

#### **Step 1: Define the Trials**
Each trial is an independent Bernoulli trial with:
- Probability of success: \( p \),
- Probability of failure: \( 1 - p \).

#### **Step 2: Sequence of Trials**
To achieve \( r \) successes with \( k \) failures:
- The last trial must be a success (to ensure exactly \( r \) successes),
- The first \( r + k - 1 \) trials consist of \( r - 1 \) successes and \( k \) failures.

#### **Step 3: Number of Ways to Arrange the Trials**
The number of ways to arrange \( r - 1 \) successes and \( k \) failures in the first \( r + k - 1 \) trials is given by the binomial coefficient:
\[
\binom{r + k - 1}{r - 1} = \binom{r + k - 1}{k}.
\]

#### **Step 4: Probability of a Specific Sequence**
The probability of a specific sequence with \( r \) successes and \( k \) failures is:
\[
p^r (1-p)^k.
\]

#### **Step 5: Combine the Number of Arrangements and Probability**
The PMF of the Negative Binomial distribution is the product of the number of arrangements and the probability of a specific sequence:
\[
P(X = k) = \binom{r + k - 1}{k} p^r (1-p)^k.
\]

---

### **3. PMF Formula**
The PMF of the Negative Binomial distribution is:
\[
P(X = k) = \binom{r + k - 1}{k} p^r (1-p)^k, \quad k = 0, 1, 2, \dots.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = \frac{r (1-p)}{p} \),
- **Variance**: \( \text{Var}(X) = \frac{r (1-p)}{p^2} \),
- **Support**: \( X \in \{0, 1, 2, \dots\} \).

---

### **5. Use Case**
The Negative Binomial distribution is used to model:
- The number of failures before achieving a specified number of successes (e.g., number of trials until a machine fails \( r \) times),
- Overdispersed count data (where the variance exceeds the mean),
- Queuing systems and reliability analysis.

---

### **6. Example**
Suppose a biased coin has a probability \( p = 0.3 \) of landing heads. The probability of observing 4 tails before achieving 3 heads is:
\[
P(X = 4) = \binom{3 + 4 - 1}{4} (0.3)^3 (0.7)^4 = \binom{6}{4} (0.3)^3 (0.7)^4.
\]
Calculate:
\[
\binom{6}{4} = 15, \quad (0.3)^3 = 0.027, \quad (0.7)^4 = 0.2401.
\]
Thus:
\[
P(X = 4) = 15 \cdot 0.027 \cdot 0.2401 \approx 0.0972.
\]

---

### **7. Connection to the Geometric Distribution**
When \( r = 1 \), the Negative Binomial distribution reduces to the **Geometric distribution**:
\[
P(X = k) = p (1-p)^k, \quad k = 0, 1, 2, \dots.
\]

---

### **Summary**
The PMF of the Negative Binomial distribution is:
\[
P(X = k) = \binom{r + k - 1}{k} p^r (1-p)^k, \quad k = 0, 1, 2, \dots.
\]
It models the number of failures before achieving a specified number of successes and is widely used in probability and statistics. Let me know if you'd like further details!
