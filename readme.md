# Biospecimen Naming Convention

This repository defines a standardized naming system for biospecimens used in genomic studies, including **patient-derived xenografts (PDX)**, **cell lines**, **normal tissues**, and **primary tumors**. The naming structure encodes key metadata about each sample’s origin, type, and processing history in a compact and interpretable format.

---

## 🔍 Sample Naming Logic

The sample ID is composed of structured segments, separated by hyphens and underscores, with each part carrying specific biological or experimental meaning.


### Components:

### 📘 Tissue ID Components

| Segment            | Example(s)                            | Description |
|--------------------|----------------------------------------|-------------|
| `JH-2-00x`         | JH-2-00x                               | **Individual ID** — unique identifier for the patient or donor |
| `a` or `0`         | `a`, `b`, `c` (tumor) or `0`, `1`, `2` (normal) | **Tumor Sequence Letter** — for **tumors**, lowercase letters (`a`, `b`, `c`, ...) represent the order of tumor collection (chronological or collection sequence).<br>For **normal tissues**, numeric values (`0`, `1`, `2`, ...) are used to indicate collection order. |
| `PDX`              | PDX, tumor, normal,PATCL,PDXCL         | **Tissue Type** — indicates the biological sample type, such as `PDX`, `cellline`, `tumor` (primary, recurrent, metastatic), or `normal`; PATCL: Cell line from patient Tumor; PDXCL: 
from PDX|
| `P0`               | P0, MP1, MP2                           | **Passage Number** — specifies the generation of the PDX or cell line (`P0`, `MP1`, `MP2`, etc.).<br>This segment is **omitted for primary tumors and normal tissue samples**. |


---

 
![Screenshot 2025-04-11 at 1 06 40 PM](https://github.com/user-attachments/assets/41d66505-61ae-4d23-ba2e-66801aca1b88)



---


## 🧬 Naming Principles


- **Tumor samples** are labeled using a **lowercase letter** (`a`, `b`, `c`, etc.) that reflects their **collection order**.
  - If multiple tumors are collected on the same day, the sequence is determined by the **order of collection**.
- **Normal tissue samples** are labeled using a **number** (`0`, `1`, `2`, etc.) that reflects the **order of normal sample collection**.
- **PDX and cell line samples** are labeled using their respective identifiers and include the **tumor sequence letter** (e.g., `a`, `b`) of their source tumor, allowing clear lineage tracking.
- This system ensures that **all biospecimens — tumors, normals, and derivatives — are traceable back to their primary source**, maintaining data integrity across studies and timepoints.


---


## 🧬 Sample Shipping Frame for human/PDX samples (not for cell experiments)

Below is an example of a properly structured shipping metadata table (`sample_shipping_frame.csv`):

| name_from_you | dna_id | rna_id | batch    | individual_id | tissue             | passage | tumor_type                                | parentBiospecimenID | tumor_location | sex  | age_months |
|---------------|--------|--------|----------|----------------|---------------------|---------|---------------------------------------------|----------------------------|----------------|------|-------------|
| P001_PT       | D_1    |        | Batch_01 | JH-2-001       | primary tumor        |         | Malignant Peripheral Nerve Sheath Tumor     | JH-2-001-a_PT              | flank          | male | 120         |
| P001_BLD      | D_2    |        | Batch_01 | JH-2-001       | blood                |         | Malignant Peripheral Nerve Sheath Tumor     | JH-2-001-0_blood          | flank          | male | 120         |
| P001_PDX0     | D_3    |        | Batch_01 | JH-2-001       | xenograft passage    | MP0     | Malignant Peripheral Nerve Sheath Tumor     | JH-2-001-a_PDX_MP0         | flank          | male | 120         |
| P001_PATCL    |        | R_1    | Batch_01 | JH-2-001       | cell line            | MP0     | Malignant Peripheral Nerve Sheath Tumor     | JH-2-001-b_PATCL_MP0       | flank          | male | 120         |
| P001_PDXCL    |        | R_2    | Batch_01 | JH-2-001       | cell line            | MP1     | Malignant Peripheral Nerve Sheath Tumor     | JH-2-001-a_PDXCL_MP1       | flank          | male | 120         |

## 🧾 Column Descriptions

| Column Name                  | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `name_from_you`             | Sample name or ID as provided by the originating lab or sample preparation site. Used during submission or shipment. |
| `dna_id`                    | Unique identifier assigned to the DNA aliquot (e.g., `D_1`, `D_2`). Leave blank if not applicable. |
| `rna_id`                    | Unique identifier assigned to the RNA aliquot (e.g., `R_1`, `R_2`). Leave blank if not applicable. |
| `batch`                     | Shipment or experimental batch in which the sample was processed or sent.   |
| `individual_id`             | Unique subject or patient ID (e.g., `JH-2-001`). Consistent across all derived samples. |
| `tissue`                    | Type of biological material: `primary tumor`, `blood`, `xenograft passage`, or `cell line`. |
| `specimenPreparationMethod`| Method used to preserve or prepare the sample (e.g., `Frash Frozen`, FFPE). |
| `passage`                   | Passage number (e.g., `MP0`, `MP1`) for PDX or cell lines. Leave blank for primary/normal samples. |
| `tumor_type`                | Full tumor type name (e.g., *Malignant Peripheral Nerve Sheath Tumor*, *Plexiform Neurofibroma*, `normal`). |
| `parentBiospecimenID_WUSTL`| Hierarchical biospecimen ID describing origin, collection, and derivation (e.g., `JH-2-001-a_PDX_MP0`). |
| `vial`                      | Internal vial code (e.g., `n1`, `n2`); denotes different pieces or replicates of the same tumor. |
| `tumor_location`            | Anatomical source of the tumor (e.g., `flank`, `spine`, `peripheral blood`). |
| `sex`                       | Biological sex of the subject (`male`, `female`, `unknown`).                |
| `age_months`                | Age of the subject at time of sample collection, in months.                 |

## 🧾 Sample Barcodes

Each sample is also assigned a unique `parentBiospecimenID` to support tissue-specific tracking and anonymization. The `parentBiospecimenID` is constructed by combining:

- The `individualID` (e.g., `JH-2-002`)
- A **random alphanumeric suffix**, with length depending on the **sample type or batch**
- 'Aliquot_ID' is the vial information for the piece of sample that is sent for sequencing or other assay
---

### 🔤 Examples

| parentBiospecimenID          | Tumor_sample_barcode      | Description                                  |
|------------------------------|-------------------------- |----------------------------------------------|
| `JH-2-00x-0_blood`           | `JH-2-00x-QZ1UM`          | Normal sample (blood) from individual JH-2-00x |
| `JH-2-00x-1_adjtissue`       | `JH-2-00x-B23LG`          | Adjacent normal tissue from JH-2-00x         |
| `JH-2-00x-a_PT`              | `JH-2-00x-8WPAQ`          | Primary tumor "a" from JH-2-00x              |
| `JH-2-00x-b_RT`              | `JH-2-00x-L3Z59`          | Recurrent tumor "b" from JH-2-00x            |
| `JH-2-00x-c_MT`              | `JH-2-00x-X7U2D`          | Metastatic tumor "c" from JH-2-00x           |
| `JH-2-00x-a_PDX_MP2`         | `JH-2-00x-3JKV7WML`       | PDX from tumor "a", passage 2                |
| `JH-2-00x-b_cellline_MP1`    | `JH-2-00x-KD9N8XQZ`       | Cell line from tumor "b", passage 1          |

---



## ✅ Benefits

- 🔗 Enables **easy linking** between paired tumors, PDXs, and cell lines  
- 🔍 Facilitates **unambiguous sample tracking** across platforms and studies  
- 🧪 Supports **longitudinal studies** and complex experimental designs

---

This convention provides a transparent and scalable framework for managing biospecimen metadata in translational and preclinical research.


