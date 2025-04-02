# Problem 1

# Simulating the Effects of the Lorentz Force

## Motivation
The Lorentz force governs the motion of charged particles in electric and magnetic fields. It is foundational in various fields such as plasma physics, particle accelerators, and astrophysics.

## 1. Exploration of Applications

### Key Systems
- **Particle Accelerators**: Utilizes electric and magnetic fields to accelerate charged particles to high speeds.
- **Mass Spectrometers**: Analyzes the mass-to-charge ratio of ions using electric and magnetic fields for trajectory manipulation.
- **Plasma Confinement**: Employs magnetic fields to confine plasma in fusion reactors.

### Relevance of Electric and Magnetic Fields
- The electric field \((\mathbf{E})\) exerts a force on charged particles: 
  \[
  \mathbf{F_E} = q\mathbf{E}
  \]
- The magnetic field \((\mathbf{B})\) interacts with the moving charges: 
  \[
  \mathbf{F_B} = q(\mathbf{v} \times \mathbf{B})
  \]

The total Lorentz force \((\mathbf{F})\) is given by:
\[
\mathbf{F} = q(\mathbf{E} + \mathbf{v} \times \mathbf{B})
\]

## 2. Simulating Particle Motion

### Python Implementation
Initial setup for simulating the motion of a charged particle under different field conditions.

```python
import numpy as np
import matplotlib.pyplot as plt

def lorentz_force(q, v, E, B):
    return q * (E + np.cross(v, B))

def simulate_particle_motion(q, m, v_init, E, B, t_end, dt):
    t = np.arange(0, t_end, dt)
    v = np.zeros((len(t), 3))  # velocity in 3D
    v[0] = v_init
    
    pos = np.zeros((len(t), 3))  # position in 3D
    for i in range(1, len(t)):
        F = lorentz_force(q, v[i-1], E, B)
        a = F / m
        v[i] = v[i-1] + a * dt
        pos[i] = pos[i-1] + v[i-1] * dt
    
    return pos

# Parameters
q = 1.6e-19  # Charge (C)
m = 9.11e-31  # Mass (kg)
v_init = np.array([1e6, 0, 0])  # Initial velocity (m/s)
E = np.array([0, 0, 0])  # Electric field (N/C)
B = np.array([0, 0, 1])  # Magnetic field (T)
t_end = 1e-5  # End time (s)
dt = 1e-8  # Time step (s)

pos = simulate_particle_motion(q, m, v_init, E, B, t_end, dt)

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(pos[:, 0], pos[:, 1])
plt.title('Particle Trajectory in a Magnetic Field')
plt.xlabel('X Position (m)')
plt.ylabel('Y Position (m)')
plt.axhline(0, color='grey', lw=1, ls='--')
plt.axvline(0, color='grey', lw=1, ls='--')
plt.grid()
plt.axis('equal')
plt.show()
