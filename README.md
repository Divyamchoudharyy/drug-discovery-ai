# BBBP Molecular Property Prediction — Scaffold vs. Random Split

Predicts blood-brain barrier permeability from molecular structure, and measures how much a naive train/test split overstates real performance compared to a scaffold-based split.

---

## What it does

- Loads the MoleculeNet BBBP dataset (2,050 compounds, binary permeability label)
- Generates Morgan fingerprints from SMILES using RDKit
- Trains a Random Forest classifier under two splitting strategies:
  - **Random split** — the naive default
  - **Scaffold split** — groups molecules sharing a Murcko scaffold onto the same side of the split, so the model can't see near-duplicate structures in both train and test
- Reports AUC, accuracy, and F1 for both, and the resulting gap
- Visualizes fingerprints in 2D via PCA (real PCA, not raw fingerprint bits)

## Result

Random split: **0.936 AUC**. Scaffold split: **0.884 AUC**. A ~0.05 AUC gap of optimism that a naive split hides — the model looks better than it actually generalizes to structurally new molecules.

A first attempt at the scaffold split (sorting scaffold groups by size before allocating to train/test) produced a test set that was 100% one class — non-permeable compounds in this dataset are concentrated in small, mostly singleton scaffolds. Shuffling the scaffold groups before allocation (fixed seed, standard practice) fixes this while keeping the split genuinely scaffold-based. Noting this here because it's a real property of the dataset, not swept under the rug.

## Setup

```bash
git clone https://github.com/Divyamchoudharyy/drug-discovery-ai.git
cd drug-discovery-ai
pip install -r requirements.txt
```

> RDKit install note — via conda for best results: `conda install -c conda-forge rdkit`

Dataset (`BBBP.csv`) is included in the repo.

Run:
```bash
jupyter notebook BBBP_scaffold_vs_random_split.ipynb
```

## Tech stack

- [RDKit](https://www.rdkit.org/) — fingerprints, scaffold extraction
- [Scikit-learn](https://scikit-learn.org/) — Random Forest, PCA, metrics
- [Pandas](https://pandas.pydata.org/) / [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)

## Planned extension

A message-passing graph neural network (ChemProp-style, PyTorch) trained on the same dataset and split, compared head-to-head against the Random Forest baseline above.

## License

MIT
