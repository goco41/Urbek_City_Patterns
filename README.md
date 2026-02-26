# Urbek Farming Pattern Optimizer
This project contains the ultimate toolset for finding and refining farming patterns in **Urbek City Builder**. Developed through an iterative journey documented on Reddit, this repository provides a high-performance Python solver and a web-based visual editor.

## Evolution of the Pattern
This project started as a quest to find the theoretical maximum efficiency for farming layouts.
*   **Post #1:** 61.35 points
*   **Post #2:** 62.62 points
*   **Post #3:** 63.012 points
*   **Post #4 (Latest):** **67.92 points**

## Project Components

### 1. Trifecta Pattern Editor (`index.html`)
A standalone, browser-based visual editor designed to manually tweak patterns or visualize solver exports.
*   **God Mode:** Place buildings anywhere ignoring rules for quick drafting.
*   **Rule Engine:** Real-time validation of building requirements (radii, neighbors, road access).
*   **Import/Export:** Seamlessly copy-paste Python arrays to and from the solver.
*   **Interactive Info:** Click any building to see its current production and synergy status.

### 2. The Solver (`optimizer.py`)
A heavy-duty optimization script that uses Constraint Programming and Meta-heuristics.
*   **Google OR-Tools (CP-SAT):** Handles the complex logic of building requirements.
*   **ALNS (Adaptive Large Neighborhood Search):** A loop that "destroys" parts of the pattern and rebuilds them to find better local optima.
*   **Numba-Accelerated:** Geometric calculations (Manhattan/Chebyshev distances) are compiled to machine code for speed.
*   **Tiling Support:** Optimized for $72 \times 9$ blocks with multiple vertical/horizontal stacks.

---

## Getting Started

### Prerequisites
To run the Python solver, you need:
```bash
pip install ortools numpy numba matplotlib
```

### Running the Solver
1.  Open the Python script.
2.  Define your `tipos_usuario` (building rules) and `producciones`.
3.  Set your time limit (default is set for long-duration deep searches).
4.  Run the script:
    ```bash
    python optimizer.py
    ```
5.  The script will output a `patron_optimizado.csv` and a Python-formatted matrix.

### Using the Editor
1.  Open `index.html` in any modern web browser.
2.  Paste a matrix into the "Import" box.
3.  Use the **Move/Swap** tool to manually refine the layout.
4.  Check the **Average Score** in the header to see the impact of your changes.

---

## Building Logic (The "Trifecta" Rules)
The solver respects the complex interdependencies of Urbek's late-game farming:
*   **Food Plants (10):** Require proximity to Farm Sheds (8).
*   **Fruit Processors (9):** Require a massive number of Orchards (7).
*   **Silos (6):** Synergize with Warehouses (I8).
*   **Road Connectivity:** All buildings (except specific ones) must be connected via a pathing rank system to the main road.

---

## History & Community
This project was born and raised on the r/Urbek subreddit. You can follow the full development history and community discussions here:

*   [Update #1: Initial Discovery](https://www.reddit.com/r/urbek/comments/1ldv8mf/is_this_really_the_best_pattern_for_farming/)
*   [Update #2: Breaking the 62 Barrier](https://www.reddit.com/r/urbek/comments/1lf6s8b/is_this_the_best_pattern_for_farming_update/)
*   [Update #3: The 63.01 optimization](https://www.reddit.com/r/urbek/comments/1lvmts0/is_this_the_best_pattern_for_farming_update_30/)

---

## Referencias Académicas
La lógica de este optimizador se basa en investigaciones punteras sobre optimización combinatoria y problemas de rutas de vehículos:

*   **Røpke, S., & Pisinger, D. (2006):** *An Adaptive Large Neighborhood Search Heuristic*. (Base de la estructura adaptativa y ajuste de pesos de los operadores).
*   **Hojabri, H., et al. (2016):** *Large Neighborhood Search with Constraint Programming*. (Inspiración para los parámetros de intensidad y la integración LNS-CP).
*   **Thomas, C., & Schaus, P. (2018):** *Revisiting the Self-Adaptive Large Neighborhood Search*. (Lógica del Portfolio de operadores y actualización de pesos por eficiencia).
*   **Souza, F., et al. (2024):** *Improved Variable-Relationship Guided LNS (iVRG)*. (Técnica utilizada para la selección estructural de celdas relaxadas).
 
---
## License
This project is open-source and available under the **MIT License**. Feel free to fork, optimize further, and share your scores!

**Can you beat 67.92?** If so, open a PR or post it on Reddit!




## 📚 Referencias Académicas
La lógica de este optimizador se basa en investigaciones punteras sobre optimización combinatoria y problemas de rutas de vehículos:

*   **Røpke, S., & Pisinger, D. (2006):** *An Adaptive Large Neighborhood Search Heuristic*. (Base de la estructura adaptativa y ajuste de pesos de los operadores).
*   **Hojabri, H., et al. (2016):** *Large Neighborhood Search with Constraint Programming*. (Inspiración para los parámetros de intensidad y la integración LNS-CP).
*   **Thomas, C., & Schaus, P. (2018):** *Revisiting the Self-Adaptive Large Neighborhood Search*. (Lógica del Portfolio de operadores y actualización de pesos por eficiencia).
*   **Souza, F., et al. (2024):** *Improved Variable-Relationship Guided LNS (iVRG)*. (Técnica utilizada para la selección estructural de celdas relaxadas).
