# Fuzzy-Searching
# PharmAlchemy Fuzzy Semantic Search Module

This tool enables fuzzy semantic search over curated datasets of genes, drugs, and diseases. It was developed to enhance user accessibility within the PharmAlchemy knowledge platform.

## 🔍 Features
- Fuzzy matching using `SequenceMatcher` with adjustable thresholds
- Real-time search with confidence scoring
- Synonym-aware query expansion
- Modular design for adding new datasets
- Tkinter-based GUI

## 📂 Datasets
- `g_final.csv`: Gene symbols, synonyms, UniProt IDs
- `DrugBank Structure Links.csv`: Names, formulas, InChI/SMILES, CIDs
- `HSDN-Symptoms-DO.tsv`: Symptoms, diseases, DOIDs

## 🚀 Usage
```bash
python PhAlSemantic.py
```
Select a dataset, choose the search field, and begin typing to receive live-ranked suggestions.

---

## 🧩 Adding a New Dataset

To add a new searchable dataset (e.g., pathways, enzymes):

1. **Prepare Your CSV/TSV File**
   - Ensure the file has **no null values** in searchable columns.
   - Format all string fields as **lowercase**, whitespace-trimmed.
   - Each row should represent a single entry.

2. **Create a Loader Function**
   Define a new function (e.g., `load_pathway_data`) in `PhAlSemantic.py` modeled after `load_gene_data`.

3. **Register the Dataset**
   Add a new entry to the `datasets` dictionary:
   ```python
   'Pathways': {
       'csv_filename': 'pathway_data.csv',
       'search_options': ['pathway_name', 'pathway_id'],
       'search_labels': ['Pathway Name', 'Pathway ID'],
       'load_function': load_pathway_data
   }
   ```

---

## ➕ Adding New Search Parameters

To allow searching by a new column (e.g., EC Number):

1. **Ensure the Column Exists**
   The field must be present and complete in the dataset.

2. **Add to Index**
   In the dataset loader function:
   ```python
   ec_index = {}
   for entry in candidate_data:
       ec = entry.get('EC_Number', '').lower()
       if ec:
           ec_index[ec] = entry
   indexes['EC_Number'] = ec_index
   ```

3. **Expose in UI**
   Add the column to `search_options` and `search_labels` in your dataset config.

---

## 📜 License
MIT License for code. Attribution required for datasets (e.g., DrugBank, DOID, etc.).

## 📘 Citation
If you use this tool, please cite the accompanying report:
"Enhancing Biomedical Data Accessibility via Modular Semantic Search: A Fuzzy Matching System for PharmAlchemy"
