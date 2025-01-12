The **Uniform distribution** is a continuous probability distribution where all outcomes in a given interval are equally likely. It is characterized by its simplicity and is often used in simulations, random sampling, and as a prior in Bayesian inference. Let’s derive its **probability density function (PDF)** step by step.

---

### **1. Definition of the Uniform Distribution**
The Uniform distribution is defined over an interval \([a, b]\), where:
- \( a \): The lower bound of the interval,
- \( b \): The upper bound of the interval (\( b > a \)).

The PDF of the Uniform distribution is constant over the interval \([a, b]\) and zero outside this interval.

---

### **2. Derivation of the PDF**
The PDF of a continuous random variable \( X \) gives the relative likelihood of \( X \) taking on a specific value. For the Uniform distribution, the PDF is derived as follows:

#### **Step 1: Define the Interval**
The random variable \( X \) takes values in the interval \([a, b]\). The probability density must be constant over this interval and zero elsewhere.

#### **Step 2: Normalize the PDF**
The total area under the PDF must equal 1 (normalization condition):
\[
\int_{-\infty}^\infty f(x) \, dx = 1.
\]
Since \( f(x) = 0 \) outside \([a, b]\), the integral simplifies to:
\[
\int_a^b f(x) \, dx = 1.
\]
Let \( f(x) = c \) (a constant) over \([a, b]\). Then:
\[
\int_a^b c \, dx = c(b - a) = 1.
\]
Solve for \( c \):
\[
c = \frac{1}{b - a}.
\]

#### **Step 3: Write the PDF**
The PDF of the Uniform distribution is:
\[
f(x) = 
\begin{cases}
\frac{1}{b - a} & \text{if } a \leq x \leq b, \\
0 & \text{otherwise}.
\end{cases}
\]

---

### **3. PDF Formula**
The PDF of the Uniform distribution over \([a, b]\) is:
\[
f(x) = 
\begin{cases}
\frac{1}{b - a} & \text{if } a \leq x \leq b, \\
0 & \text{otherwise}.
\end{cases}
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[X] = \frac{a + b}{2} \),
- **Variance**: \( \text{Var}(X) = \frac{(b - a)^2}{12} \),
- **Support**: \( X \in [a, b] \).

---

### **5. Use Case**
The Uniform distribution is used to model:
- Random variables with no preference for any value within a range (e.g., random number generation),
- Prior distributions in Bayesian inference when no prior information is available,
- Quantization errors in digital signal processing.

---

### **6. Example**
Suppose \( X \) is uniformly distributed over the interval \([0, 10]\). The PDF of \( X \) is:
\[
f(x) = 
\begin{cases}
\frac{1}{10} & \text{if } 0 \leq x \leq 10, \\
0 & \text{otherwise}.
\end{cases}
\]

---

### **7. Special Case: Standard Uniform Distribution**
When \( a = 0 \) and \( b = 1 \), the Uniform distribution is called the **Standard Uniform distribution**. Its PDF is:
\[
f(x) = 
\begin{cases}
1 & \text{if } 0 \leq x \leq 1, \\
0 & \text{otherwise}.
\end{cases}
\]

---

### **Summary**
The PDF of the Uniform distribution over \([a, b]\) is:
\[
f(x) = 
\begin{cases}
\frac{1}{b - a} & \text{if } a \leq x \leq b, \\
0 & \text{otherwise}.
\end{cases}
\]
It models situations where all outcomes in a given interval are equally likely and is widely used in probability and statistics. Let me know if you'd like further details!
