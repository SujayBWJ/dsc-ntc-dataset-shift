# Lightweight and Explainable Network Traffic Classification under Dataset Shift: A Cross-Dataset Evaluation

## Project Overview

Network Traffic Classification (NTC) identifies the type or application associated with network traffic and supports network management and security. Port-based classification and Deep Packet Inspection (DPI) become less effective with encrypted traffic, dynamically assigned ports, and changing traffic patterns. Deep learning can learn complex traffic patterns, but its computational requirements can limit use in resource-constrained or edge environments.

This project reproduces the lightweight CNN with Depth-wise Separable Convolutions (DSC) described in the selected base paper and extends its evaluation to dataset shift. It compares within-dataset and cross-dataset classification performance, computational efficiency, and the consistency of LIME and SHAP explanations across traffic distributions.

## Objectives

- Implement the lightweight network traffic classification model based on DSC from the selected base paper.
- Preprocess and standardize compatible features from the base and additional public datasets, and assess accuracy, precision, recall, and F1-score in within-dataset and cross-dataset tests.
- Assess computational efficiency using trainable parameters, approximate FLOPs, and CPU inference time.
- Apply LIME and SHAP to explain predictions and investigate whether important features remain consistent under dataset shift.
- Analyze the relationship between lightweight computation, classification performance, cross-dataset robustness, and explainability.
- Investigate SHAP-guided feature selection to assess whether reducing input features can improve computational efficiency while maintaining classification performance and explanation quality.

## Proposed System and Methodology

The project extends the base paper's lightweight CNN and evaluates it across traffic datasets rather than replacing it with a different model.

1. **Dataset selection:** Use the Unicauca and UTMobileTraffic2021 datasets studied in the base paper, subject to availability. Examine an additional publicly available 5G traffic dataset for cross-dataset evaluation.
2. **Preprocessing:** Remove unusable or null features, encode labels, select common numerical features, standardize features, and handle class imbalance using an appropriate strategy.
3. **Lightweight model:** Implement the base paper's lightweight 1-D CNN using Depth-wise Separable Convolutions, Inception blocks B1 and B2, Group Normalization, ReLU activation, average pooling, dropout, and a final classification layer.
4. **Baseline:** Implement a conventional CNN with a comparable training setup.
5. **Evaluation:** Conduct within-dataset experiments and cross-dataset testing. Record accuracy, precision, recall, F1-score, confusion matrices, and class-wise performance.
6. **Efficiency analysis:** Measure trainable parameters, approximate FLOPs, and CPU inference time under the same hardware and software environment.
7. **Explainability and dataset-shift analysis:** Apply LIME and SHAP to representative correctly and incorrectly classified samples. Compare predictive performance and feature-attribution patterns across datasets, using a simple top-k feature-overlap measure as an exploratory indicator of explanation consistency.
8. **Result analysis:** Identify where the lightweight model generalizes or degrades, relate changes to dataset characteristics, and document limitations and possible future improvements.

## Tools and Requirements

### Hardware

- Intel Core i5 or above
- 16 GB RAM recommended
- At least 10–20 GB free storage for datasets and experiments
- GPU optional; the lightweight model's experiments are designed to remain feasible on CPU

### Software

- Windows or Linux
- Python 3.14
- PyTorch
- Scikit-learn, NumPy, and Pandas
- SHAP and LIME
- Matplotlib and Seaborn
- Jupyter Notebook or VS Code
- Git and GitHub

## Project Timeline

| Phase | Planned work | Duration |
|---|---|---|
| 1 | Literature survey, base-paper study, and dataset investigation | Weeks 1–2 |
| 2 | System design, feature harmonization, and experiment protocol | Week 3 |
| 3 | Dataset preprocessing and lightweight CNN implementation | Weeks 4–5 |
| 4 | Baseline CNN implementation and within-dataset experiments | Week 6 |
| 5 | Cross-dataset experiments and efficiency measurements | Week 7 |
| 6 | LIME/SHAP analysis, explanation-consistency analysis, and result validation | Week 8 |
| 7 | Documentation, paper preparation, and final presentation | Week 9 |

## Project Team

Department of Computer Science and Business Systems

P.E.S. College of Engineering, Mandya – 571401

Academic Year: 2026–27

- R. Sujay Bharadwaj — 4PS24CB043
- Sinchana K. — 4PS24CB050
- Pranav R. — 4PS24CB040
- P. Tanmay Shreesha — 4PS24CB034

**Project Guide:** Mrs. Swathy Denesh, Assistant Professor

## References

1. M. Ghaleb, M. Hamdan, A. Y. Barnawi, M. Gambo, A. Danasabe, S. Bello, and A. Habib, “Explainable AI for Lightweight Network Traffic Classification Using Depthwise Separable Convolutions,” *IEEE Open Journal of the Computer Society*, vol. 6, pp. 908–920, 2025. DOI: 10.1109/OJCS.2025.3576495.
2. Z. Li, L. Bu, Y. Wang, Q. Ma, L. Tan, and F. Bu, “Hierarchical Perception for Encrypted Traffic Classification via Class Incremental Learning,” *Computers & Security*, vol. 149, 104195, 2025. DOI: 10.1016/j.cose.2024.104195.
3. A. Nascita, G. Aceto, D. Ciuonzo, A. Montieri, V. Persico, and A. Pescapé, “A Survey on Explainable Artificial Intelligence for Internet Traffic Classification and Prediction, and Intrusion Detection,” *IEEE Communications Surveys & Tutorials*, vol. 27, no. 5, pp. 3165–3198, 2025. DOI: 10.1109/COMST.2024.3504955.
4. Z. Li, Y. Liu, C. Zhang, W. Shan, H. Zhang, and X. Zhu, “Trustworthy Deep Learning for Encrypted Traffic Classification,” *Soft Computing*, vol. 29, no. 2, pp. 645–662, 2025. DOI: 10.1007/S00500-025-10462-W.
5. Z. Li, H. Zhao, J. Zhao, Y. Jiang, and F. Bu, “SAT-Net: A Staggered Attention Network Using Graph Neural Networks for Encrypted Traffic Classification,” *Journal of Network and Computer Applications*, vol. 233, 104069, 2025. DOI: 10.1016/j.jnca.2024.104069.
6. A. H. Haris, A. Ariffin, F. Zaki, and N. B. Anuar, “Lightweight Deep Learning-Based Network Traffic Classification Using Explainable Artificial Intelligence,” 2024 IEEE International Conference on Computing (ICOCO), 2024. DOI: 10.1109/ICOCO62848.2024.10928266.
7. P. Khani, E. Moeinaddini, N. D. Abnavi, and A. Shahraki, “Explainable Artificial Intelligence for Feature Selection in Network Traffic Classification: A Comparative Study,” *Transactions on Emerging Telecommunications Technologies*, vol. 35, no. 4, e4970, 2024. DOI: 10.1002/ett.4970.
8. A. Zou, W. Yang, C. Tang, J. Lu, and J. Guo, “A Novel and Effective Encrypted Traffic Classification Method Based on Channel Attention and Deformable Convolution,” *Computers & Electrical Engineering*, vol. 118, 109406, 2024. DOI: 10.1016/j.compeleceng.2024.109406.
9. J. Cui, L. Bai, X. Zhang, Z. Lin, and Q. Liu, “The Attention-Based Autoencoder for Network Traffic Classification with Interpretable Feature Representation,” *Symmetry*, vol. 16, no. 5, 589, 2024. DOI: 10.3390/sym16050589.
10. J.-T. Park, C.-Y. Shin, U.-J. Baek, and M.-S. Kim, “Fast and Accurate Multi-Task Learning for Encrypted Network Traffic Classification,” *Applied Sciences*, vol. 14, no. 7, 3073, 2024. DOI: 10.3390/app14073073.
