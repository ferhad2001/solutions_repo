import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Constants
q = 1.6e-19  # Charge of the particle (Coulombs)
m = 9.11e-31  # Mass of the particle (kg)
B = np.array([0, 0, 1])  # Magnetic field (T)
E = np.array([0, 0, 0])  # Electric field (V/m)
v0 = np.array([1e6, 0, 0])  # Initial velocity (m/s)
r0 = np.array([0, 0, 0])  # Initial position (m)

dt = 1e-10  # Time step (s)
n_steps = 1000  # Number of time steps

def lorentz_force(q, v, E, B):
    """Compute the Lorentz force."""
    return q * (E + np.cross(v, B))

def simulate_motion(q, m, r0, v0, E, B, dt, n_steps):
    """Simulates the motion of a charged particle under Lorentz force."""
    r = np.zeros((n_steps, 3))
    v = v0.copy()
    r[0] = r0
    
    for i in range(1, n_steps):
        F = lorentz_force(q, v, E, B)
        a = F / m  # Acceleration (Newton's Second Law)
        v = v + a * dt  # Update velocity
        r[i] = r[i - 1] + v * dt  # Update position
    
    return r

# Run simulation
trajectory = simulate_motion(q, m, r0, v0, E, B, dt, n_steps)

# Visualization
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot(trajectory[:, 0], trajectory[:, 1], trajectory[:, 2], label='Particle Trajectory')
ax.set_xlabel("X Position (m)")
ax.set_ylabel("Y Position (m)")
ax.set_zlabel("Z Position (m)")
ax.set_title("Motion of a Charged Particle in a Magnetic Field")
ax.legend()
plt.show()
