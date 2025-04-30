# Fuzzy-Searching
Fuzzy/Semantic Searching for PharmAlchemy, INFO 603 SP25
# PharmAlchemy Fuzzy Semantic Search Module

This tool enables fuzzy semantic search over curated datasets of genes, drugs, and diseases. It was developed to enhance user accessibility within the PharmAlchemy knowledge platform.

## Features
- Fuzzy matching using `SequenceMatcher` with adjustable thresholds
- Real-time search with confidence scoring
- Synonym-aware query expansion
- Modular design for adding new datasets
- Tkinter-based GUI

## Datasets
- `g_final.csv` — curated gene symbols and synonyms
- `DrugBank Structure Links.csv` — metadata for DrugBank compounds
- `HSDN-Symptoms-DO.tsv` — disease and symptom metadata

## Usage
```bash
python PhAlSemantic.py
