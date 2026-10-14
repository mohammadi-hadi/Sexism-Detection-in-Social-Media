<div align="center">

# Sexism Detection in Social Media with Multilingual Transformer Ensembles

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8144300.svg)](https://doi.org/10.5281/zenodo.8144300)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

*Transformer-based detection and categorization of sexism in tweets, developed for the EXIST 2023 shared task at CLEF 2023.*

</div>

## Paper

|                  |                                                                          |
| ---------------- | ------------------------------------------------------------------------ |
| **Title**        | Towards Robust Online Sexism Detection: A Multi-Model Approach with BERT, XLM-RoBERTa, and DistilBERT for EXIST 2023 Tasks |
| **Authors**      | Hadi Mohammadi, Anastasia Giachanou, Robert A. Bagheri |
| **Affiliation**  | Department of Methodology and Statistics, Utrecht University, The Netherlands |
| **Venue**        | Working Notes of CLEF 2023 (CEUR Workshop Proceedings, Vol. 3497), pp. 1000–1011 |
| **Paper**        | [ceur-ws.org/Vol-3497/paper-085.pdf](https://ceur-ws.org/Vol-3497/paper-085.pdf) |
| **Code archive** | [10.5281/zenodo.8144300](https://doi.org/10.5281/zenodo.8144300) |

> This notebook is identical to the one in the [Exist-2023](https://github.com/mohammadi-hadi/Exist-2023) repository, which is the **primary home** of this code.

## Abstract

The EXIST 2023 shared task (sEXism Identification in Social neTworks) targets the identification and categorization of sexism in English and Spanish tweets across three subtasks: binary sexism identification, source-intention classification (direct, reported, or judgemental), and multi-label sexism categorization. Our approach combines three multilingual transformer encoders — BERT, XLM-RoBERTa, and DistilBERT — with a voting ensemble, on top of text preprocessing, data augmentation, and class-imbalance handling. Results on the official test set are reported in the [paper](https://ceur-ws.org/Vol-3497/paper-085.pdf).

## Citation

If you use this code, please cite:

```bibtex
@inproceedings{mohammadi2023towards,
  title     = {Towards Robust Online Sexism Detection: A Multi-Model Approach with BERT, XLM-RoBERTa, and DistilBERT for EXIST 2023 Tasks},
  author    = {Mohammadi, Hadi and Giachanou, Anastasia and Bagheri, Robert A.},
  booktitle = {Working Notes of CLEF 2023 -- Conference and Labs of the Evaluation Forum},
  series    = {CEUR Workshop Proceedings},
  volume    = {3497},
  pages     = {1000--1011},
  year      = {2023},
  url       = {https://ceur-ws.org/Vol-3497/paper-085.pdf}
}
```

---

## Overview

This repository holds the code of the M&S NLP team (Utrecht University) for **EXIST 2023** at CLEF 2023. The shared task covers three subtasks on English and Spanish tweets:

- **Task 1 — Sexism identification**: binary classification (sexist vs. non-sexist)
- **Task 2 — Source intention**: direct, reported, or judgemental
- **Task 3 — Sexism categorization**: multi-label classification over sexism categories

## Methods

Implemented in the notebook (TensorFlow/Keras + Hugging Face Transformers):

- **Preprocessing**: regex cleaning, NLTK tokenization, WordNet lemmatization
- **Class imbalance handling**: `nlpaug` augmentation, SMOTE / random oversampling, class weights
- **Models**: frozen `bert-base-multilingual-uncased`, `xlm-roberta-base`, and `distilbert-base-multilingual-cased` encoders with Keras classification heads
- **Ensemble voting** over the three models; TF-IDF + random forest baseline
- **Tuning and validation**: Keras Tuner random search, stratified k-fold cross-validation, early stopping
- **Submission output**: files with hard and soft labels in the EXIST evaluation format

## Quick Start

```bash
git clone https://github.com/mohammadi-hadi/Sexism-Detection-in-Social-Media.git
cd Sexism-Detection-in-Social-Media
pip install tensorflow transformers keras-tuner scikit-learn imbalanced-learn nlpaug nltk pandas numpy
jupyter notebook "M&S_NLP technical report for Exist 2023 (new version).ipynb"
```

Update the data paths at the top of the notebook to point to your local EXIST 2023 files. A GPU is recommended.

## Repository Structure

```
Sexism-Detection-in-Social-Media/
├── M&S_NLP technical report for Exist 2023 (new version).ipynb  # Main analysis notebook
├── CITATION.cff
├── LICENSE
└── README.md
```

## Data

The EXIST 2023 dataset is distributed by the task organizers and is **not included** here; see the [EXIST 2023 website](http://nlp.uned.es/exist2023/) for access conditions. The notebook expects local copies of the training/test JSON files and optionally an additional sexism dataset (`train_all_tasks.csv`) merged into training.

## Related Work

- [Exist-2023](https://github.com/mohammadi-hadi/Exist-2023) — primary home of this code (identical notebook)
- [Explainable-Sexism-Detection](https://github.com/mohammadi-hadi/Explainable-Sexism-Detection) — transparent sexism-detection pipeline with SHAP explanations (Applied Sciences, 2024)
- [MAP-PO](https://github.com/mohammadi-hadi/MAP-PO) — behavioral cluster-driven multi-agent preference optimization for sexism detection (EXIST 2024)

## License

MIT License — see [LICENSE](LICENSE).

## Contact

- **Hadi Mohammadi** — Utrecht University
- Website: [mohammadi.cv](https://mohammadi.cv)

## Acknowledgments

Thanks to the EXIST 2023 organizers for providing the dataset and evaluation framework, and to CLEF 2023 for hosting the shared task.
