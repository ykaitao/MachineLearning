The **Multinomial distribution** is a generalization of the **Binomial distribution** to more than two outcomes. It models the counts of outcomes in \( n \) independent trials, where each trial results in one of \( K \) possible outcomes. Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Multinomial Distribution**
The Multinomial distribution is characterized by:
- \( n \): The number of trials.
- \( K \): The number of possible outcomes.
- \( p_1, p_2, \dots, p_K \): The probabilities of each outcome, where \( p_k \geq 0 \) and \( \sum_{k=1}^K p_k = 1 \).

The random vector \( \mathbf{X} = (X_1, X_2, \dots, X_K) \) represents the counts of each outcome, where \( X_k \) is the number of times outcome \( k \) occurs in \( n \) trials. Note that \( \sum_{k=1}^K X_k = n \).

---

### **2. Derivation of the PMF**
The PMF of the Multinomial distribution gives the probability of observing a specific count vector \( \mathbf{X} = (x_1, x_2, \dots, x_K) \), where \( x_k \) is the number of times outcome \( k \) occurs.

#### **Step 1: Define the Outcomes**
Each trial results in one of \( K \) outcomes, with probabilities \( p_1, p_2, \dots, p_K \). The counts of the outcomes are \( X_1, X_2, \dots, X_K \), where \( \sum_{k=1}^K X_k = n \).

#### **Step 2: Multinomial Coefficient**
The number of ways to arrange \( n \) trials with counts \( x_1, x_2, \dots, x_K \) is given by the **multinomial coefficient**:
\[
\binom{n}{x_1, x_2, \dots, x_K} = \frac{n!}{x_1! x_2! \cdots x_K!}.
\]

#### **Step 3: Probability of a Specific Sequence**
The probability of a specific sequence of outcomes (e.g., outcome 1 occurs \( x_1 \) times, outcome 2 occurs \( x_2 \) times, etc.) is:
\[
p_1^{x_1} p_2^{x_2} \cdots p_K^{x_K}.
\]

#### **Step 4: Combine the Multinomial Coefficient and Probability**
The PMF of the Multinomial distribution is the product of the multinomial coefficient and the probability of a specific sequence:
\[
P(\mathbf{X} = (x_1, x_2, \dots, x_K)) = \binom{n}{x_1, x_2, \dots, x_K} p_1^{x_1} p_2^{x_2} \cdots p_K^{x_K}.
\]

#### **Step 5: Verify the PMF**
The PMF must satisfy two conditions:
1. **Non-negativity**: \( P(\mathbf{X} = (x_1, x_2, \dots, x_K)) \geq 0 \).
2. **Normalization**: The sum of probabilities over all possible count vectors is 1:
   \[
   \sum_{x_1 + x_2 + \dots + x_K = n} P(\mathbf{X} = (x_1, x_2, \dots, x_K)) = 1.
   \]

---

### **3. PMF Formula**
The PMF of the Multinomial distribution is:
\[
P(\mathbf{X} = (x_1, x_2, \dots, x_K)) = \frac{n!}{x_1! x_2! \cdots x_K!} p_1^{x_1} p_2^{x_2} \cdots p_K^{x_K},
\]
where:
- \( x_k \geq 0 \) and \( \sum_{k=1}^K x_k = n \),
- \( p_k \geq 0 \) and \( \sum_{k=1}^K p_k = 1 \).

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X_k] = n p_k \),
- **Variance**: \( \text{Var}(X_k) = n p_k (1 - p_k) \),
- **Covariance**: \( \text{Cov}(X_k, X_l) = -n p_k p_l \) for \( k \neq l \).

---

### **5. Use Case**
The Multinomial distribution is used to model:
- Counts of outcomes in categorical data (e.g., text data, survey responses),
- Multiclass classification problems in machine learning,
- Any experiment with multiple discrete outcomes.

---

### **6. Example**
Suppose a fair 6-sided die is rolled 10 times. The probability of observing counts \( \mathbf{X} = (2, 2, 2, 2, 1, 1) \) (i.e., each number 1–4 appears twice, and numbers 5–6 appear once) is:
\[
P(\mathbf{X} = (2, 2, 2, 2, 1, 1)) = \frac{10!}{2! 2! 2! 2! 1! 1!} \left(\frac{1}{6}\right)^2 \left(\frac{1}{6}\right)^2 \left(\frac{1}{6}\right)^2 \left(\frac{1}{6}\right)^2 \left(\frac{1}{6}\right)^1 \left(\frac{1}{6}\right)^1.
\]

---

### **7. Connection to the Binomial Distribution**
When \( K = 2 \), the Multinomial distribution reduces to the **Binomial distribution**:
\[
P(X_1 = x_1, X_2 = x_2) = \frac{n!}{x_1! x_2!} p_1^{x_1} p_2^{x_2},
\]
where \( x_1 + x_2 = n \) and \( p_1 + p_2 = 1 \).

---

### **Summary**
The PMF of the Multinomial distribution is:
\[
P(\mathbf{X} = (x_1, x_2, \dots, x_K)) = \frac{n!}{x_1! x_2! \cdots x_K!} p_1^{x_1} p_2^{x_2} \cdots p_K^{x_K}.
\]
It models counts of outcomes in categorical data and is foundational for many machine learning tasks. Let me know if you'd like further details!
