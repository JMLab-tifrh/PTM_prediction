# Post-Translational Modification (PTM) Site Prediction

This repository contains machine learning models for predicting three types of post-translational modification (PTM) sites in protein sequences:
- **Acetylation**
- **Phosphorylation**
- **Ubiquitination**

## Repository Structure

```
.
├── Acetylation/
│   ├── *.ipynb           # Prediction notebook
│   ├── sample.fasta      # Example input file
│   └── *.pth             # Finetuned model
├── Phosphorylation/
│   ├── *.ipynb           # Prediction notebook
│   ├── sample.fasta      # Example input file
│   └── *.pth             # Pre-trained model
├── Ubiquitination/
│   ├── *.ipynb           # Prediction notebook
│   ├── sample.fasta      # Example input file
│   └── *.pth             # Pre-trained model
└── finetune.yml          # Conda environment file
```

## Setup

### Prerequisites
- Anaconda or Miniconda
- Python 3.x

### Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Create the conda environment:
```bash
conda env create -f finetune.yml
conda activate finetune
```

3. Launch Jupyter Notebook:
```bash
jupyter notebook
```

## Usage

### Input Format

Your input FASTA file must follow the same format as the provided `sample.fasta` files:

```
>tr|FASTA_1|PHOSPHORYLATION_TEST
MRFCPFAERTRLVLKAKGIRHEVININLKNKPEWFFKKNPFGLVPVLENSQGQLIYESAI
>sp|FASTA_2|PHOSPHORYLATION_TEST
MAEQSDEAVKYYTLEEIQKHNHSKSTWLILHHKVYDLTKFLEEHPGGEEVLREQAGGDAT
```

### Running Predictions

1. Navigate to the desired PTM directory (Acetylation, Phosphorylation, or Ubiquitination)
2. Place your FASTA file in the directory or update the file path in the notebook
3. Open and run the corresponding `*.ipynb` notebook
4. The prediction will generate two output files (see Output Format below)

### Output Format

Each prediction notebook generates two output files:

#### 1. Tab-separated file (`*.txt`)
Contains predicted PTM sites with four columns:

| Column | Description |
|--------|-------------|
| Sequence_ID | Identifier from the FASTA header |
| Position | 1-indexed position in the sequence |
| Residue | Amino acid at the predicted site |
| PTM type | Type of modification (Acetylation/Phosphorylation/Ubiquitination) |


#### 2. Full sequence prediction file (*.pkl)
Contains complete prediction labels for each sequence:
- Length matches the original protein sequence
- Residues predicted as PTM sites are labeled accordingly
- Non-PTM residues are labeled as `-100`

## Models

Each directory contains a pre-trained model optimized for its respective PTM type. The models have been trained on curated datasets of experimentally validated PTM sites.
