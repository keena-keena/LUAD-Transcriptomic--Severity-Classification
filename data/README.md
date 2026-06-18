This folder notes guidelines for TCGA LUAD transcriptomic data storage.
# 📂 TCGA-LUAD Dataset Reference & Guidelines

Due to GitHub file size limitations (<100MB) and strict data utilization policies regarding clinical cohorts, the raw and preprocessed transcriptomic matrices are not hosted directly within this repository. 

### 📥 Data Acquisition Requirements
To fully execute the replication pipeline, download the original source files directly from the open-access tier of **The Cancer Genome Atlas (TCGA)** via the Genomic Data Commons (GDC) portal or cBioPortal:

1. **Transcriptomic Expression Profile:** `data_mrna_seq_v2_rsem.txt` (~19,188 protein-coding genes mapped by Hugo Symbols).
2. **Clinical Patient Metadata Registry:** `data_clinical_patient.txt` (Containing longitudinal data including pathologic staging configurations).

### 🛠️ Local Execution Directory Mapping
Once extracted, place the uncompressed `.txt` matrices within this directory matching the layout structure below:

```text
data/
├── LUAD/
│   ├── data_mrna_seq_v2_rsem.txt
│   └── data_clinical_patient.txt
└── README.md
