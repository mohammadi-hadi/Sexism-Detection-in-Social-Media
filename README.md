# Sexism Detection in Social Media

Transformer-based detection and categorization of sexism in tweets, developed for the EXIST 2023 shared task at CLEF 2023.

[Paper](https://ceur-ws.org/Vol-3497/paper-085.pdf) • [Code archive on Zenodo](https://doi.org/10.5281/zenodo.8144300) • [Website](https://mohammadi.cv)

## Overview

This repository holds the code of the M&S NLP team (Utrecht University) for **EXIST 2023** (sEXism Identification in Social neTworks), described in the CLEF 2023 working-notes paper *"Towards Robust Online Sexism Detection: A Multi-Model Approach with BERT, XLM-RoBERTa, and DistilBERT for EXIST 2023 Tasks"* by Hadi Mohammadi, Anastasia Giachanou, and Ayoub Bagheri.

The shared task covers three subtasks on English and Spanish tweets:

- **Task 1 — Sexism identification**: binary classification (sexist vs. non-sexist)
- **Task 2 — Source intention**: direct, reported, or judgemental
- **Task 3 — Sexism categorization**: multi-label classification over sexism categories

Note: this notebook is identical to the one in the [Exist-2023](https://github.com/mohammadi-hadi/Exist-2023) repository, which is the primary home of this code.

## Data

The EXIST 2023 dataset is distributed by the task organizers and is **not included** here; see the [EXIST 2023 website](http://nlp.uned.es/exist2023/) for access conditions. The notebook expects local copies of the training/test JSON files and optionally an additional sexism dataset (`train_all_tasks.csv`) merged into training.

## Methods

Implemented in the notebook (TensorFlow/Keras + Hugging Face Transformers):

- Text preprocessing (regex cleaning, NLTK tokenization, WordNet lemmatization)
- Class imbalance handling: `nlpaug` augmentation, SMOTE / random oversampling, class weights
- Frozen `bert-base-multilingual-uncased`, `xlm-roberta-base`, and `distilbert-base-multilingual-cased` encoders with Keras classification heads
- Ensemble voting over the three models; TF-IDF + random forest baseline
- Keras Tuner random search, stratified k-fold cross-validation, early stopping
- Submission files with hard and soft labels in the EXIST evaluation format

Results on the official test set are reported in the [paper](https://ceur-ws.org/Vol-3497/paper-085.pdf).

## Repository structure

```
Sexism-Detection-in-Social-Media/
├── M&S_NLP technical report for Exist 2023 (new version).ipynb  # Main analysis notebook
├── LICENSE
└── README.md
```

## How to run

```bash
git clone https://github.com/mohammadi-hadi/Sexism-Detection-in-Social-Media.git
cd Sexism-Detection-in-Social-Media
pip install tensorflow transformers keras-tuner scikit-learn imbalanced-learn nlpaug nltk pandas numpy
jupyter notebook "M&S_NLP technical report for Exist 2023 (new version).ipynb"
```

Update the data paths at the top of the notebook to point to your local EXIST 2023 files. A GPU is recommended.

## Citation

```bibtex
@inproceedings{mohammadi2023towards,
  title     = {Towards Robust Online Sexism Detection: A Multi-Model Approach with BERT, XLM-RoBERTa, and DistilBERT for EXIST 2023 Tasks},
  author    = {Mohammadi, Hadi and Giachanou, Anastasia and Bagheri, Ayoub},
  booktitle = {Working Notes of CLEF 2023 -- Conference and Labs of the Evaluation Forum},
  series    = {CEUR Workshop Proceedings},
  volume    = {3497},
  pages     = {1000--1011},
  year      = {2023},
  url       = {https://ceur-ws.org/Vol-3497/paper-085.pdf}
}
```

## Related work

- [Explainable-Sexism-Detection](https://github.com/mohammadi-hadi/Explainable-Sexism-Detection) — transparent sexism detection pipeline (Applied Sciences, 2024)

## License

MIT License — see [LICENSE](LICENSE).

For questions, see [mohammadi.cv](https://mohammadi.cv).
