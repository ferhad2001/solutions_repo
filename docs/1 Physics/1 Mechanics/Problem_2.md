# Problem 2

# Forced Damped Pendulum Dynamics

## Motivation

The forced damped pendulum shows behavior from damping, restoring forces, and external forcing, leading to resonance, chaos, and quasiperiodic motion.

---

## 1. Theoretical Foundation

### Governing Equation

\[
\ddot{\theta} + b \dot{\theta} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
\]

For small angles, \( \sin(\theta) \approx \theta \):

\[
\ddot{\theta} + b \dot{\theta} + \frac{g}{L} \theta = A \cos(\omega t)
\]

### Resonance Condition

At resonance: 

\[
\omega = \sqrt{\frac{g}{L}}
\]

---

## 2. Dynamics Analysis

### Parameter Influence

- **Damping**: Increases damping reduces oscillation amplitude.
- **Driving Amplitude**: Larger \( A \) increases transition to chaotic behavior.
- **Driving Frequency**: Resonance at \( \omega \approx \sqrt{\frac{g}{L}} \).

---

## 3. Practical Applications

- **Energy Harvesting**: Pendulum motion generates power.
- **Suspension Bridges**: Modeling vibrations.
- **Oscillating Circuits**: Similar to driven RLC circuits.

---

## 4. Implementation

![alt text](image-6.png)
![alt text](image-7.png)