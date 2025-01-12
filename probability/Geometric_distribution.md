The **Geometric distribution** is a discrete probability distribution that models the number of trials needed to achieve the first success in a sequence of independent Bernoulli trials. It is widely used in reliability engineering, queuing theory, and other fields. Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Geometric Distribution**
The Geometric distribution is characterized by a single parameter:
- \( p \): The probability of success in a single trial (\( 0 < p \leq 1 \)).

The random variable \( X \) represents the number of trials needed to achieve the first success. It takes values \( X = 1, 2, 3, \dots \).

---

### **2. Derivation of the PMF**
The PMF of the Geometric distribution gives the probability that the first success occurs on the \( k \)-th trial. Here’s how it is derived:

#### **Step 1: Define the Trials**
Each trial is an independent Bernoulli trial with:
- Probability of success: \( p \),
- Probability of failure: \( 1 - p \).

#### **Step 2: First Success on the \( k \)-th Trial**
For the first success to occur on the \( k \)-th trial:
- The first \( k-1 \) trials must be failures,
- The \( k \)-th trial must be a success.

#### **Step 3: Probability of \( k-1 \) Failures Followed by 1 Success**
The probability of \( k-1 \) failures is \( (1-p)^{k-1} \), and the probability of 1 success is \( p \). Since the trials are independent, the probability of the sequence is:
\[
P(X = k) = (1-p)^{k-1} p.
\]

#### **Step 4: Verify the PMF**
The PMF must satisfy two conditions:
1. **Non-negativity**: \( P(X = k) \geq 0 \) for all \( k \).
2. **Normalization**: The sum of probabilities over all possible values of \( k \) is 1:
   \[
   \sum_{k=1}^\infty P(X = k) = \sum_{k=1}^\infty (1-p)^{k-1} p = 1.
   \]
   This is a geometric series with sum:
   \[
   p \sum_{k=0}^\infty (1-p)^k = p \cdot \frac{1}{1 - (1-p)} = p \cdot \frac{1}{p} = 1.
   \]

---

### **3. PMF Formula**
The PMF of the Geometric distribution is:
\[
P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, \dots.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = \frac{1}{p} \),
- **Variance**: \( \text{Var}(X) = \frac{1-p}{p^2} \),
- **Support**: \( X \in \{1, 2, 3, \dots\} \).

---

### **5. Use Case**
The Geometric distribution is used to model:
- The number of trials until the first success (e.g., number of coin flips until the first heads),
- Waiting times in queuing systems,
- Reliability analysis (e.g., time until the first failure).

---

### **6. Example**
Suppose a biased coin has a probability \( p = 0.2 \) of landing heads. The probability that the first heads occurs on the 3rd toss is:
\[
P(X = 3) = (1 - 0.2)^{3-1} \cdot 0.2 = (0.8)^2 \cdot 0.2 = 0.128.
\]

---

### **7. Alternative Parameterization**
Sometimes the Geometric distribution is defined as the number of **failures** before the first success. In this case:
- The random variable \( Y = X - 1 \) represents the number of failures,
- The PMF becomes:
  \[
  P(Y = k) = (1-p)^k p, \quad k = 0, 1, 2, \dots.
  \]

---

### **Summary**
The PMF of the Geometric distribution is:
\[
P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, \dots.
\]
It models the number of trials needed to achieve the first success and is widely used in probability and statistics. Let me know if you'd like further details!
