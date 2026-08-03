# Repository Structure

This repository contains the deep learning model training notebooks, the unified ablation study scripts, the Python visualization pipeline, and raw simulation data generated for analyzing wireless communication strategies (WBAN / IoT).

> 📊 **Dataset Availability:**  
> The **Local Dataset** (raw triaxial accelerometer data captured by the custom ESP32/MPU-6050 IoT system and transformed into 2D spatio-temporal images) is hosted on Kaggle. The direct link to access and download this dataset is provided in the submitted paper.

---

## 🗂️ Detailed Directory Overview

### 📂 `01_Dataset/`
Contains the benchmark dataset setup and instructions used for deep learning model training, validation, and ablation testing:
* **`SisFall_Public_Benchmark/`:** Public SisFall benchmark dataset resampled and transformed following the exact same spatio-temporal imaging protocol.
* *(Note: To use the local dataset, please refer to the Kaggle link provided in the paper and place the downloaded files in your local directory).*

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

---

> 🌐 **Language Note:** The codebase and variable names are predominantly written in **English**. However, some internal print messages, console logs, comments, or class labels (e.g., `chute` for *Fall*, `autre` for *Other ADL*) may occasionally appear in **French**.
