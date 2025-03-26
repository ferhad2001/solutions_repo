# Problem 1

# Investigating the Range as a Function of the Angle of Projection

## Motivation
Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Yet, beneath this simplicity lies a complex and versatile framework. 

The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful. This study allows us to analyze key parameters such as initial velocity, gravitational acceleration, and launch height, which influence real-world scenarios like sports and rocket trajectories.

---

## 1. Theoretical Foundation
### Equations of Motion
We derive the equations of motion using kinematic principles:

- **Horizontal motion:**
  \[
  x = v_0 \cos\theta \cdot t
  \]
- **Vertical motion:**
  \[
  y = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
  \]

The time of flight is obtained by solving for \( t \) when \( y = 0 \):

\[
 t = \frac{2 v_0 \sin\theta}{g}
\]

Thus, the **range** \( R \) is:

\[
 R = v_0 \cos\theta \cdot t = \frac{v_0^2 \sin 2\theta}{g}
\]

- The range depends on both the initial velocity \( v_0 \) and launch angle \( \theta \).
- The **maximum range** occurs at \( \theta = 45^\circ \).

---

## 2. Analysis of the Range
- **Effect of Initial Velocity (\( v_0 \))**: Increasing \( v_0 \) increases the range quadratically.
- **Effect of Gravity (\( g \))**: Higher gravity (e.g., Jupiter) reduces the range, while lower gravity (e.g., Moon) increases it.
- **Effect of Angle (\( \theta \))**: The range is symmetric around 45°; i.e., \( 30^\circ \) and \( 60^\circ \) yield the same range.

---

## 3. Practical Applications
This model applies to real-world systems such as:
- **Sports**: Basketball, soccer, javelin throws.
- **Engineering**: Ballistic missile trajectories, launch angles for rockets.
- **Astrophysics**: Projectiles on celestial bodies with varying gravity.

### Real-World Challenges:
- Air resistance significantly alters motion.
- Wind and uneven terrain can impact the actual range.

---

## 4. Implementation in Python
![alt text](image-1.png)

---

## 5. Limitations & Extensions
### Limitations
- Assumes **no air resistance**, **flat terrain**, and **uniform gravity**.
- Ignores rotational effects and wind influence.

### Extensions
- **Include drag force** for more realistic motion.
- **Model projectiles on uneven terrain**.
- **Account for varying wind speeds**.

---

## Conclusion
This study demonstrates how fundamental physics principles govern projectile motion. By adjusting parameters such as velocity and gravity, we can model a wide variety of real-world applications. Future work can incorporate more realistic factors such as drag and wind resistance to refine our understanding.
