---
title: "Genomic Variant Classifier"
description: "A machine learning pipeline for classifying genomic variants from whole-exome sequencing data, built as my undergraduate dissertation project."
tags: ["Python", "PyTorch", "Bioinformatics", "scikit-learn"]
github: "https://github.com/clark-bai/genomic-variant-classifier"
date: 2025-06-01
featured: true
---

## Overview

My dissertation project explored whether deep learning could improve on traditional rule-based approaches for classifying genomic variants as pathogenic or benign. The pipeline takes annotated VCF files as input, extracts features from variant annotations and population frequency databases, and trains a neural network classifier.

## Approach

The project combined domain-specific feature engineering with a relatively straightforward model architecture. Key steps included:

- **Data preprocessing** — Parsed VCF files using Biopython, merged annotations from ClinVar and gnomAD, and handled class imbalance with SMOTE oversampling.
- **Feature extraction** — Combined conservation scores (CADD, GERP), allele frequencies, and functional impact predictions into a unified feature matrix.
- **Model** — A feedforward neural network in PyTorch with dropout regularisation, benchmarked against a random forest baseline in scikit-learn.
- **Evaluation** — 5-fold stratified cross-validation with precision-recall curves, since the dataset was heavily imbalanced toward benign variants.

## Outcome

The neural network achieved an AUROC of 0.94 on the held-out test set, outperforming the random forest baseline (0.89) and a rule-based ACMG classifier (0.82). The biggest gains came from incorporating population frequency features alongside conservation scores.

## Lessons learnt

- Class imbalance is the dominant challenge in variant classification — model architecture matters less than how you handle the data.
- Reproducibility requires discipline: I used Nextflow to orchestrate the full pipeline and pinned every dependency version.
- Writing the dissertation forced me to explain trade-offs clearly, which improved the code itself.
