# 🏀 NBA Schedule Optimization via Integer Programming

## 📌 Overview
This project studies the reconstruction and improvement of an NBA regular-season schedule using Integer Programming (IP).

Given a preliminary (fictitious) schedule, the goal is to:
- Reconstruct alternative feasible schedules that preserve league constraints  
- Incorporate travel-related constraints (time zones)  
- Evaluate improvements in schedule quality using a proxy for travel burden  

The project combines data processing, optimization modeling, and performance evaluation to solve a real-world scheduling problem.

---

## 📂 Data

- [`games_data.csv`](./games_data.csv): Original schedule dataset containing game dates, home teams, and away teams  

---

## 🧠 Modeling Framework

### 🔹 Problem 1: Structural Constraint Extraction
From the original schedule, we extract:
- Home game dates for each team  
- Away game dates for each team  
- Pairwise matchup frequencies  

These define the **feasible space of all valid schedules**.

---

### 🔹 Problem 2: Feasible Schedule Reconstruction (MILP)
We formulate a **Mixed-Integer Linear Program (MILP)**:

**Decision Variable**
- `x[i,j,d] = 1` if team *i* hosts team *j* on date *d*

**Constraints**
- Each team plays exactly one game per assigned date  
- Home/away dates must match the original schedule  
- Matchup frequencies must be preserved  

**Output**
- [`feasible_schedule_problem2.csv`](./feasible_schedule_problem2.csv)  
- [`feasible_schedule_problem2.pdf`](./feasible_schedule_problem2.pdf)  

---

### 🔹 Problem 3: Time-Zone-Constrained Scheduling
We extend the model with **travel constraints**:

- Each game is associated with a time zone  
- Teams cannot play 3 consecutive games with excessive time-zone shifts  

**Result**
- Eliminates infeasible travel sequences  
- Maintains full feasibility  

**Output**
- [`feasible_schedule_problem3.csv`](./feasible_schedule_problem3.csv)  
- [`feasible_schedule_problem3.pdf`](./feasible_schedule_problem3.pdf)  

---

### 🔹 Problem 4: Schedule Improvement Analysis
We evaluate schedule quality using a **proxy travel metric**:

- Total time-zone movement across consecutive games  
- Number of "forbidden" travel sequences  

**Results**
- All forbidden sequences are eliminated  
- Average travel burden is reduced across teams  

**Output**
- [`schedule_improvement_summary_problem4.pdf`](./schedule_improvement_summary_problem4.pdf)  
- [`schedule_improvement_summary_problem4.csv`](./schedule_improvement_summary_problem4.csv)  

---

## 📈 Results & Insights

- A feasible schedule satisfying all structural constraints exists  
- Adding travel constraints does **not break feasibility**  
- Time-zone constraints improve schedule quality:
  - Eliminate extreme travel patterns  
  - Reduce cumulative travel burden  

This demonstrates how optimization can balance:
- Feasibility  
- Operational constraints  
- Player welfare considerations  

---

## 🛠️ Tech Stack

- Python (Pandas, NumPy)  
- Optimization: PuLP / MILP (CBC Solver)  
- Data Processing & Validation  

---

## 📂 Repository Structure
```
├── games_data.csv                          # Original schedule data
├── feasible_schedule_problem2.csv          # Feasible schedule (P2)
├── feasible_schedule_problem2.pdf
├── feasible_schedule_problem3.csv          # Time-zone constrained schedule (P3)
├── feasible_schedule_problem3.pdf
├── schedule_improvement_summary_problem4.csv  # Travel comparison (P4)
├── schedule_improvement_summary_problem4.pdf
├── NBA_Schedule_Project.ipynb              # Modeling & experiments
├── Optimization_Project_2.pdf              # Final report
└── README.md
```

---

## 📄 Report

For full methodology and mathematical formulation, see:

👉 [`Optimization_Project_2.pdf`](./Optimization_Project_2.pdf)

---

## ✨ Key Takeaways

- Integer Programming can reconstruct complex scheduling systems  
- Adding realistic constraints improves outcomes without sacrificing feasibility  
- Optimization provides a structured way to evaluate trade-offs in large-scale systems  

---

## 👤 Author
Althea He  
Columbia University
