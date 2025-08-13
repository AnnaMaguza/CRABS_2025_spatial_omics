# Cell2Location Setup Guide

This guide provides three different approaches for setting up and running Cell2Location analysis, each with distinct advantages and limitations.

## Option 1: Local Machine Environment

**Benefits:**
- Higher RAM availability for memory-intensive operations

**Limitations:**
- No GPU acceleration (longer training times)
- Requires reducing the number of epochs for feasible computation

### Environment Setup

Create and activate a new conda environment:

```bash
conda create -y -n cell2loc_env python=3.10
conda activate cell2loc_env
```

Install required packages:

```bash
pip install cell2location[tutorials]
pip install squidpy
pip install igraph leidenalg
pip install scvi-tools==1.2.0
pip install ipykernel
pip install torch==2.3.0 torchvision==0.18.0
```

Configure Jupyter kernel:

```bash
python -m ipykernel install --user --name cell2loc_env --display-name "Python (cell2loc_env)"
```

## Option 2: Google Colab

**Benefits:**
- GPU acceleration for faster model training

**Limitations:**
- RAM limited to 12GB in the free tier
- The "expected expression per cell type" computation step must be skipped due to memory constraints

### Getting Started

Access the tutorial directly through Google Colab:

[Cell2Location Tutorial](https://colab.research.google.com/drive/1EJJKcnPJ-rVgEOBx2zvO8wEDYSj9in08#scrollTo=06Fc_vHEaXap)

## Option 3: Hybrid Approach (Recommended)

**Benefits:**
- Combines GPU acceleration for training with sufficient RAM for downstream analysis
- Optimal resource utilisation

**Workflow:**
1. Train the model using Google Colab to leverage GPU acceleration
2. Download the trained model and AnnData objects to your local machine
3. Perform downstream analysis locally with full RAM availability
