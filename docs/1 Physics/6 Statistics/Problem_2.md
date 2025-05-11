# Monte Carlo Estimation of Pi using Circle Method and Buffon's Needle

import random
import math
import matplotlib.pyplot as plt

### PART 1: Circle-based Monte Carlo Estimation ###
def estimate_pi_circle(num_points):
    inside_circle = 0
    x_inside, y_inside = [], []
    x_outside, y_outside = [], []

    for _ in range(num_points):
        x = random.uniform(-1, 1)
        y = random.uniform(-1, 1)
        if x**2 + y**2 <= 1:
            inside_circle += 1
            x_inside.append(x)
            y_inside.append(y)
        else:
            x_outside.append(x)
            y_outside.append(y)

    pi_estimate = 4 * inside_circle / num_points
    return pi_estimate, x_inside, y_inside, x_outside, y_outside

# Visualization for circle method
def plot_circle_method(xi, yi, xo, yo, pi, num_points):
    plt.figure(figsize=(6,6))
    plt.scatter(xi, yi, color='blue', s=1, label='Inside Circle')
    plt.scatter(xo, yo, color='red', s=1, label='Outside Circle')
    plt.title(f'Monte Carlo Estimation of π\nEstimated π = {pi:.5f} with {num_points} points')
    plt.legend()
    plt.xlabel('x')
    plt.ylabel('y')
    plt.axis('equal')
    plt.grid(True)
    plt.show()

### PART 2: Buffon's Needle Estimation ###
def estimate_pi_buffon(num_drops, needle_length=1.0, line_spacing=1.0):
    crossings = 0
    for _ in range(num_drops):
        y_center = random.uniform(0, line_spacing / 2)
        theta = random.uniform(0, math.pi / 2)
        if y_center <= (needle_length / 2) * math.sin(theta):
            crossings += 1

    if crossings == 0:
        return float('inf')  # Avoid division by zero

    pi_estimate = (2 * needle_length * num_drops) / (line_spacing * crossings)
    return pi_estimate

### MAIN EXECUTION ###
if __name__ == '__main__':
    # Parameters
    num_points = 10000
    num_drops = 10000

    # Circle-based estimation
    pi_circle, xi, yi, xo, yo = estimate_pi_circle(num_points)
    print(f"[Circle Method] Estimated π: {pi_circle:.5f} using {num_points} points")
    plot_circle_method(xi, yi, xo, yo, pi_circle, num_points)

    # Buffon's Needle estimation
    pi_buffon = estimate_pi_buffon(num_drops)
    print(f"[Buffon's Needle] Estimated π: {pi_buffon:.5f} using {num_drops} needle drops")

"""
# Estimating π Using Monte Carlo Methods

## 1. Introduction
This script demonstrates two Monte Carlo techniques to estimate π:
- Geometric probability via points inside a circle.
- Buffon's Needle problem using random needle drops.

## 2. Circle-Based Method
### Formula:
π ≈ 4 * (number of points inside circle / total number of points)

### Procedure:
- Generate random (x, y) in a unit square.
- Count how many fall within the inscribed circle.
- Multiply ratio by 4 to estimate π.

## 3. Buffon's Needle Method
### Formula:
π ≈ (2 * needle_length * num_drops) / (line_spacing * crossings)

### Procedure:
- Simulate needle drops across parallel lines.
- Count how many cross a line.
- Use formula to estimate π.

## 4. Results and Observations
- Both methods converge to π with more iterations.
- The circle method generally converges faster.
- Buffon’s method shows more variance for fewer trials.

## 5. Conclusion
Monte Carlo simulations provide elegant probabilistic estimations for mathematical constants like π.
"""
