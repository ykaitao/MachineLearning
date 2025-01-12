The **Pareto distribution** is a continuous probability distribution that is often used to model phenomena where a small proportion of items account for a large proportion of some resource (e.g., wealth distribution, city sizes). Let’s derive the **probability density function (PDF)** of the Pareto distribution step by step.

---

### **1. Background**
The Pareto distribution is characterized by two parameters:
- **Scale parameter (\( x_m \))**: The minimum value of the random variable.
- **Shape parameter (\( \alpha \))**: Controls the shape of the distribution (also called the tail index).

The PDF of the Pareto distribution is:
\[
f(x) = \frac{\alpha x_m^\alpha}{x^{\alpha + 1}}, \quad x \geq x_m.
\]

---

### **2. Derivation of the PDF**
The Pareto distribution can be derived from the **power-law principle**, which states that the probability of observing a value \( x \) is proportional to \( x^{-\alpha} \). Here’s how:

#### **Step 1: Power-Law Principle**
Assume that the probability density \( f(x) \) follows a power-law relationship:
\[
f(x) \propto x^{-\alpha}, \quad x \geq x_m.
\]

#### **Step 2: Normalization**
To ensure that the total probability integrates to 1, we normalize \( f(x) \):
\[
\int_{x_m}^\infty f(x) \, dx = 1.
\]
Substitute \( f(x) = C x^{-\alpha} \), where \( C \) is the normalization constant:
\[
\int_{x_m}^\infty C x^{-\alpha} \, dx = 1.
\]

#### **Step 3: Evaluate the Integral**
The integral is:
\[
C \int_{x_m}^\infty x^{-\alpha} \, dx = C \left[ \frac{x^{-\alpha + 1}}{-\alpha + 1} \right]_{x_m}^\infty.
\]
For \( \alpha > 1 \), the integral converges:
\[
C \left[ \frac{x^{-\alpha + 1}}{-\alpha + 1} \right]_{x_m}^\infty = C \left( 0 - \frac{x_m^{-\alpha + 1}}{-\alpha + 1} \right) = C \cdot \frac{x_m^{-\alpha + 1}}{\alpha - 1}.
\]
Set this equal to 1:
\[
C \cdot \frac{x_m^{-\alpha + 1}}{\alpha - 1} = 1.
\]
Solve for \( C \):
\[
C = \frac{\alpha - 1}{x_m^{-\alpha + 1}} = (\alpha - 1) x_m^{\alpha - 1}.
\]

#### **Step 4: PDF of the Pareto Distribution**
Substitute \( C \) back into \( f(x) \):
\[
f(x) = (\alpha - 1) x_m^{\alpha - 1} x^{-\alpha}.
\]
Simplify the expression:
\[
f(x) = \frac{\alpha x_m^\alpha}{x^{\alpha + 1}}, \quad x \geq x_m.
\]

---

### **3. Pareto PDF Formula**
The PDF of the Pareto distribution with scale parameter \( x_m \) and shape parameter \( \alpha \) is:
\[
f(x) = \frac{\alpha x_m^\alpha}{x^{\alpha + 1}}, \quad x \geq x_m.
\]

---

### **4. Summary**
The PDF of the Pareto distribution is derived by:
1. Assuming a power-law relationship for the probability density.
2. Normalizing the PDF to ensure the total probability integrates to 1.
3. Solving for the normalization constant \( C \).

The resulting PDF describes the probability density of a random variable that follows a power-law distribution.
