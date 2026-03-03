# Beyond the Tap: KPT Optimization & Predictive Logistics 🚀

**Zomato Hackathon Submission - Track 1 (Kitchen Prep Time Optimization)**

This repository contains the data curation pipeline, machine learning models, and discrete-event simulations backing the **"Beyond the Tap"** architecture. Our solution addresses the fundamental "Garbage-In, Garbage-Out" problem of human-biased Food Order Ready (FOR) signals by introducing scalable, physics-informed Edge AI telemetry (Acoustic Load & Kinematic Chaos).

## 📊 Project Overview

Current KPT prediction models suffer from severe manual bias. Merchants frequently engage in "Proximity Tapping" (marking orders ready only when the rider is nearby) or "Batch Tapping."

Instead of trying to fix human behavior, this project proves mathematically that we can bypass it. By transforming existing Zomato merchant devices into passive environmental sensors, we can feed un-falsifiable, physical-world data directly into the KPT dispatch algorithms.

### Key Innovations Demonstrated in this Repo:

* **The KOT Acoustic Spooler:** Simulating the correlation between thermal printer acoustic spikes and true kitchen load (Omni-channel proxy).
* **Kinematic Chaos Index ($\kappa$):** Simulating device accelerometer variance and thermal drift to quantify real-time kitchen stress without relying on POS integrations.
* **Algorithmic De-Noising:** Using Random Forest regressors to filter out biased human inputs and predict True KPT.

---

## 📂 Repository Structure

```text
├── Zomato_Dataset.csv                  # The raw, open-source base dataset
├── Zomato_KPT_Optimization.ipynb       # Main Jupyter Notebook (Data pipeline, ML, and Simulation)
├── Wait_Time_Reduction_Chart.png       # Exported KDE plot of the wait-time reduction
└── README.md                           # Project documentation

```

---

## ⚙️ Data Methodology (The Curation Pipeline)

As actual KPT backend data is proprietary, we built a robust data engineering pipeline to simulate the business problem and mathematically validate our hardware solution:

1. **Base Data:** We ingested the open-source Zomato Delivery Dataset (~40,000 real-world delivery coordinate/timestamp rows).
2. **Ground Truth Extraction:** Calculated strict Ground Truth KPT by measuring the $\Delta t$ between `Time_Orderd` and `Time_Order_picked`, handling edge cases like post-midnight pickups.
3. **Bias Simulation:** Mathematically injected the exact problem Zomato faces by turning 30% of the simulated merchants into "Early Tappers" who systematically underreport prep times by 5-10 minutes.
4. **Signal Enrichment:** Feature-engineered our novel Edge AI telemetry—Acoustic Rush Scores and Kinematic Chaos Indices—mapping them logically to the underlying True KPT distribution.

---

## 🚀 How to Run the Simulation

The entire pipeline is self-contained within the Jupyter Notebook.

### Prerequisites

Ensure you have Python 3.8+ installed along with the following libraries:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn

```

### Execution Steps

1. Clone this repository:
```bash
git clone https://github.com/YourUsername/predictive-logistics-sim.git

```


2. Open the notebook:
```bash
jupyter notebook Zomato_KPT_Optimization.ipynb

```


3. **Run All Cells:** The notebook will automatically clean the timestamps, apply the bias simulation, generate the Edge AI sensors, train the Random Forest Regressor, and output the success metrics comparing the Baseline to the Optimized Architecture.

---

## 📈 Key Results & Impact Metrics

By training our predictive model on physics-informed edge signals rather than biased manual FOR taps, the simulation achieved the following reductions in Zomato's Success Metrics:

| Metric | Baseline (Manual FOR) | Optimized (Edge AI) | Net Improvement |
| --- | --- | --- | --- |
| **Average Rider Wait Time** | 2.21 mins | 0.96 mins | **56.5% Reduction** |
| **P90 ETA Prediction Error** | 7.18 mins | 4.10 mins | **42.8% Reduction** |
| **P50 ETA Prediction Error** | 2.09 mins | 1.55 mins | **25.8% Reduction** |
| **Mean Absolute Error (MAE)** | 2.77 mins | 1.90 mins | **31.4% Reduction** |

*Note: See the generated `Wait_Time_Reduction_Chart.png` in the repository for a visual density plot of how the architecture flattens the "fat tail" of extreme rider delays.*

---
