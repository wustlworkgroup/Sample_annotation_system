# Biospecimen Naming Convention

This repository defines a standardized naming system for biospecimens used in genomic studies, including **patient-derived xenografts (PDX)**, **cell lines**, **normal tissues**, and **primary tumors**. The naming structure encodes key metadata about each sample’s origin, type, and processing history in a compact and interpretable format.

---

## 🔍 Sample Naming Logic

The sample ID is composed of structured segments, separated by hyphens and underscores, with each part carrying specific biological or experimental meaning.


### Components:

| Segment       | Description |
|---------------|-------------|
| `JH-2-002`    | **Individual ID** — unique identifier for the patient or donor |
| `a`           | **Tumor Sequence Letter** — represents the order of tumor collection (chronological by collection date or collection sequence) |
| `PDX`         | **Tissue Type** — sample type such as `PDX`, `cellline`, `tumor` |
| `P0`          | **Passage Number** — generation of the PDX or cell line (`P0`, `MP1`, `MP2`, etc.), will omit this if it is tumor |

---

## 🧬 Naming Principles

- **Tumor samples** are labeled using a **lowercase letter** (`a`, `b`, `c`, etc.) that reflects their **collection order**.
  - If multiple tumors are collected on the same day, the sequence is determined by the **order of collection**.
- **PDX and cell lines** are labeled using their own identifiers and include the **letter of the paired tumor**, allowing lineage tracking.
- This system ensures that all derived biospecimens are **traceable back to their primary source**, maintaining data integrity across studies and timepoints.

---

## ✅ Benefits

- 🔗 Enables **easy linking** between paired tumors, PDXs, and cell lines  
- 🔍 Facilitates **unambiguous sample tracking** across platforms and studies  
- 🧪 Supports **longitudinal studies** and complex experimental designs

---

This convention provides a transparent and scalable framework for managing biospecimen metadata in translational and preclinical research.


