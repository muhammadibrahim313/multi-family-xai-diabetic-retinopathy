# A Clinically-Aligned Multi-Family Explainable AI Framework for Diabetic Retinopathy Detection on Fundus Images

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C.svg)](https://pytorch.org/)
[![Paper](https://img.shields.io/badge/Preprint-Preprints.org-orange)](https://www.preprints.org/)

Official implementation of the paper:

> **A Clinically-Aligned Multi-Family Explainable AI Framework for Diabetic Retinopathy Detection on Fundus Images**
> Muhammad Ibrahim Qasmi, Aqib Rehman Pirzada
> *Preprint, 2026*

---

## Overview

Automated diabetic retinopathy (DR) screening has reached expert-level accuracy, yet clinical adoption remains limited by the opacity of deep neural networks. This work addresses that gap by jointly delivering:

1. A **DenseNet121-based binary DR classifier** trained on 3,662 retinal fundus images from APTOS 2019, optimised through a two-phase transfer-learning and fine-tuning strategy, achieving **95.45% accuracy** and **0.9881 AUC-ROC**.
2. A **systematic benchmark of six explainable AI (XAI) methods** drawn from three theoretical families:
   - **Perturbation**: Occlusion Sensitivity, LIME, RISE
   - **Gradient**: Integrated Gradients
   - **Activation**: Grad-CAM++, Score-CAM
3. A **quantitative clinical-alignment evaluation** that measures each method's agreement with expert-annotated anatomical structures (optic disc, major vessels, macula) and lesion regions (microaneurysms, haemorrhages, exudates).

The six methods converge on clinically meaningful regions — 85% average agreement at the optic disc, 78% at major vessels, 66% at the macula — indicating that the network's decisions are grounded in established DR pathology rather than spurious correlations.

---

## Key Results

| Metric | Value | 95% CI |
|---|---|---|
| Accuracy | 95.45% | [93.41, 96.99] |
| Sensitivity | 93.91% | [90.54, 96.39] |
| Specificity | 95.94% | [93.01, 97.92] |
| AUC-ROC | 0.9881 | [0.9786, 0.9943] |
| Cohen's κ | 0.9090 | [0.8814, 0.9313] |

### XAI Method Comparison

| Method | Family | Time (s) | Memory (MB) | Mean IoU | Clinical Alignment |
|---|---|---|---|---|---|
| Grad-CAM++ | Activation | 0.82 | 423 | 0.171 | 83% |
| Integrated Gradients | Gradient | 1.01 | 567 | 0.175 | 85% |
| Score-CAM | Activation | 15.34 | 1456 | 0.165 | 79% |
| RISE | Perturbation | 9.72 | 987 | 0.155 | 81% |
| LIME | Perturbation | 12.43 | 1234 | 0.160 | 78% |
| Occlusion | Perturbation | 43.98 | 892 | 0.188 | 87% |

---

## Repository Status

🚧 **Active development.** Code release is being prepared in stages:

- [x] Initial notebook upload (training + XAI inference)
- [ ] Modular `src/` package (models, training, XAI methods, evaluation)
- [ ] Reproducibility scripts (one-line training and evaluation)
- [ ] Pre-trained model weights
- [ ] Sample inference demo
- [ ] Documentation site

The current `notebooks/` folder contains the main Jupyter notebook used to produce the paper's results. A complete, modular implementation will follow.

---

## Repository Structure

```clinically-aligned-xai-dr/
├── notebooks/
│   └── main_pipeline.ipynb        # End-to-end: training, evaluation, XAI
├── figures/                       # Paper figures (auto-generated)
├── results/                       # Evaluation logs and metrics (coming soon)
├── src/                           # Modular implementation (coming soon)
│   ├── models/
│   ├── training/
│   ├── xai/
│   └── evaluation/
├── requirements.txt               # Dependencies (coming soon)
└── README.md

---

## Dataset

This work uses the publicly available **APTOS 2019 Blindness Detection** dataset, released by the Asia Pacific Tele-Ophthalmology Society and hosted on Kaggle:

🔗 https://www.kaggle.com/competitions/aptos2019-blindness-detection

The original five-class severity labels (R0–R4) are collapsed into a binary referable-DR task. The dataset is split stratified into 70/15/15 train/validation/test (2,562 / 550 / 550 images).

Lesion-level masks used for the clinical-alignment evaluation are transferred from the **IDRiD lesion-segmentation benchmark** via SSIM matching; please see Section IV-A of the paper for full provenance.

---

## Quick Start

> ⏳ Full installation and training instructions will be added as the modular codebase is released. For now, the main pipeline notebook is self-contained and can be run end-to-end on Kaggle or any GPU-enabled Jupyter environment.

```bashClone the repository
git clone https://github.com/ibrahimqasmi313/clinically-aligned-xai-dr.git
cd clinically-aligned-xai-drOpen the notebook
jupyter notebook notebooks/main_pipeline.ipynb

---

## Citation

If you use this code or build on this work, please cite:

```bibtex@article{qasmi2026clinically,
title   = {A Clinically-Aligned Multi-Family Explainable AI Framework for Diabetic Retinopathy Detection on Fundus Images},
author  = {Qasmi, Muhammad Ibrahim and Pirzada, Aqib Rehman},
journal = {Preprints.org},
year    = {2026},
note    = {DOI will be added once preprint is approved}
}

The BibTeX entry above will be updated with the official DOI once the preprint is live on Preprints.org.

---

## License

This project is released under the MIT License — see [LICENSE](LICENSE) for details.

The APTOS 2019 dataset is governed by its own terms as specified by the Asia Pacific Tele-Ophthalmology Society and the Kaggle competition rules.

---

## Acknowledgements

We thank the **Asia Pacific Tele-Ophthalmology Society** for releasing the APTOS 2019 dataset, and the open-source community behind PyTorch, Captum, scikit-learn, scikit-image, and the original implementations of LIME, RISE, Grad-CAM++, and Score-CAM, on which this work builds.

---

## Contact

For questions, collaboration, or replication issues, please open an [issue](https://github.com/ibrahimqasmi313/clinically-aligned-xai-dr/issues) or reach out to:

- **Muhammad Ibrahim Qasmi** — [LinkedIn](https://www.linkedin.com/in/ibrahimqasmi313/) · `ibrahimqasmi@gpgcs.edu.pk`
- **Aqib Rehman Pirzada** — [LinkedIn](https://www.linkedin.com/in/aqibrehman-pirzada-ml/)
