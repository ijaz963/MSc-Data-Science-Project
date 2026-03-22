# MSc-Data-Science-Project
Decoding Amoxicillin Resistance in E. coli via Graph Neural Networks (GNN)

📌 Project Overview
This project transitions from traditional tabular machine learning to Graph-based Topological Analysis to predict antibiotic resistance. By treating E. coli genomes and their accessory protein families (PGFams) as a Bipartite Graph, the model learns the "genetic neighborhoods" and mobile element clusters that drive Amoxicillin resistance.

Unlike standard models that treat genes as independent variables, this Graph Convolutional Network (GCN) leverages physical genomic connectivity to bridge the Genotype-Phenotype Gap.

🧬 Dataset & Features

Source: BV-BRC (Bacterial and Viral Bioinformatics Resource Center).

Samples: 2,481 clinical E. coli genomes.

Features: 14,608 unique Accessory Protein Families (PGFams).

Target: Binary classification (Susceptible vs. Resistant to Amoxicillin).

Graph Construction: A bipartite adjacency matrix where edges represent the presence of a PGFam within a genome.
🧠 Model Architecture

The model is built using PyTorch Geometric with a 2-layer GCN architecture:

Input Layer: 14,608 features $\rightarrow$ 64 Hidden Units.

Message Passing: GCNConv layers aggregate neighborhood features to identify resistance "toolkits."

Activation: ReLU with Dropout (0.5) to manage high-dimensional sparsity.

Output: LogSoftmax for phenotypic prediction

📊 Key Results:

Metric,   |   Score

Overall   |   Accuracy,67%

F1-Score  |  (Resistant),0.69

F1-Score  |  (Susceptible),0.65

The "Weapon vs. Shield" Discovery

Feature importance analysis revealed that the GNN independently identified a hierarchical defense strategy:

Primary Weapon: Class A Beta-lactamase (TEM family).

Maintenance Shield: Antigen 43 (Biofilm formation) and Aerobactin (Iron scavenging).
.

🖼️ Visualizations

1. Confusion Matrix
The model highlights the Genotype-Phenotype Gap, identifying "Silent Genes" (False Positives) and highlighting the role of the accessory genome vs. core-chromosomal mutations.

2. Bipartite Network Topology
The network visualization proves the "Topological Signature" of resistance:

Resistant Genomes: Form dense "Hubs" with high connectivity to mobile genetic elements.

Susceptible Genomes: Exhibit sparsity and lack the structural clusters required for phenotypic resistance.
🛠️ Installation & Usage

Requirements

pip install torch torch-geometric pandas numpy matplotlib scikit-learn
Run the Analysis
Clone the repository.

Open the Jupyter Notebook.

Ensure metadata and features files are in the /data directory.

Run all cells to train the GNN and generate visualizations.
🚀 Future Work
Explainable AI (XAI): Implementing GNNExplainer to isolate specific subgraphs for clinical lab validation.

Core Genome Fusion: Integrating SNPs and point mutations to resolve False Negatives.

Multi-Drug Expansion: Testing the GNN architecture on Ciprofloxacin and Gentamicin.

⚖️ Ethics & License

This project utilizes publicly available, anonymized clinical data from BV-BRC. No personally identifiable information (PII) is included.
Distributed under the MIT License.

Author: Ijaz Hussain

M.Sc. Data Science | University of Hertfordshire
