# Drug Discovery AI — RDKit Molecular Clustering

ML pipeline for drug prediction using molecular fingerprints, KMeans clustering, and PCA visualization.

---

## What it does

- Generates Morgan fingerprints from SMILES molecular data using RDKit
- Finds optimal clusters using the Elbow method (KMeans)
- Visualizes molecular clusters in 2D using PCA
- Predicts potential drug candidates using Tanimoto similarity scoring
- Integrates with ChEMBL API for real-world drug database matching

---

## Setup

### 1. Clone the repo
```bash
git clone https://github.com/Divyamchoudharyy/drug-discovery-ai.git
cd drug-discovery-ai
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

> RDKit installation note — install via conda for best results:
> ```bash
> conda install -c conda-forge rdkit
> ```

### 3. Run the notebook
```bash
jupyter notebook enhanced_rdkit_clustering_analysis_3fp_final.ipynb
```

---

## Project Structure

```
drug-discovery-ai/
├── enhanced_rdkit_clustering_analysis_3fp_final.ipynb  ← main notebook
├── requirements.txt                                     ← dependencies
├── .gitignore
└── README.md
```

---

## How it works

1. 25 drug molecules are encoded as SMILES strings
2. Morgan fingerprints (radius=2, size=1024) are generated via RDKit
3. Elbow method determines the optimal number of KMeans clusters
4. PCA reduces fingerprint dimensions to 2D for visualization
5. For each cluster, 3 fingerprints are combined (bitwise OR)
6. Tanimoto similarity finds the closest matching drug candidate

---

## Sample Molecules Included

Aspirin, Ibuprofen, Caffeine, Morphine, Diazepam, Warfarin, and 19 more common drug compounds.

---

## Tech Stack

- [RDKit](https://www.rdkit.org/) — cheminformatics & fingerprint generation
- [Scikit-learn](https://scikit-learn.org/) — KMeans clustering & PCA
- [ChEMBL API](https://www.ebi.ac.uk/chembl/) — drug database
- [NumPy](https://numpy.org/) / [Pandas](https://pandas.pydata.org/) — data processing
- [Matplotlib](https://matplotlib.org/) — visualization
- [Jupyter Notebook](https://jupyter.org/) — interactive environment

---

## Team

Developed as part of B.Tech CSE project at VIT Bhopal University (March 2025)

- Divyam Choudhary (23BCE11129)
- Promal Sharma (23BCE10541)
- Girish Jaiswal (23BCE11257)
- Hogarth Neeraj (23BCE11101)
- Dev Maggo (23BCE11790)

---

## License

MIT
