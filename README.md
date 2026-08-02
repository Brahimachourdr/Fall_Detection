
# Repository Structure

This repository contains the dataset, the deep learning model training notebooks, the unified ablation study scripts, as well as the Python visualization pipeline and raw simulation data generated for analyzing wireless communication strategies (WBAN / IoT).

---

## 📂 Repository Layout
├── 01_Dataset/
│   ├── Local_Dataset/                # Triaxial accelerometer data converted into 2D spatio-temporal images (ESP32 / MPU-6050)
│   └── SisFall_Public_Benchmark/     # Resampled public SisFall benchmark dataset transformed into 2D spatio-temporal images
│
├── 02_Model_Training_Exp1_Exp2/
│   ├── exp1_train_and_visualizations.ipynb
│   ├── exp2_train_and_confidence_scores.ipynb
│   └── exp2_visualizations.ipynb
│
├── 03_Ablation_Study/
│   └── Model_Variants_and_Statistical_Tests.ipynb   # Single unified notebook for architectural variants & statistical testing
│
└── 04_Wireless_Communication_Analysis/
├── Simulation_Results/           # Raw CSV export files generated from OMNeT++ 6.3 / INET 4.5.4 simulations
└── Communication_Analysis.ipynb  # Python processing and plotting notebook (Throughput, Radio Duty Cycle, Latency, Data Volume)



---

## 🗂️ Detailed Directory Overview

### 📂 `01_Dataset/`
Contains the spatio-temporal image representation datasets used for deep learning model training, validation, and ablation testing:
* **`Local_Dataset/`:** Raw triaxial accelerometer data captured by the custom IoT edge system (ESP32 / MPU-6050) and transformed into 2D spatio-temporal image matrices.
* **`SisFall_Public_Benchmark/`:** Public SisFall benchmark dataset resampled and transformed following the exact same spatio-temporal imaging protocol.

### 📂 `02_Model_Training_Exp1_Exp2/`
Contains the Jupyter notebooks implementing the model training workflows, performance evaluations, and visual analytics for both main experiments:
* **`exp1_train_and_visualizations.ipynb`:** End-to-end pipeline for Experiment 1 (model training, evaluation metrics, and visual analytics for fall detection against standard everyday activities).
* **`exp2_train_and_confidence_scores.ipynb`:** Model training workflow and prediction confidence score generation for Experiment 2 (fall detection evaluated against 20 complex ADLs and 22 fall types).
* **`exp2_visualizations.ipynb`:** Model interpretability and feature analysis scripts for Experiment 2.

### 📂 `03_Ablation_Study/`
Contains a single, unified notebook for conducting the structural ablation study across both datasets:
* **`Model_Variants_and_Statistical_Tests.ipynb`:** Integrates the execution pipeline for all 4 architectural variants (ConvNeXt-Base baseline, +Bi-GRU layer, +Self-Attention, and the full proposed architecture with CBAM), along with automated statistical significance tests (Paired t-test, Wilcoxon signed-rank test, Cohen's *d* effect size).

> **Note on Codebase Annotations:** Some internal comments, class labels, and logs within the ablation study codebase use French annotations (e.g., `chute` denotes *Fall* and `autre` denotes *Other ADL activities*).

### 📂 `04_Wireless_Communication_Analysis/`
Contains the simulation output data and network performance visualization tools:
* **`Simulation_Results/` (.csv):** Directory housing the raw CSV output data exported from the OMNeT++ 6.3 / INET 4.5.4 simulation experiments, evaluating three wireless transmission strategies:
  1. High-frequency periodic transmission
  2. Variance-based adaptive transmission
  3. Postural transition-based event-driven transmission
* **`Communication_Analysis.ipynb`:** Python notebook for processing the raw CSV simulation logs, computing network metrics, and generating publication-ready plots for throughput, radio duty cycle, cumulative data volume, and end-to-end latency.
