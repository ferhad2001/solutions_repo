import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Constants
q = 1.0     # charge (C)
m = 1.0     # mass (kg)
E = np.array([0.0, 0.0, 0.0])  # Electric field (V/m)
B = np.array([0.0, 0.0, 1.0])  # Magnetic field (T)

# Initial conditions
r = np.array([0.0, 0.0, 0.0])  # Initial position
v = np.array([1.0, 0.0, 0.0])  # Initial velocity
dt = 0.01                      # Time step (s)
steps = 1000                  # Number of steps
