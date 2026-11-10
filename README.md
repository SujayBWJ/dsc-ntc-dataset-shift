# Lightweight and Explainable Network Traffic Classification under Dataset Shift: A Cross-Dataset Evaluation

> **Official Repository for the Mini Project:** *"Lightweight and Explainable Network Traffic Classification under Dataset Shift: A Cross-Dataset Evaluation"*

---

## Abstract

Network Traffic Classification (NTC) is a critical component of modern network management and security infrastructure. Traditional port-based and Deep Packet Inspection (DPI) methods have become increasingly ineffective due to widespread encryption, dynamic port allocations, and evolving traffic patterns. While deep learning models offer high classification capabilities, conventional architectures impose substantial computational overheads that restrict their deployment in edge environments.

This repository implements a lightweight 1-D Convolutional Neural Network (CNN) utilizing Depth-wise Separable Convolutions (DSC) alongside multi-scale Inception blocks ($B_1$ and $B_2$), Group Normalization, and Explainable AI (XAI) frameworks (LIME and SHAP). This project extends prior literature by conducting a controlled cross-dataset evaluation across heterogeneous traffic distributions (Unicauca, UTMobileTraffic2021, and an auxiliary 5G traffic dataset) to quantify predictive performance degradation, computational efficiency, and feature attribution stability under dataset shift.

---

## Objectives

1. **Model Implementation:** Implement the lightweight network traffic classification model based on Depth-wise Separable Convolutions (DSC) as proposed in the base paper.
2. **Feature Harmonization & Preprocessing:** Preprocess and harmonize compatible numerical network traffic features across selected public datasets, applying class-balancing strategies where required.
3. **Performance Evaluation:** Evaluate classification performance using Accuracy, Precision, Recall, and F1-Score under within-dataset and cross-dataset testing scenarios.
4. **Efficiency Benchmarking:** Quantify computational efficiency by profiling total trainable parameters, approximate Floating Point Operations (FLOPs), and CPU inference latency relative to a conventional CNN baseline.
5. **Explainability & Stability Analysis:** Apply LIME and SHAP to examine feature attribution consistency under dataset shift using a quantitative Top-$k$ Feature Overlap metric ($\mathcal{O}_k$).
6. **Feature Optimization:** Investigate SHAP-guided feature selection to determine whether input dimensionality reduction preserves classification accuracy while reducing computational requirements.

---

## System Architecture

```
+-----------------------------------------------------------------------+
|                       Network Traffic Datasets                        |
|             (Unicauca, UTMobileTraffic2021, 5G Traffic)               |
+-----------------------------------┬-----------------------------------+
                                    |
                                    v
+-----------------------------------------------------------------------+
|                             Preprocessing                             |
|       (Cleaning, Label Encoding, Feature Standardization, SMOTE)      |
+-----------------------------------┬-----------------------------------+
                                    |
                                    v
+-----------------------------------------------------------------------+
|          Lightweight 1-D CNN with Depth-wise Separable Convs          |
|            (DSC Modules, Inception B1/B2, Group Norm, GAP)            |
+-----------------------------------┬-----------------------------------+
                                    |
                                    v
+-----------------------------------------------------------------------+
|                         Traffic Classification                        |
+-------------------------┬───────────────────┬-------------------------+
                          |                   |
                          v                   v
+-----------------------------------+   +-------------------------------+
|       Performance Evaluation      |   |          XAI Analysis         |
| Acc, Prec, Rec, F1, Params, FLOPs |   |          (LIME & SHAP)        |
+-------------------------┬---------+   +----------------┬--------------+
                          |                              |
                          +--------------┬---------------+
                                         |
                                         v
+-----------------------------------------------------------------------+
|        Cross-Dataset Robustness & Explanation Consistency Analysis    |
+-----------------------------------------------------------------------+
```

---

## Repository Structure

```
├── data/
│   ├── raw/                  # Raw dataset files (Unicauca, UTMobileTraffic2021, 5G)
│   └── processed/            # Harmonized CSVs, serialized PyTorch tensors (.pt), summary metadata
├── models/
│   ├── lightweight_dsc.py    # PyTorch implementation of the 1-D DSC-CNN architecture
│   └── baseline_cnn.py       # Standard conventional 1-D CNN baseline model
├── utils/
│   ├── preprocess.py         # Data cleaning, canonical feature mapping, scaling, and SMOTE
│   └── metrics.py            # Profiling utilities (parameters, FLOPs, CPU inference time)
├── xai/
│   ├── lime_shap_eval.py     # LIME and SHAP feature attribution routines
│   └── consistency_check.py  # Top-k Feature Overlap (O_k) calculation under dataset shift
├── paper/
│   ├── main.tex              # IEEE format LaTeX manuscript
│   └── references.bib        # BibTeX reference database
├── train_and_eval.py         # Training pipeline, validation, and cross-dataset testing harness
├── requirements.txt          # Software dependencies
└── README.md                 # Project documentation
```

---

## Technical Specifications

### Hardware Requirements
* **Processor:** Intel Core i5 or above
* **RAM:** 16 GB recommended
* **Storage:** 10–20 GB available storage space
* **GPU:** Optional (Architecture is optimized for CPU execution)

### Software Dependencies
* **Operating System:** Windows / Linux
* **Programming Language:** Python 3.14
* **Deep Learning Framework:** PyTorch
* **Data Processing:** Scikit-learn, NumPy, Pandas, Imbalanced-learn
* **Explainable AI Tools:** SHAP, LIME
* **Profiling & Visualization:** thop, Matplotlib, Seaborn

---

## Installation and Execution

### 1. Environment Setup

Clone the repository and install required dependencies:

```bash
git clone https://github.com/SujayBWJ/dsc-ntc-dataset-shift.git
cd dsc-ntc-dataset-shift

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

pip install -r requirements.txt
```

### 2. Preprocessing and Data Harmonization

Process the raw data source files into standard continuous features, perform label encoding, execute train-test splits, apply SMOTE class balancing, and serialize PyTorch tensors:

```bash
python utils/preprocess.py
```

### 3. Model Training and Cross-Dataset Evaluation

Train the primary DSC-CNN and Baseline CNN models on the base dataset and perform cross-dataset evaluation across target traffic distributions:

```bash
python train_and_eval.py
```

### 4. Explainability Analysis

Extract feature attributions using LIME and SHAP, and compute the Top-$k$ Feature Overlap metric ($\mathcal{O}_k$):

```bash
python xai/lime_shap_eval.py
```

---

## Experimental Framework

### Evaluated Metrics
* **Classification Performance:** Accuracy, Precision, Recall, Macro F1-Score, Confusion Matrices.
* **Computational Efficiency:** Total Trainable Parameters, Floating Point Operations (FLOPs via `thop`), CPU Inference Latency (ms).
* **Explanation Consistency:** Top-$k$ Feature Overlap ($\mathcal{O}_k$) across source domain $\mathcal{D}_{\text{src}}$ and target domain $\mathcal{D}_{\text{tgt}}$:

$$\mathcal{O}_k(\mathcal{D}_{\text{src}}, \mathcal{D}_{\text{tgt}}) = \frac{|\mathbf{S}_{\text{src}}^k \cap \mathbf{S}_{\text{tgt}}^k|}{k} \times 100\%$$

---

## Project Contributors

**Department of Computer Science and Business Systems (CSBS)**  
*P.E.S. College of Engineering, Mandya – 571401*  
*(An Autonomous Institution Affiliated to VTU Belagavi)*

* **R. Sujay Bharadwaj** – USN: `4PS24CB043`
* **Sinchana K.** – USN: `4PS24CB050`
* **Pranav R.** – USN: `4PS24CB040`
* **P. Tanmay Shreesha** – USN: `4PS24CB034`

**Project Guide:** Mrs. Swathy Denesh, Assistant Professor, Department of CSBS.  
**Academic Year:** 2026 - 2027

---

## License

This project is licensed under the MIT License. Refer to the `LICENSE` file for details.