---
title: "RNA-Seq Analysis Pipeline"
description: "A Nextflow pipeline for automated RNA-Seq analysis, from raw FASTQ files through to differential expression results."
tags: ["Nextflow", "Python", "R", "Bioinformatics", "Docker"]
github: "https://github.com/clark-bai/nf-rnaseq-pipeline"
date: 2025-03-15
featured: false
---

## Overview

A reproducible bioinformatics pipeline that automates the standard RNA-Seq workflow: quality control, trimming, alignment, quantification, and differential expression analysis. Built with Nextflow for portability and Docker containers for dependency management.

## Approach

- **Quality control** — FastQC reports with MultiQC aggregation, automated adapter trimming via Trimmomatic.
- **Alignment** — STAR aligner with a two-pass mapping strategy for improved splice junction detection.
- **Quantification** — featureCounts for gene-level counts, with an optional Salmon path for transcript-level estimates.
- **Differential expression** — DESeq2 in R, with automated report generation using R Markdown.
- **Orchestration** — Nextflow DSL2 with modular sub-workflows, configurable via a single params file.

## Outcome

The pipeline processes a typical 6-sample experiment in under two hours on a standard workstation. It has been tested on public GEO datasets and produces results consistent with published analyses. The modular design means individual steps (e.g. swapping STAR for HISAT2) can be changed without rewriting the pipeline.

## Lessons learnt

- Nextflow's resume functionality saves hours of re-computation when debugging late-stage steps.
- Containerising every tool eliminated the "works on my machine" problem that plagued earlier projects.
- Writing good pipeline documentation is as important as writing good pipeline code — future users (including yourself) will thank you.
