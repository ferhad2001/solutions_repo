# Measuring Earth's Gravitational Acceleration with a Pendulum

import numpy as np
import matplotlib.pyplot as plt

# ------------------ Step 1: Input Measurements ------------------ #
L = 1.0  # Pendulum length in meters
resolution_ruler = 0.01  # Ruler resolution in meters
Delta_L = resolution_ruler / 2  # Uncertainty in length

# Time measurements for 10 oscillations (T_10), in seconds
T_10_values = [20.1, 19.9, 20.0, 20.2, 19.8, 20.1, 19.9, 20.0, 20.2, 19.8]
T_10_values = np.array(T_10_values)
n = len(T_10_values)

# ------------------ Step 2: Calculate Mean and Uncertainties ------------------ #
T_10_mean = np.mean(T_10_values)
sigma_T = np.std(T_10_values, ddof=1)
Delta_T_10 = sigma_T / np.sqrt(n)

# Calculate single oscillation period and uncertainty
T = T_10_mean / 10
Delta_T = Delta_T_10 / 10

# ------------------ Step 3: Calculate g ------------------ #
# Formula: g = 4 * pi^2 * L / T^2
g = 4 * np.pi**2 * L / T**2

# ------------------ Step 4: Uncertainty in g ------------------ #
Delta_g = g * np.sqrt((Delta_L / L)**2 + (2 * Delta_T / T)**2)

# ------------------ Step 5: Output Results ------------------ #
print("Length of pendulum L =", L, "m")
print("Uncertainty in length ΔL =", Delta_L, "m")
print("Mean time for 10 oscillations T̄₁₀ =", round(T_10_mean, 3), "s")
print("Standard deviation σ_T =", round(sigma_T, 3), "s")
print("Uncertainty in T̄₁₀ =", round(Delta_T_10, 3), "s")
print("Period of 1 oscillation T =", round(T, 3), "s")
print("Uncertainty in period ΔT =", round(Delta_T, 4), "s")
print("\ng =", round(g, 3), "m/s²")
print("Δg =", round(Delta_g, 3), "m/s²")

# ------------------ Step 6: Visualization ------------------ #
plt.figure(figsize=(8, 4))
plt.plot(range(1, n+1), T_10_values, marker='o', linestyle='-', color='blue')
plt.axhline(T_10_mean, color='red', linestyle='--', label=f"Mean = {T_10_mean:.2f} s")
plt.title("Time for 10 Oscillations")
plt.xlabel("Trial")
plt.ylabel("Time (s)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

