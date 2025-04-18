# Biospecimen sample annotation system

This repository defines a standardized naming system for biospecimens used in genomic studies, including **patient-derived xenografts (PDX)**, **cell lines**, **normal tissues**, and **primary tumors**. The naming structure encodes key metadata about each sample’s origin, type, and processing history in a compact and interpretable format.

---
## 🧬 sample map


Below is an example of a properly structured shipping metadata table (`sample_shipping_frame.csv`) using the latest standardized column order:

| label       | date  | individual_id | nuc_id | specimenID             | parentBiospecimenID_WUSTL | tissue             | passage | tumorType                                | batch      | assay                    |
|-------------|-------|----------------|--------|-------------------------|-----------------------------|--------------------|---------|-------------------------------------------|------------|--------------------------|
| P001_PT     | 2504  | JH-2-001       | D1     | JH-2-001_2504D1         | JH-2-001-a_PT               | primary tumor      |         | Malignant Peripheral Nerve Sheath Tumor   | WU_batch4  | Whole Exome Sequencing   |
| P001_BLD    | 2504  | JH-2-001       | D2     | JH-2-001_2504D2         | JH-2-001-0_N                | blood              |         | Malignant Peripheral Nerve Sheath Tumor   | WU_batch4  | Whole Genome Sequencing  |
| P001_PDX0   | 2504  | JH-2-001       | D3     | JH-2-001_2504D3         | JH-2-001-a_PDX_MP0          | xenograft passage  | MP0     | Malignant Peripheral Nerve Sheath Tumor   | WU_batch4  | Whole Exome Sequencing   |
| P001_PATCL  | 2504  | JH-2-001       | R1     | JH-2-001_2504R1         | JH-2-001-b_PATCL_MP0        | cell line          | MP0     | Malignant Peripheral Nerve Sheath Tumor   | WU_batch4  | RNAseq                   |
| P001_PDXCL  | 2504  | JH-2-001       | R2     | JH-2-001_2504R2         | JH-2-001-a_PDXCL_MP1        | cell line          | MP1     | Malignant Peripheral Nerve Sheath Tumor   | WU_batch4  | RNAseq                   |

| Column Name                  | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `label`                     | Sample alias or code provided by the lab or shipping site. Used for tracking during submission. |
| `date`                      | Month and year of processing or shipping, in `MMYY` format (e.g., `2504` = April 2025). |
| `individual_id`             | Unique identifier for the patient or subject (e.g., `JH-2-001`). Consistent across all samples from the same individual. |
| `nuc_id`                    | Nucleic acid ID — either DNA (e.g., `D_1`) or RNA (e.g., `R_1`). Only one per row. |
| `specimenID`                | Unique barcode for the specimen: `<individual_id>-<date><nuc_id><random3digits>`. |
| `parentBiospecimenID_WUSTL`| Hierarchical ID showing sample source and derivation (e.g., `JH-2-001-a_PDX_MP0`). |
| `tissue`                    | Biological sample type: `primary tumor`, `blood`, `xenograft passage`, or `cell line`. |
| `passage`                   | Passage number (e.g., `MP0`, `MP1`) for PDX or cell lines. Leave blank for primary or normal samples. |
| `tumorType`                 | Full tumor diagnosis name (e.g., *Malignant Peripheral Nerve Sheath Tumor*, `normal`). |
| `batch`                     | Shipment or processing batch (e.g., `WU_batch4` for Washington University batch 4). |
| `assay`                     | Type of sequencing or profiling assay (e.g., `Whole Exome Sequencing`, `RNAseq`, `Whole Genome Sequencing`). |

## 🔍 speciman name 

The sample ID is composed of structured segments, separated by hyphens and underscores, with each part carrying specific biological or experimental meaning.


### parentBiospecimenID_WUSTL (tumor ID) :

### 📘 parentBiospecimenID_WUSTL Components

| Segment            | Example(s)                            | Description |
|--------------------|----------------------------------------|-------------|
| `JH-2-00x`         | JH-2-00x                               | **Individual ID** — unique identifier for the patient or donor |
| `a` or `0`         | `a`, `b`, `c` (tumor) or `0`, `1`, `2` (normal) | **Tumor Sequence Letter** — for **tumors**, lowercase letters (`a`, `b`, `c`, ...) represent the order of tumor collection (chronological or collection sequence).<br>For **normal tissues**, numeric values (`0`, `1`, `2`, ...) are used to indicate collection order. |
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


