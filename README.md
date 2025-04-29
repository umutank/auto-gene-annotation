
# UniProt and GO Term Annotation Script

---

## Citation
If you use this script in your research, please cite:

> Umut Tank. (2025). UniProt and GO Term Annotation Script. GitHub Repository. Available at: [https://github.com/umutank/auto-gene-annotation.git]

---

## Overview
This Jupyter Notebook (`Uniprot GO terms final 2.ipynb`) provides a high-throughput pipeline for annotating gene symbols with comprehensive biological information using the UniProt and g:Profiler APIs.  
In addition to core annotations, it integrates domain descriptions, GO terms (via QuickGO/g:Profiler), pathway data, and custom proteomics-specific flags.

This tool is tailored for systems biology and omics researchers seeking functional annotation of protein datasets, especially in the context of proteomics, transcriptomics, and interactome studies.

---

## Features
- Automated annotations for input gene lists with:
  - **UniProt ID**, **protein names**, **function**, and **subcellular localization**.
  - **Pfam domain IDs**, **Pfam domain descriptions**, and **Pfam clan names**.
  - **Canonical isoform** information.
  - **GO terms** (Biological Process, Molecular Function, Cellular Component) from g:Profiler and/or QuickGO.
  - **Pathway memberships**: KEGG, Reactome, WikiPathways.
  - **Protein complexes**: CORUM.
  - **Name matching** consistency check.
  - **Sticky binder** and **background contamination flags** (e.g., EV LFQ/Control background flags).

- Output saved in Excel format with clear column organization.
- Modular code allows easy adaptation to new annotation sources.

---

## Requirements

Install required packages with:

```bash
pip install pandas requests gprofiler-official openpyxl
```

Tested on:
- Python 3.10+
- Jupyter Notebook

---

## Usage

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/your-repository.git
    ```

2. Prepare your input:
    - An Excel file (.xlsx) with a `"Gene names"` column containing gene symbols to be annotated.

3. Open the notebook:
    ```bash
    jupyter notebook "Uniprot GO terms final 2.ipynb"
    ```

4. Set the input file path inside the notebook:
    ```python
    input_file_path = "your_input_file.xlsx"
    ```

5. Run all cells sequentially to generate the output file.

---

## Output Description

The final output is an Excel file containing:

| Column | Description |
|--------|-------------|
| Gene names | Original gene symbol |
| UniProt ID | Accession number |
| Protein Description | Recommended protein name from UniProt |
| Function | Functional summary (UniProt) |
| Subcellular Location | Known or predicted cellular compartment |
| PFAM Domains | Domain IDs from Pfam |
| PFAM Descriptions | Domain function summaries |
| PFAM Clan Names | Pfam clan (if any) |
| GO:BP Terms | Biological process terms |
| GO:MF Terms | Molecular function terms |
| GO:CC Terms | Cellular component terms |
| REAC Terms | Reactome pathway annotations |
| KEGG Terms | KEGG pathway names |
| WP Terms | WikiPathways associations |
| CORUM Terms | Complex memberships from CORUM |
| Sticky Binder Flag | Indicates sticky background binders (if flagged) |
| EV LFQ Background Flag | Flag for enrichment in EV LFQ background |
| EV Control Background Flag | Flag for control background enrichment |
| Name Match Discrepancy | Notes discrepancies between UniProt and input gene names |

---

## How It Works

- **UniProt API** is queried using gene names to extract ID, protein info, localization, and domains.
- **Pfam domains** and **clan descriptions** are retrieved and matched.
- **g:Profiler** returns functional annotations (GO, KEGG, Reactome, WP, CORUM).
- **QuickGO (optional)** can validate or extend GO terms.
- Final dataset is merged and exported as a clean Excel file.

---

## Notes
- Ensure input has a column titled exactly `"Gene names"`.
- Some entries may lack annotations if not found in UniProt or g:Profiler.
- Custom background filtering (Sticky Binder/EV LFQ flags) is based on user-defined criteria (edit inside the script).
- Internet connection is required for API access.

---

## Future Improvements
- Support mixed UniProt IDs and gene names.
- Integrate disease annotations (e.g., DisGeNET).
- Add batch progress tracking and retry mechanisms.


