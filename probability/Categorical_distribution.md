The **Categorical distribution** is a generalization of the **Bernoulli distribution** to more than two outcomes. It models a random experiment with \( K \) possible discrete outcomes, each with its own probability. Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Categorical Distribution**
The Categorical distribution is characterized by:
- \( K \): The number of possible outcomes.
- \( p_1, p_2, \dots, p_K \): The probabilities of each outcome, where \( p_k \geq 0 \) and \( \sum_{k=1}^K p_k = 1 \).

The random variable \( X \) takes on values \( 1, 2, \dots, K \), where \( X = k \) corresponds to the \( k \)-th outcome.

---

### **2. Derivation of the PMF**
The PMF of a discrete random variable \( X \) gives the probability that \( X \) takes on a specific value. For the Categorical distribution, the PMF is defined as:
\[
P(X = k) = p_k, \quad k = 1, 2, \dots, K.
\]

#### **Step 1: Define the Outcomes**
The Categorical random variable \( X \) has \( K \) possible outcomes:
- \( X = 1 \) with probability \( p_1 \),
- \( X = 2 \) with probability \( p_2 \),
- \( \vdots \)
- \( X = K \) with probability \( p_K \).

#### **Step 2: Write the PMF**
The PMF assigns a probability \( p_k \) to each outcome \( k \):
\[
P(X = k) = p_k, \quad k = 1, 2, \dots, K.
\]

#### **Step 3: Verify the PMF**
The PMF must satisfy two conditions:
1. **Non-negativity**: \( p_k \geq 0 \) for all \( k \).
2. **Normalization**: \( \sum_{k=1}^K p_k = 1 \).

These conditions ensure that the PMF is a valid probability distribution.

---

### **3. PMF Formula**
The PMF of the Categorical distribution is:
\[
P(X = k) = p_k, \quad k = 1, 2, \dots, K.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = \sum_{k=1}^K k \cdot p_k \),
- **Variance**: \( \text{Var}(X) = \sum_{k=1}^K (k - \mathbb{E}[X])^2 \cdot p_k \),
- **Support**: \( X \in \{1, 2, \dots, K\} \).

---

### **5. Use Case**
The Categorical distribution is used to model:
- Multiclass classification problems in machine learning,
- Discrete outcomes with more than two possibilities (e.g., rolling a die, selecting a category).

---

### **6. Example**
Suppose a random variable \( X \) represents the outcome of rolling a fair 6-sided die. The PMF of the Categorical distribution for this experiment is:
\[
P(X = k) = \frac{1}{6}, \quad k = 1, 2, \dots, 6.
\]

---

### **7. Connection to One-Hot Encoding**
In machine learning, the Categorical distribution is often represented using **one-hot encoding**. If \( X = k \), the one-hot encoded vector \( \mathbf{y} \) is:
\[
\mathbf{y} = (0, \dots, 0, 1, 0, \dots, 0),
\]
where the \( k \)-th element is 1, and all other elements are 0. The PMF can then be written as:
\[
P(\mathbf{y}) = \prod_{k=1}^K p_k^{y_k},
\]
where \( y_k \) is the \( k \)-th element of \( \mathbf{y} \).

---

### **Summary**
The PMF of the Categorical distribution is:
\[
P(X = k) = p_k, \quad k = 1, 2, \dots, K.
\]
It models discrete outcomes with more than two possibilities and is foundational for multiclass classification and other machine learning tasks. Let me know if you'd like further details!
