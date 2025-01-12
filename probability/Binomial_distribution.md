The **Binomial Distribution** is a discrete probability distribution that models the number of successes in a fixed number of independent Bernoulli trials. Let’s derive the **probability mass function (PMF)** for the Binomial distribution step by step.

---

### **1. Bernoulli Trial**
A **Bernoulli trial** is a random experiment with two possible outcomes: **success** (with probability \( p \)) or **failure** (with probability \( 1-p \)).

- Probability of success: \( P(X = 1) = p \)
- Probability of failure: \( P(X = 0) = 1-p \)

---

### **2. Binomial Experiment**
A **Binomial experiment** consists of \( n \) independent Bernoulli trials, each with the same probability of success \( p \). Let \( X \) be the random variable representing the number of successes in \( n \) trials.

---

### **3. Derivation of the Binomial PMF**
The PMF of the Binomial distribution gives the probability of observing exactly \( k \) successes in \( n \) trials. To derive it, we need to consider:
1. The number of ways to arrange \( k \) successes in \( n \) trials.
2. The probability of each specific arrangement.

#### **Step 1: Number of Arrangements**
The number of ways to choose \( k \) successes out of \( n \) trials is given by the **binomial coefficient**:
\[
\binom{n}{k} = \frac{n!}{k!(n-k)!}
\]

#### **Step 2: Probability of a Specific Arrangement**
Each specific arrangement of \( k \) successes and \( n-k \) failures has a probability:
\[
p^k (1-p)^{n-k}
\]
This is because:
- Each success has probability \( p \), and there are \( k \) successes.
- Each failure has probability \( 1-p \), and there are \( n-k \) failures.

#### **Step 3: Combine the Two**
The total probability of observing exactly \( k \) successes in \( n \) trials is the product of the number of arrangements and the probability of each arrangement:
\[
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
\]

---

### **4. Binomial PMF Formula**
The PMF of the Binomial distribution is:
\[
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, 2, \dots, n
\]
where:
- \( n \): Number of trials.
- \( k \): Number of successes.
- \( p \): Probability of success in a single trial.
- \( \binom{n}{k} \): Binomial coefficient, representing the number of ways to choose \( k \) successes out of \( n \) trials.

---

### **5. Binomial PDF**
The Binomial distribution is a **discrete distribution**, so it does not have a probability density function (PDF). Instead, it has a **probability mass function (PMF)** as derived above. The term "PDF" is typically used for continuous distributions, while "PMF" is used for discrete distributions.

---

### **6. Example**
Suppose you flip a fair coin (\( p = 0.5 \)) 10 times (\( n = 10 \)). What is the probability of getting exactly 4 heads (\( k = 4 \))?

Using the Binomial PMF:
\[
P(X = 4) = \binom{10}{4} (0.5)^4 (1-0.5)^{10-4}
\]
\[
P(X = 4) = \frac{10!}{4!6!} (0.5)^4 (0.5)^6
\]
\[
P(X = 4) = 210 \cdot (0.5)^{10}
\]
\[
P(X = 4) = 210 \cdot \frac{1}{1024} \approx 0.205
\]

So, the probability of getting exactly 4 heads in 10 flips is approximately 20.5%.

---

### **Summary**
- The **PMF of the Binomial distribution** is derived by considering the number of ways to arrange \( k \) successes in \( n \) trials and the probability of each arrangement.
- The formula is:
  \[
  P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, 2, \dots, n
  \]
- The Binomial distribution is discrete, so it has a PMF, not a PDF.
