# Biospecimen Naming Convention

This repository defines a standardized naming system for biospecimens used in genomic studies, including **patient-derived xenografts (PDX)**, **cell lines**, **normal tissues**, and **primary tumors**. The naming structure encodes key metadata about each sample’s origin, type, and processing history in a compact and interpretable format.

---

## 🔍 Sample Naming Logic

The sample ID is composed of structured segments, separated by hyphens and underscores, with each part carrying specific biological or experimental meaning.


### Components:

### Components

| Segment   | Example(s)     | Description |
|-----------|----------------|-------------|
| `JH-2-002` | JH-2-002       | **Individual ID** — unique identifier for the patient or donor |
| `a` or `0` | `a`, `b`, `c` (tumor) or `0`, `1`, `2` (normal) | **Tumor Sequence Letter** — for **tumors**, lowercase letters (`a`, `b`, `c`, ...) represent the order of tumor collection (chronological or collection sequence).<br>For **normal tissues**, numeric values (`0`, `1`, `2`, ...) are used to indicate collection order. |
| `PDX`     | PDX, cellline, tumor, normal | **Tissue Type** — indicates the biological sample type, such as `PDX`, `cellline`, `tumor` (primary), or `normal` |
| `P0`      | P0, MP1, MP2   | **Passage Number** — specifies the generation of the PDX or cell line (`P0`, `MP1`, `MP2`, etc.).<br>This segment is **omitted for primary tumors and normal tissue samples**. |


---

## 🧬 Naming Principles


- **Tumor samples** are labeled using a **lowercase letter** (`a`, `b`, `c`, etc.) that reflects their **collection order**.
  - If multiple tumors are collected on the same day, the sequence is determined by the **order of collection**.
- **Normal tissue samples** are labeled using a **number** (`0`, `1`, `2`, etc.) that reflects the **order of normal sample collection**.
- **PDX and cell line samples** are labeled using their respective identifiers and include the **tumor sequence letter** (e.g., `a`, `b`) of their source tumor, allowing clear lineage tracking.
- This system ensures that **all biospecimens — tumors, normals, and derivatives — are traceable back to their primary source**, maintaining data integrity across studies and timepoints.


---

## ✅ Benefits

- 🔗 Enables **easy linking** between paired tumors, PDXs, and cell lines  
- 🔍 Facilitates **unambiguous sample tracking** across platforms and studies  
- 🧪 Supports **longitudinal studies** and complex experimental designs

---

This convention provides a transparent and scalable framework for managing biospecimen metadata in translational and preclinical research.


