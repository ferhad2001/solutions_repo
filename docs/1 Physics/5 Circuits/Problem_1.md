# Problem 1
# 🔌 Equivalent Resistance Using Graph Theory

## 📐 1. Series and Parallel Formulas

### Series:
\[
R_{\text{eq}} = R_1 + R_2 + R_3 + \dots + R_n
\]

### Parallel:
\[
\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
\]

---

## 🧮 2. Graph Representation

- Nodes: Circuit junctions
- Edges: Resistors with weight = resistance
- Use libraries like `networkx` for graph construction.

---

## 🔁 3. Graph Reduction Algorithm

### Step 1: Identify Series
- Look for a path where a node has exactly 2 neighbors and no other branches.

\[
R_{\text{eq}} = R_a + R_b
\]

### Step 2: Identify Parallel
- Look for multiple edges between the same two nodes.

\[
\frac{1}{R_{\text{eq}}} = \frac{1}{R_a} + \frac{1}{R_b}
\]

---

## 📚 4. Advanced Concepts

### Voltage Division:
\[
V_i = V_{\text{total}} \cdot \frac{R_i}{R_{\text{total}}}
\]

### Current Division:
\

