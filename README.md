# Sexism Detection in Social Media - EXIST 2023

This repository contains our submission for the EXIST 2023 shared task on sexism detection and categorization in social media.

## Paper

**Title:** Multi-Model Detection and Classification Pipeline for Online Sexism

**Authors:** Hadi Mohammadi, Anastasia Giachanou, Ayoub Bagheri

**Affiliation:** Utrecht University, The Netherlands

**Venue:** CLEF 2023 - Conference and Labs of the Evaluation Forum

## Task Description

EXIST 2023 (sEXism Identification in Social neTworks) focuses on:
- **Task 1**: Binary sexism detection (sexist vs. non-sexist)
- **Task 2**: Sexism categorization (ideological, stereotyping, objectification, etc.)
- **Task 3**: Fine-grained sexism classification

## Approach

Our approach combines multiple models and techniques:

1. **Transformer Models**: BERT, RoBERTa, XLM-RoBERTa for multilingual support
2. **Ensemble Learning**: Combining predictions from multiple models
3. **Data Augmentation**: Handling class imbalance
4. **Explainability Analysis**: Understanding model decisions with SHAP/LIME

## Repository Contents

```
Sexism-Detection-in-Social-Media/
├── M&S_NLP technical report for Exist 2023.ipynb  # Main analysis notebook
└── README.md
```

## Results

Our system achieved competitive results on the EXIST 2023 benchmark across all three tasks.

## Citation

```bibtex
@inproceedings{mohammadi2023exist,
  title={Multi-Model Detection and Classification Pipeline for Online Sexism},
  author={Mohammadi, Hadi and Giachanou, Anastasia and Bagheri, Ayoub},
  booktitle={CLEF 2023 Working Notes},
  year={2023}
}
```

## Related Work

- [Explainable-Sexim-Detection](https://github.com/mohammadi-hadi/Explainable-Sexim-Detection) - Full Applied Sciences paper on transparent sexism detection
- This research is part of the PhD thesis "From Tokens to Thoughts: Explainable NLP for Understanding Large Language Models" by Hadi Mohammadi at Utrecht University (2025)

## License

MIT License

## Contact

- Hadi Mohammadi - [h.mohammadi@uu.nl](mailto:h.mohammadi@uu.nl)
- Website: [mohammadi-hadi.github.io](https://mohammadi-hadi.github.io)
