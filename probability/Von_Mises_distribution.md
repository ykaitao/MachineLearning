The **Von Mises distribution** is a continuous probability distribution defined on the circle (or more generally, on the unit sphere in higher dimensions). It is often used to model directional data, such as angles or orientations. Let’s derive its **probability density function (PDF)** step by step.

---

### **1. Definition of the Von Mises Distribution**
The Von Mises distribution is characterized by two parameters:
- \( \mu \): The mean direction (a angle in radians, \( 0 \leq \mu < 2\pi \)),
- \( \kappa \): The concentration parameter (\( \kappa \geq 0 \)).

The random variable \( \theta \) represents an angle and takes values in the interval \( [0, 2\pi) \).

---

### **2. Derivation of the PDF**
The PDF of the Von Mises distribution is derived by analogy to the normal distribution but adapted for circular data. Here’s how it works:

#### **Step 1: Circular Analogy to the Normal Distribution**
The normal distribution on the real line has the PDF:
\[
f(x | \mu, \sigma^2) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp\left(-\frac{(x - \mu)^2}{2\sigma^2}\right).
\]
For circular data, we replace the squared distance \( (x - \mu)^2 \) with the angular distance \( 1 - \cos(\theta - \mu) \).

#### **Step 2: Exponential Form**
The Von Mises distribution is defined in exponential form as:
\[
f(\theta | \mu, \kappa) = \frac{1}{2\pi I_0(\kappa)} \exp\left(\kappa \cos(\theta - \mu)\right),
\]
where:
- \( I_0(\kappa) \): The modified Bessel function of order 0, which ensures normalization.

#### **Step 3: Normalization Constant**
The normalization constant \( 2\pi I_0(\kappa) \) ensures that the PDF integrates to 1 over the interval \( [0, 2\pi) \):
\[
\int_0^{2\pi} f(\theta | \mu, \kappa) \, d\theta = 1.
\]
Substitute the PDF:
\[
\int_0^{2\pi} \frac{1}{2\pi I_0(\kappa)} \exp\left(\kappa \cos(\theta - \mu)\right) \, d\theta = 1.
\]
The integral evaluates to \( 2\pi I_0(\kappa) \), so:
\[
\frac{1}{2\pi I_0(\kappa)} \cdot 2\pi I_0(\kappa) = 1.
\]

---

### **3. PDF Formula**
The PDF of the Von Mises distribution with mean direction \( \mu \) and concentration parameter \( \kappa \) is:
\[
f(\theta | \mu, \kappa) = \frac{1}{2\pi I_0(\kappa)} \exp\left(\kappa \cos(\theta - \mu)\right), \quad 0 \leq \theta < 2\pi.
\]

---

### **4. Key Properties**
- **Mean**: \( \mathbb{E}[\theta] = \mu \),
- **Concentration**: Higher \( \kappa \) values indicate stronger concentration around \( \mu \),
- **Symmetry**: The distribution is symmetric about \( \mu \).

---

### **5. Use Case**
The Von Mises distribution is used to model:
- Directional data (e.g., wind directions, animal migration paths),
- Circular statistics and data analysis,
- Periodic phenomena (e.g., time of day, seasonal patterns).

---

### **6. Example**
Suppose \( \theta \) follows a Von Mises distribution with \( \mu = \pi/2 \) and \( \kappa = 2 \). The PDF of \( \theta \) is:
\[
f(\theta | \pi/2, 2) = \frac{1}{2\pi I_0(2)} \exp\left(2 \cos(\theta - \pi/2)\right).
\]

---

### **7. Connection to the Normal Distribution**
When \( \kappa \) is large, the Von Mises distribution approximates a normal distribution on the circle:
\[
f(\theta | \mu, \kappa) \approx \frac{1}{\sqrt{2\pi / \kappa}} \exp\left(-\frac{\kappa (\theta - \mu)^2}{2}\right).
\]

---

### **Summary**
The PDF of the Von Mises distribution is:
\[
f(\theta | \mu, \kappa) = \frac{1}{2\pi I_0(\kappa)} \exp\left(\kappa \cos(\theta - \mu)\right), \quad 0 \leq \theta < 2\pi.
\]
It models directional data and is widely used in circular statistics. Let me know if you'd like further details!
