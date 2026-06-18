# LUAD-Transcriptomic--Severity-Classification
A Leakage-free hybrid ensemble framework (1D-CNN, XGBoost,TabPFN) utilizing a 4-stage feature selection funnel for high- dimensional TCGA-LUAD transcriptomic stage classification.
# 🧬 LUAD Transcriptomic Severity Classification

A leakage-free, hybrid ensemble framework for **lung adenocarcinoma (LUAD) stage classification** using high-dimensional RNA-Seq data from TCGA. This project integrates **advanced feature selection** and **heterogeneous deep learning models** to deliver biologically validated predictions for precision oncology.

---

## 📖 Introduction
Lung adenocarcinoma (LUAD) is the most prevalent subtype of non-small cell lung cancer (NSCLC) and a leading cause of cancer-related mortality worldwide. Accurate stratification between **early-stage (I/II)** and **late-stage (III/IV)** LUAD is critical for treatment planning, yet transcriptomic staging faces severe computational challenges:
- **High dimensionality** (>19,000 genes across 508 patient samples)  
- **Severe class imbalance** (398 early-stage vs. 110 late-stage instances)  
- **Feature redundancy & multicollinearity** - **Risk of data leakage** if data scaling or balancing is executed before splitting

This project implements a robust **four-stage hybrid funnel** for feature selection and a **heterogeneous ensemble** (1D-CNN, XGBoost, TabPFN) inside a strict stratified validation loop to overcome these systemic anomalies.

---

## 🔎 Feature Selection Workflow
The hybrid funnel drastically compresses the high-dimensional feature matrix without discarding critical multivariant genetic interactions:

```text
Raw RNA-Seq Data (19,188 genes)
       │
       ▼
ANOVA (FDR-corrected) ──> Filters statistically significant variance
       │
       ▼
ReliefF               ──> Captures multivariate interactions & non-linear dependencies
       │
       ▼
mRMR                  ──> Removes informational redundancy, maximizes relevance
       │
       ▼
Random Forest         ──> Establishes final biomarker importance ranking
       │
       ▼
Compact 150-Gene Signature (99.2% Dimensionality Reduction)
Model ArchitectureThe classification layer combines highly diverse mathematical frameworks into a unified predictive network:1D-CNN: Built to capture positional or structural pattern relationships within the engineered gene profiles, utilizing targeted Dropout (0.45) and L2 regularization to suppress overfitting.XGBoost: A gradient-boosted decision tree architecture utilized to trace sharp tabular splits and non-linear feature boundaries.TabPFN (Prior-Data Fitted Network): A cutting-edge, transformer-based foundation model designed for tabular data, approximating zero-shot Bayesian posterior inferences in a single forward pass.🛡️ Leakage Control & Balancing StrategyTo ensure true model validity on unseen data, SMOTETomek class balancing and feature engineering transformations are performed strictly within each training fold of a Stratified 5-Fold Cross-Validation loop. This shuts down data leakage vectors completely. The individual outputs are aggregated via a soft-voting ensemble.📊 Performance MetricsFinal cross-validated metrics on the TCGA-LUAD cohort:MetricValueClassification Accuracy77.45%Macro F1-Score0.4390Area Under the Curve (ROC-AUC)0.7347🔬 Biological ValidationFunctional enrichment analysis using KEGG pathways verified the clinical profile of the selected 150-gene signature.Highly significant tracking was confirmed for PD-L1 immune evasion mechanisms, KRAS oncogenic signaling pathways, and apical junction dynamics.Extracted a high-confidence consensus triad of biomarker genes: ONECUT1, CDK5R2, and IL9R.🚀 Key Engineering ContributionsZero-Leakage Guarantee: Developed an evaluation layout protecting baseline integrity across unseen validation data folds.99.2% Dimensionality Reduction: Structured a pipeline to collapse massive microarray feature spaces into crisp, actionable indicator panels.Transformer Foundation Integration: Early deployment of tabular foundation transformers (TabPFN) alongside classical boosting architectures.Biologically Actionable Output: Grounded machine learning performance metrics inside established cancer pathway realities.💡 Future ScopeMulti-Omics Fusion: Expanding the dataset matrices to include integrated copy number variations (CNV) and DNA methylation signatures.Clinical Deployment: Structuring the core Python pipeline code into a lightweight decision-support API layer accessible to oncologists.👩‍💻 AuthorKeerthana R Machine Learning Research Analyst | Precision Oncology Enthusiast LinkedIn Profile | Portfolio Page
