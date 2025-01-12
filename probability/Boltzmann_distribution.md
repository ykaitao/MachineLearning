The **Boltzmann distribution** is a probability distribution that describes the distribution of states in a system at thermal equilibrium. It is widely used in statistical mechanics and machine learning (e.g., energy-based models, Boltzmann machines). Let’s derive its **probability mass function (PMF)** step by step.

---

### **1. Definition of the Boltzmann Distribution**
The Boltzmann distribution is characterized by:
- \( E(x) \): The energy of state \( x \),
- \( T \): The temperature of the system (\( T > 0 \)).

The probability of a state \( x \) is proportional to the exponential of the negative energy divided by the temperature:
\[
P(x) \propto \exp\left(-\frac{E(x)}{T}\right).
\]

---

### **2. Derivation of the PMF**
The PMF of the Boltzmann distribution is derived by normalizing the exponential weights. Here’s how it works:

#### **Step 1: Unnormalized Probability**
The unnormalized probability of state \( x \) is:
\[
P(x) \propto \exp\left(-\frac{E(x)}{T}\right).
\]

#### **Step 2: Normalization Constant**
To ensure the probabilities sum to 1, we introduce the **partition function** \( Z \):
\[
Z = \sum_{x} \exp\left(-\frac{E(x)}{T}\right).
\]
The partition function \( Z \) normalizes the probabilities.

#### **Step 3: PMF of the Boltzmann Distribution**
The PMF of the Boltzmann distribution is:
\[
P(x) = \frac{\exp\left(-\frac{E(x)}{T}\right)}{Z}.
\]

---

### **3. PMF Formula**
The PMF of the Boltzmann distribution is:
\[
P(x) = \frac{\exp\left(-\frac{E(x)}{T}\right)}{Z},
\]
where:
- \( Z = \sum_{x} \exp\left(-\frac{E(x)}{T}\right) \) is the partition function,
- \( E(x) \): The energy of state \( x \),
- \( T \): The temperature of the system.

---

### **4. Key Properties**
- **Energy-Based**: States with lower energy have higher probabilities.
- **Temperature**: Higher temperatures make the distribution more uniform, while lower temperatures concentrate probability on low-energy states.
- **Partition Function**: \( Z \) ensures normalization and is often computationally expensive to compute.

---

### **5. Use Case**
The Boltzmann distribution is used to model:
- Systems in thermal equilibrium (e.g., gases, spins),
- Energy-based models in machine learning (e.g., Boltzmann machines),
- Probabilistic graphical models.

---

### **6. Example**
Suppose a system has three states with energies \( E(1) = 1 \), \( E(2) = 2 \), and \( E(3) = 3 \), and the temperature is \( T = 1 \). The PMF of the Boltzmann distribution is:
\[
P(x) = \frac{\exp\left(-E(x)\right)}{Z},
\]
where:
\[
Z = \exp(-1) + \exp(-2) + \exp(-3).
\]
Thus:
\[
P(1) = \frac{\exp(-1)}{Z}, \quad P(2) = \frac{\exp(-2)}{Z}, \quad P(3) = \frac{\exp(-3)}{Z}.
\]

---

### **7. Connection to the Gibbs Distribution**
The Boltzmann distribution is a special case of the **Gibbs distribution**, which generalizes to systems with multiple particles and interactions.

---

### **Summary**
The PMF of the Boltzmann distribution is:
\[
P(x) = \frac{\exp\left(-\frac{E(x)}{T}\right)}{Z},
\]
where \( Z = \sum_{x} \exp\left(-\frac{E(x)}{T}\right) \). It models the distribution of states in a system at thermal equilibrium and is widely used in physics and machine learning. Let me know if you'd like further details!
