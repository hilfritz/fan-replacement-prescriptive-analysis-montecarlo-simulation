# Cooling Fan Replacement Policy – Prescriptive Analysis 

## Table of Contents
- [Monte Carlo Simulation](#monte-carlo-simulation)
- [Problem Definition](#problem-definition)
- [Objective](#objective)
- [Variables & Distributions](#variables--distributions)
- [Policy Key Performance Indicators (KPIs)](#policy-key-performance-indicators-kpis)
- [Monte Carlo Simulation Implementation](#monte-carlo-simulation-implementation)
- [How To Use](#how-to-use)
- [Results & Recommendation](#results--recommendations)

## Monte Carlo simulation
**What is Monte Carlo simulation?** </br>
- Monte Carlo simulation is a tool used in descriptive, predictive tool, and prescriptive analytics. In Predictive Analysis it helps by providing decision-makers a way to compare stratigies (in this case Policies) under uncertainty.
- It is a technique that uses repeated random sampling of data to estimate the probability of different outcomes in a process that cannot easily be predicteddue to uncertainty.
- In this project, it is used to prescribe the most cost-effective cooling fan replacement policy for the data center.  


## Problem Definition
A data center relies on a server rack cooled by **three identical fans**.  
When a fan fails, the server shuts down and requires technician intervention.  
  
  Two policies were evaluated:  
  - **Current Policy (V1):** Replace only the failed fan.  
  - **Proposed Policy (V2):** Replace all three fans whenever one fails.  


## Objective
- The objective is to determine which policy minimizes total costs, using **Monte Carlo simulation** in **Python**.

## Variables & Distributions
- **Fan Lifetime (hrs)**: Discrete distribution between **1,000 – 1,900 hrs** with varying probabilities.  
- **Technician Arrival Delay (min)**:  
  - 20 → 60%  
  - 30 → 30%  
  - 45 → 10%  
- **Costs**:  
  - Fan = **$32/unit**  
  - Downtime = **$10/minute**  
  - Labor = **$30/hour**  
- **Replacement Times**:  
  - 1 fan → 20 min  
  - 2 fans → 30 min  
  - 3 fans → 40 min

## Policy Key Performance Indicators (KPIs)

To evaluate the effectiveness of the two fan replacement policies, the following KPIs were measured:

### Cost KPIs
- **Total Cost ($):** Overall economic outcome, the primary decision-making metric.  
- **Cost Breakdown ($):** Separate reporting of Fan, Labor, and Downtime costs.  
- **Cost Variability:** Standard deviation of Total Cost across multiple simulation runs (predictability).  
- **Mean Cost per Time:** Ratio of total cost to operational time, normalizing cost efficiency.

### Reliability & Operations KPIs
- **Cumulative Downtime (hrs):** Total server unavailability until 45 fans are replaced.  
- **Operating Horizon (hrs):** Elapsed time to reach 45 fan replacements.  
- **Convergence Diagnostics:** Tracking of mean and standard deviation of Total Cost across runs to confirm sufficient simulation repetitions.

These KPIs provide both financial and operational insights, showing not only which policy is cheaper, but also how stable, predictable, and reliable it is under uncertainty.

## Monte Carlo Simulation Implementation
The simulation was implemented as an **event-driven Monte Carlo model**:  
- **Random inputs:**  
  - Fan lifetimes sampled from discrete distribution (1,000–1,900 hrs).  
  - Technician delays sampled from distribution (20, 30, 45 mins).  
- **Policy rules:**  
  - **Current Policy (V1):** Replace only failed fan.  
  - **Proposed Policy (V2):** Replace all three fans whenever one fails.  
- **Simulation loop:**  
  - Continue until **45 fans replaced**.  
  - Record per-event and per-run costs (Fan, Labor, Downtime).  
- **Repetition:** Multiple runs (e.g., 500) were executed to ensure stable averages and reliable KPIs.

## How To Use
This section shows how the project is structured and how to use to properly run the simulation. The Monte Carlo Simulation is implemented with Python and Jupyter Notebook so the prerequisite for the project to run is Jupyter and Python are already installed.

### Repository Structure
- `montecarlo-notebook.ipynb` → Python simulation implementation  
- `README.md` → Project documentation  


Python Library Requirements:
```bash
python >= 3.9
numpy
pandas
matplotlib
```

Install them with:
```bash
pip install numpy pandas matplotlib kagglehub
```

### Running the Code

1. **Clone this repository**  
   ```bash
   git clone https://github.com/hilfritz/fan-replacement-prescriptive-analysis-montecarlo-simulation.git
   cd fan-replacement-prescriptive-analysis-montecarlo-simulation
   ```

2. **Open Jupyter Notebook**  
   ```bash
   jupyter notebook montecarlo-notebook.ipynb
   ```

3. **Run all cells** to simulate both policies.  

4. **Outputs include:**  
   - Per-event breakdowns of Fan, Labor, and Downtime costs.  
   - Per-run aggregates (total cost, downtime, operating horizon).  
   - KPI summaries comparing Current vs Proposed policies.

## Results & Recommendation
- **Current Policy (V1):** Mean Total Cost ≈ $21,108  
- **Proposed Policy (V2):** Mean Total Cost ≈ $11,563  
- **Savings:** ~45% lower under Proposed Policy  
- **Key Driver:** Major reduction in downtime costs  

**Recommendation:** Adopt the **Proposed Policy (V2)** — it delivers significant cost savings, more predictable performance, and reduced downtime.  

📓 *Note:* The **Jupyter Notebook (`montecarlo-notebook.ipynb`)** contains the full simulation outputs, including figures, event-level data, KPI breakdowns, and supporting analysis.


## Author
Hilfritz Camallere
A simple project to showcase Prescriptive Analysis to demonstrate use of Monte Carlo Simulation to identify optimal policy to save cost on fan replacements.

<!--
## 👥 Team
Group 6 – Prescriptive Analytics, University of Niagara Falls Canada  
- Hilfritz Camallere  
- Tiago Caramello Ceolato  
- Daniyal Nadeem Khan  
- Bruno Sassi
--> 
