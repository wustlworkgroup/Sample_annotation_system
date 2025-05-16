# Biospecimen sample annotation system

This repository defines a standardized naming system for biospecimens used in genomic studies, including **patient-derived xenografts (PDX)**, **cell lines**, **normal tissues**, and **primary tumors**. The naming structure encodes key metadata about each sample’s origin, type, and processing history in a compact and interpretable format.

---
## 🧬 sample map

Below is an example of a properly structured shipping metadata table (`sample_shipping_frame.csv`) using the latest standardized column order and unique specimenID format:

| label       | individual_id | tumor_seq | date  | nuc_id | seq_ID | specimenID               | tissue             | passage | tumorType                                | parentBiospecimenID_WUSTL | batch      | assay                    |
|-------------|----------------|-----------|-------|--------|--------|---------------------------|--------------------|---------|-------------------------------------------|-----------------------------|------------|--------------------------|
| P001_PT     | JH-2-001       | a/a1/b/b1 | 2504  | D1     | S001   | JH-2-001-a_2504D1_S001    | primary tumor      |         | Malignant Peripheral Nerve Sheath Tumor   | JH-2-001-a_PT               | WU_batch4  | Whole Exome Sequencing   |
| P001_BLD    | JH-2-001       | 0         | 2504  | D2     | S002   | JH-2-001-0_2504D2_S002    | blood              |         | Malignant Peripheral Nerve Sheath Tumor   | JH-2-001-0_N                | WU_batch4  | Whole Genome Sequencing  |
| P001_PDX0   | JH-2-001       | a         | 2504  | D3     | S003   | JH-2-001-a_2504D3_S003    | xenograft passage  | MP0     | Malignant Peripheral Nerve Sheath Tumor   | JH-2-001-a_PDX_MP0          | WU_batch4  | Whole Exome Sequencing   |
| P001_PATCL  | JH-2-001       | b         | 2504  | R1     | S004   | JH-2-001-b_2504R1_S004    | cell line          | MP0     | Malignant Peripheral Nerve Sheath Tumor   | JH-2-001-b_PATCL_MP0        | WU_batch4  | RNAseq                   |
| P001_PDXCL  | JH-2-001       | a         | 2504  | R2     | S005   | JH-2-001-a_2504R2_S005    | cell line          | MP1     | Malignant Peripheral Nerve Sheath Tumor   | JH-2-001-a_PDXCL_MP1        | WU_batch4  | RNAseq                   |

### Column Definitions

| Column Name                  | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `label`                     | Sample alias or code provided by the lab or shipping site. Used for tracking. |
| `individual_id`             | Unique identifier for the patient or subject (e.g., `JH-2-001`).            |
| `tumor_seq`                 | Tumor sequence identifier (e.g., `a`, `b`, `0`), indicating sample version. |
| `date`                      | Month and year of extraction or shipment in `YYMM` format (e.g., `2504`).   |
| `nuc_id`                    | Nucleic acid ID (e.g., `D1` for DNA, `R1` for RNA).                         |
| `seq_ID`                    | Sequencing ID to uniquely track individual nucleic acid aliquots.           |
| `specimenID`                | Formatted ID: `<individual_id>-<tumor_seq>_<date><nuc_id>_<seq_ID>`.       |
| `tissue`                    | Sample source (e.g., `blood`, `primary tumor`, `xenograft passage`).       |
| `passage`                   | Passage number for PDX/cell lines (e.g., `MP0`). Leave blank otherwise.     |
| `tumorType`                 | Diagnosis (e.g., *Malignant Peripheral Nerve Sheath Tumor*, or `normal`).  |
| `parentBiospecimenID_WUSTL`| Original biospecimen tracking ID.                                           |
| `batch`                     | Processing batch name (e.g., `WU_batch4`).                                 |
| `assay`                     | Type of sequencing or analysis (e.g., `RNAseq`, `Whole Genome Sequencing`).|





### parentBiospecimenID_WUSTL (tumor ID) :

### 📘 parentBiospecimenID_WUSTL Components

| Segment            | Example(s)                            | Description |
|--------------------|----------------------------------------|-------------|
| `JH-2-00x`         | JH-2-00x                               | **Individual ID** — unique identifier for the patient or donor |
| `a` or `0`         | `a`,'a1', `b`, `c` (tumor) or `0`, `1`, `2` (normal) | **Tumor Sequence Letter** — for **tumors**, lowercase letters (`a`, `b`, `c`, ...) represent the order of surgery (a1/a2/a3 samples from each surgery).<br>For **normal tissues**, numeric values (`0`, `1`, `2`, ...) are used to indicate collection order. |
| `PDX`              | PDX, tumor, normal,PATCL,PDXCL         | **Tissue Type** — indicates the biological sample type, such as `PDX`, `cellline`, `tumor` (primary, recurrent, metastatic), or `normal`; PATCL: Cell line from patient Tumor; PDXCL: 
from PDX|
| `P0`               | P0, MP1, MP2                           | **Passage Number** — specifies the generation of the PDX or cell line (`P0`, `MP1`, `MP2`, etc.).<br>This segment is **omitted for primary tumors and normal tissue samples**. |


---
- **Tumor samples** are labeled using a **lowercase letter** (`a`, `b`, `c`, etc.) that reflects their **collection order**.
  - If multiple tumors are collected on the same day, the sequence is determined by the **order of collection**.
- **Normal tissue samples** are labeled using a **number** (`0`, `1`, `2`, etc.) that reflects the **order of normal sample collection**.
- **PDX and cell line samples** are labeled using their respective identifiers and include the **tumor sequence letter** (e.g., `a`, `b`) of their source tumor, allowing clear lineage tracking.
- This system ensures that **all biospecimens — tumors, normals, and derivatives — are traceable back to their primary source**, maintaining data integrity across studies and timepoints.

 
![Screenshot 2025-04-11 at 1 06 40 PM](https://github.com/user-attachments/assets/41d66505-61ae-4d23-ba2e-66801aca1b88)

---



## ✅ Benefits

- 🔗 Enables **easy linking** between paired tumors, PDXs, and cell lines  
- 🔍 Facilitates **unambiguous sample tracking** across platforms and studies  
- 🧪 Supports **longitudinal studies** and complex experimental designs

---

This convention provides a transparent and scalable framework for managing biospecimen metadata in translational and preclinical research.


