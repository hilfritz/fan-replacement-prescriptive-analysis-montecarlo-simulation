# Cooling Fan Replacement Policy – Prescriptive Analysis 
- Determine the best policy to minimizes cost using Monte Carlo Simulation
## Table of Contents
- [Monte Carlo Simulation](#monte-carlo-simulation)
- [Problem Definition](#problem-definition)
- [Objective](#objective)
- [Variables & Distributions](#variables--distributions)

** Monte Carlo simulation** is a computational technique that uses repeated random sampling to
estimate the probability of different outcomes in a process that cannot easily be predicted
due to uncertainty.  
It is widely applied in decision-making and risk analysis because it allows us to model
complex systems, incorporate randomness, and assess the range of possible results.  

Monte Carlo simulation is not only a descriptive or predictive tool,  
it also supports **prescriptive analytics** by enabling decision-makers  
to compare alternative strategies under uncertainty.  
In this project, it is used to prescribe the most cost-effective cooling  
fan replacement policy for the data center.  


## Problem Definition
A data center relies on a server rack cooled by **three identical fans**.  
When a fan fails, the server shuts down and requires technician intervention.  

Two policies were evaluated:  
- **Current Policy (V1):** Replace only the failed fan.  
- **Proposed Policy (V2):** Replace all three fans whenever one fails.  

## Objective
The objective is to determine which policy minimizes total costs, using **Monte Carlo simulation** in **Python**.

---

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
