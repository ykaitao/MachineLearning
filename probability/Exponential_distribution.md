The **Exponential distribution** is a continuous probability distribution that models the time between events in a Poisson process, where events occur continuously and independently at a constant average rate. Let’s derive the **probability density function (PDF)** of the Exponential distribution step by step.

---

### **1. Background**
The Exponential distribution is characterized by a single parameter:
- **Rate parameter (\( \lambda \))**: The average rate at which events occur. Alternatively, the **scale parameter** \( \theta = \frac{1}{\lambda} \) represents the mean time between events.

The PDF of the Exponential distribution is:
\[
f(x) = \lambda e^{-\lambda x}, \quad x \geq 0.
\]

---

### **2. Derivation of the PDF**
The Exponential distribution can be derived from the **Poisson process**, which models the occurrence of events over time. Here’s how:

#### **Step 1: Poisson Process**
In a Poisson process:
- Events occur independently at a constant average rate \( \lambda \).
- The probability of an event occurring in a small time interval \( \Delta t \) is \( \lambda \Delta t \).
- The probability of no event occurring in \( \Delta t \) is \( 1 - \lambda \Delta t \).

#### **Step 2: Probability of No Events in Time \( t \)**
Let \( T \) be the time until the first event occurs. The probability that no events occur in time \( t \) is:
\[
P(T > t) = e^{-\lambda t}.
\]
This is because the number of events in time \( t \) follows a Poisson distribution with parameter \( \lambda t \), and the probability of 0 events is \( e^{-\lambda t} \).

#### **Step 3: Cumulative Distribution Function (CDF)**
The cumulative distribution function (CDF) of \( T \) is the probability that the time until the first event is less than or equal to \( t \):
\[
F(t) = P(T \leq t) = 1 - P(T > t) = 1 - e^{-\lambda t}.
\]

#### **Step 4: Probability Density Function (PDF)**
The PDF is the derivative of the CDF:
\[
f(t) = \frac{d}{dt} F(t) = \frac{d}{dt} \left(1 - e^{-\lambda t}\right).
\]
Compute the derivative:
\[
f(t) = \lambda e^{-\lambda t}.
\]

---

### **3. Exponential PDF Formula**
The PDF of the Exponential distribution with rate parameter \( \lambda \) is:
\[
f(t) = \lambda e^{-\lambda t}, \quad t \geq 0.
\]

---

### **4. Alternative Parameterization (Scale Parameter)**
The Exponential distribution is often parameterized using the **scale parameter** \( \theta = \frac{1}{\lambda} \), which represents the mean time between events. In this case, the PDF becomes:
\[
f(t) = \frac{1}{\theta} e^{-t / \theta}, \quad t \geq 0.
\]

---

### **5. Summary**
The PDF of the Exponential distribution is derived by:
1. Modeling the time between events in a Poisson process.
2. Calculating the probability of no events occurring in time \( t \).
3. Differentiating the CDF to obtain the PDF.

The resulting PDF describes the probability density of the time until the first event in a Poisson process.
