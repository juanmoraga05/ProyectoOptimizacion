# 🏀 Joel Embiid Schedule Optimization (2025-2026)

## Overview
This project applies **Mathematical Optimization** to solve a critical resource allocation problem for the Philadelphia 76ers: managing Joel Embiid's playing time for the 2025/2026 NBA season.

The goal is to find the perfect balance between maximizing the team's total wins and minimizing the star player's injury risk, ensuring he arrives healthy for the playoffs while maintaining player satisfaction.

> **Note:** For a deep dive into the mathematical formulation, constraints, and business context, please refer to the detailed report: **[Optimization Project.pdf](Optimization%20Project.pdf)**.

## How It Works

The solution is built in Python using **Pyomo** and **Scikit-learn**, following a three-step approach:

### 1. Opponent Clustering (Data Analysis)
Not all wins are equal, and not all opponents require the same effort. We analyzed team metrics (Offensive/Defensive Ratings, Net Rating, Projected Wins) to categorize all NBA teams into 4 distinct clusters using **K-Means**:
* **Cluster 0 & 3:** Elite Contenders (High effort required).
* **Cluster 2:** Playoff Hopefuls.
* **Cluster 1:** Rebuilding/Tanking teams (Low effort required).

### 2. The Optimization Model
We formulated a Mixed-Integer Programming (MIP) model to make two key decisions for every game of the season:
1.  **Binary Decision:** Should Embiid suit up? (Yes/No)
2.  **Continuous Decision:** If yes, how many minutes should he play?

**Objective:** Maximize the expected accumulated "Score" (a proxy for Win Probability) over the 82-game season.

**Key Constraints:**
* **Injury Risk Threshold:** The model calculates accumulated fatigue based on recent minutes played. If the risk exceeds a safety parameter, Embiid is forced to rest.
* **"The Trade Request" Constraint:** Embiid must play a minimum amount of total minutes/games to feel valued and avoid demanding a trade.
* **Physical Limits:** Maximum minutes per game and specific handling of back-to-back games.

### 3. Results
The model outputs an optimal schedule that suggests resting Embiid against specific lower-tier opponents or during high-risk schedule stretches, while allocating heavy minutes against direct conference rivals.

## Repository Structure

* `main.ipynb`: The Jupyter Notebook containing the data cleaning, clustering logic, and the Pyomo optimization model.
* `Optimization Project.pdf`: Detailed report covering the problem statement, mathematical formulation, and scenario analysis.
* `data/`:
    * `schedule.csv`: The 2025/2026 76ers schedule.
    * `ratings.csv` & `wins.csv`: Team performance metrics used for clustering.
* `model_approach.jpg`: Visual diagram of the project workflow.

## Dependencies

To run the notebook, you will need:

* Python 3.x
* Pyomo (Optimization)
* Pandas & NumPy (Data Manipulation)
* Scikit-learn (K-Means Clustering)
* Matplotlib (Visualization)

## Authors
* Juan Díaz Arenas
* Javier Andrés Bernárdez
* Juan García Moraga
* Ana Banqueri Camy