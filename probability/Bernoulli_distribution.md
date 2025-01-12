The **Bernoulli distribution** is one of the simplest discrete probability distributions. It models a random experiment with two possible outcomes: **success** (often coded as 1) and **failure** (often coded as 0). Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Bernoulli Distribution**
The Bernoulli distribution is characterized by a single parameter:
- \( p \): The probability of success (\( 0 \leq p \leq 1 \)).

The random variable \( X \) takes on two values:
- \( X = 1 \) (success) with probability \( p \),
- \( X = 0 \) (failure) with probability \( 1-p \).

---

### **2. Derivation of the PMF**
The PMF of a discrete random variable \( X \) gives the probability that \( X \) takes on a specific value. For the Bernoulli distribution, the PMF is defined as:
\[
P(X = x) = 
\begin{cases}
p & \text{if } x = 1, \\
1-p & \text{if } x = 0.
\end{cases}
\]

#### **Step 1: Define the Outcomes**
The Bernoulli random variable \( X \) has two possible outcomes:
- \( X = 1 \): Success, with probability \( p \),
- \( X = 0 \): Failure, with probability \( 1-p \).

#### **Step 2: Write the PMF**
The PMF can be written compactly using an indicator function or as a single expression:
\[
P(X = x) = p^x (1-p)^{1-x}, \quad x \in \{0, 1\}.
\]

#### **Step 3: Verify the PMF**
- For \( x = 1 \):
  \[
  P(X = 1) = p^1 (1-p)^{1-1} = p.
  \]
- For \( x = 0 \):
  \[
  P(X = 0) = p^0 (1-p)^{1-0} = 1-p.
  \]

Thus, the PMF correctly assigns probabilities to the two outcomes.

---

### **3. PMF Formula**
The PMF of the Bernoulli distribution is:
\[
P(X = x) = p^x (1-p)^{1-x}, \quad x \in \{0, 1\}.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = p \),
- **Variance**: \( \text{Var}(X) = p(1-p) \),
- **Support**: \( X \in \{0, 1\} \).

---

### **5. Use Case**
The Bernoulli distribution is used to model:
- Binary outcomes (e.g., coin flips, yes/no decisions),
- Binary classification problems in machine learning,
- Any experiment with two possible outcomes.

---

### **6. Example**
Suppose a biased coin has a probability \( p = 0.6 \) of landing heads. The PMF of the Bernoulli distribution for this experiment is:
\[
P(X = x) = 
\begin{cases}
0.6 & \text{if } x = 1, \\
0.4 & \text{if } x = 0.
\end{cases}
\]

---

### **Summary**
The PMF of the Bernoulli distribution is:
\[
P(X = x) = p^x (1-p)^{1-x}, \quad x \in \{0, 1\}.
\]
It models binary outcomes and is foundational for more complex distributions like the binomial distribution. Let me know if you'd like further details!
