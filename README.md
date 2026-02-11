
# Signal Peptide Prediction: Classical vs Machine Learning vs Deep Learning

This project was developed as part of the Laboratory of Bioinformatics 2 course 2024/2025 for the Master’s degree in Bioinformatics at the University of Bologna. It focuses on the computational prediction of signal peptides (SPs)—short N-terminal sequences that act as "zip codes" to direct proteins to their correct cellular destinations.

## Project description

This project investigates and compares three computational approaches for **signal peptide prediction in eukaryotic protein sequences**, progressing from classical statistical methods to modern deep learning architectures. The goal is to evaluate how increasingly sophisticated models impact predictive performance.

The following methods are implemented and benchmarked:

* **Von Heijne (Position-Specific Weight Matrix)**
  A classical statistical approach that models conserved motifs around signal peptide cleavage sites using a PSWM.

* **Support Vector Machine (SVM)**
  A supervised machine learning classifier trained on engineered features, including amino acid composition and physicochemical properties such as hydrophobicity and charge.

* **Multi-Layer Perceptron (MLP) with ESM-2 embeddings**
  A deep learning approach leveraging transformer-based protein language model embeddings (ESM-2) to encode sequences in a high-dimensional, information-rich space.


## Data and Methodology

### Dataset

* Source: **UniProtKB/Swiss-Prot (release 2024_04)**
* Only manually reviewed, high-quality eukaryotic protein sequences were used.

### Redundancy Reduction

To avoid overfitting and ensure unbiased evaluation:

* Redundancy was reduced using **MMSeqs2**
* Sequence identity threshold: **30%**
* Result: balanced training and benchmark datasets

### Model Optimization

All models were evaluated using **5-fold cross-validation**.

* **SVM**

  * Hyperparameters optimized via grid search
  * Tuned parameters:

    * Regularization parameter `C`
    * Kernel coefficient `γ`

* **MLP**

  * Architecture optimized via random search
  * Tuned parameters include:

    * Number of hidden layers
    * Number of neurons per layer
    * Dropout rates


## Results

The comparative analysis reveals a clear performance hierarchy:

1. **Von Heijne PSWM** provides a solid historical baseline.
2. **SVM** improves performance through supervised learning and engineered features.
3. **MLP with ESM-2 embeddings** significantly outperforms both traditional approaches.

These results demonstrate the effectiveness of **protein language models** in capturing complex, context-dependent biological patterns that are difficult to encode manually. Transformer-based embeddings such as ESM-2 enable substantially more accurate signal peptide prediction.


## Technical Implementation

The repository is implemented in **Python** and integrates the following libraries:

* **Biopython & Pandas**
  Sequence parsing, preprocessing and dataset management

* **Scikit-learn**
  Feature-based modeling, SVM implementation and evaluation

* **Hugging Face Transformers**
  Extraction of protein embeddings using the **ESM-2** model

* **PyTorch**
  Design, training and optimization of the MLP neural network


## Conclusion

This project highlights the evolution of signal peptide prediction methods and demonstrates how deep learning, particularly transformer-based protein representations, provides a substantial performance advantage over classical and feature-engineered approaches.

