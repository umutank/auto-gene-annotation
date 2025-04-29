
# UniProt and GO Term Annotation Script

## Overview
This Jupyter Notebook (`Uniprot GO terms final 2.ipynb`) provides an automated pipeline to annotate gene symbols with detailed biological information from the UniProt and g:Profiler databases.  
It is designed for researchers who need to enrich protein or gene lists with molecular function, biological processes, cellular components, pathway memberships, and protein complex participation.

This tool is especially useful for proteomics, transcriptomics, and functional genomics studies.

---

## Features
- Annotate gene lists with:
  - **Protein names**, **UniProt IDs**, and **functional descriptions** (from UniProt).
  - **Subcellular localization** and **Pfam domains** (from UniProt).
  - **GO terms**: Biological Process, Molecular Function, Cellular Component (from g:Profiler).
  - **Pathway memberships**: KEGG, Reactome, WikiPathways (from g:Profiler).
  - **Protein complexes**: CORUM complexes (from g:Profiler).
- Export the final annotated dataset as an Excel file.
- Fully automated querying and merging of results.
- Researcher-friendly, clean output.

---

## Requirements

You will need the following Python packages installed:

```bash
pip install pandas requests gprofiler-official openpyxl
```

Tested with:
- Python 3.10+
- Jupyter Notebook

---

## Usage

1. **Clone** this repository:
    ```bash
    git clone https://github.com/umutank/auto-gene-annotation.git
    ```

2. **Prepare your input**:
    - An Excel file containing a column `"Gene names"` with the gene symbols you wish to annotate.

3. **Open the notebook**:
    ```bash
    jupyter notebook "Uniprot GO terms final 2.ipynb"
    ```

4. **Modify the input path** inside the notebook:
    - Set `input_file_path` to the path of your input file.
    
5. **Run all cells**

6. **Retrieve your output**:
    - An Excel file will be generated, containing all annotations, including:
      - UniProt ID, Protein Name, Function, Localization, Pfam Domains
      - GO terms, Pathways, CORUM Complexes

---

## Example

### Input Format

| Gene names |
|------------|
| TP53       |
| EGFR       |
| GAPDH      |

### Output Format

| Gene names | UniProt ID | Protein names | Function | Subcellular Location | Pfam Domains | GO: Biological Process | GO: Molecular Function | GO: Cellular Component | KEGG Pathways | Reactome Pathways | WikiPathways | CORUM Complexes |
|------------|------------|---------------|----------|----------------------|--------------|-------------------------|-------------------------|-------------------------|----------------|-------------------|--------------|-----------------|
| TP53       | P04637     | Cellular tumor antigen p53 | Acts as a tumor suppressor | Nucleus | P53_tetramer (PF07710) | Apoptotic process | DNA binding | Nucleus | Apoptosis (hsa04210) | Signaling by TP53 | TP53 Network | p53 tetramer complex |

---

## How It Works

- **UniProt Query**:  
  For each gene symbol, the notebook queries UniProt REST API to retrieve functional, localization, and domain data.
  
- **g:Profiler Query**:  
  The notebook uses the g:Profiler API to fetch GO terms and pathway/complex annotations.

- **Data Merging**:  
  UniProt and g:Profiler results are merged into the original gene list.

- **Final Export**:  
  The enriched table is saved as a new Excel file.

---

## Notes
- Ensure that your input Excel file has a column named exactly `"Gene names"`.
- A working internet connection is required to query UniProt and g:Profiler APIs.
- If a gene symbol cannot be found in UniProt or g:Profiler, its annotations will be left blank.
- UniProt and g:Profiler APIs have usage limits; large datasets may require batching.

---

## Future Improvements
- Parallelization to speed up large-scale queries.
- Automatic handling of mixed UniProt IDs and gene symbols.
- Integration of additional annotation databases (e.g., DisGeNET, STRING).


## Citation
If you use this script in your research, please cite:

> Umut Tank. (2025). UniProt and GO Term Annotation Script. GitHub Repository. Available at: [https://github.com/umutank/auto-gene-annotation.git]

---
