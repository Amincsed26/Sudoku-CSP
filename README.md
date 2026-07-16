# 🧩 Sudoku-CSP

A Sudoku solver that models the puzzle as a **Constraint Satisfaction Problem (CSP)** and solves it using the **AC-3 (Arc Consistency 3)** algorithm, presented through a **PyQt5** desktop GUI.

## ✨ Overview

Each cell on the 9×9 board is treated as a CSP variable with an initial domain of `{1–9}` (or a fixed value if pre-filled). Row, column, and 3×3 sub-grid "all-different" constraints define the arcs between variables. AC-3 repeatedly prunes inconsistent values from each variable's domain by enforcing arc consistency across all constrained pairs, reducing the search space before/while a solution is derived.

- **Variables:** 81 cells (one per board position)
- **Domains:** `{1, 2, ..., 9}` per empty cell
- **Constraints:** All-different across each row, column, and 3×3 block
- **Inference algorithm:** AC-3 (arc consistency propagation)

---

## 🛠️ Tech Stack
- Python
- PyQt5 (GUI framework)

---

## 📂 Project Structure
```
Sudoku-CSP/
├── GUI/         # PyQt5 windows, widgets, and UI assets for the Sudoku board
├── adapter/     # Adapter layer connecting the GUI to the CSP solving logic
├── modules/     # Core CSP model (variables, domains, constraints, AC-3 implementation)
├── services/    # Supporting services used by the solver/application
└── main.py      # Application entry point (launches the PyQt5 GUI)
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.x
- PyQt5

### Installation
```bash
git clone https://github.com/Amincsed26/Sudoku-CSP.git
cd Sudoku-CSP
pip install PyQt5
```

### Run
```bash
python main.py
```

This launches the GUI, where a Sudoku board can be entered/loaded and solved using the AC-3-based CSP solver.

---

## 📈 How It Works
1. The board is parsed into 81 variables, each with a domain of possible digits.
2. Constraints are generated for every row, column, and 3×3 box (all-different).
3. AC-3 processes the constraint arcs, removing values from domains that cannot satisfy some constraint, until the network is arc-consistent or a domain is emptied (indicating no solution).
4. The (possibly further searched/reduced) result is rendered back onto the GUI board.
