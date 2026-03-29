# Geopolitical Forecasting with Deep Learning

HPC-based deep learning pipeline for short-term geopolitical forecasting with GDELT.

## Overview

This project explores whether short-term Iran-related conflict intensity can be meaningfully forecast from recent GDELT patterns using deep learning.

The core methodological question is simple:

**Does a larger dataset improve forecasting, or does a more focused and structured representation perform better?**

To test that, the project compares two different approaches:

1. **Focused regional time-series modeling** using a GRU on a 10-country panel
2. **Large-scale document-level modeling** using an MLP on GKG-derived features

## Main Idea

The central comparison in this project is:

**structure vs. scale**

- The focused setup uses a regional 10-country panel aggregated at 15-minute intervals
- The large-input setup uses a much broader document-level GKG representation expanded into a large model-input dataset
- The project evaluates which representation is more effective for the forecasting task

## Data

- **Source:** GDELT
- **Temporal scope:** March 2026
- **Focused dataset:** Iran-centered 10-country regional panel
- **Large-input dataset:** document-level GKG-based feature dataset
- **Large-input scale:** approximately 27.32 GiB

> **Important:**  
> The prediction target in this project is an **engineered future conflict intensity proxy**, not verified battlefield ground truth.  
> This repository presents an exploratory research-engineering pipeline, not an operational intelligence system.

## Models

### 1. Focused Model
- **Model type:** GRU regressor
- **Purpose:** learn temporal patterns from the structured regional time-series panel
- **Best setup:** 7-day input window for short-term forecasting

### 2. Comparison Model
- **Model type:** MLP regressor
- **Purpose:** test whether a much larger document-level feature dataset improves performance
- **Input:** GKG-derived large-scale tabular feature representation

## Results Snapshot

The main result of the project is that the **focused regional GRU setup outperformed the much larger document-level MLP setup** for the Iran-specific forecasting task.

This suggests that, for this problem, **task alignment, subset relevance, and structure mattered more than raw data volume alone**.

A fuller comparison summary is provided in the `results/` folder.

## What This Repository Demonstrates

- Large-scale preprocessing of public geopolitical data
- Feature engineering from event and media-derived signals
- Time-series deep learning with GRU
- Tabular deep learning with MLP
- Comparative experimental design
- HPC-based workflow on CSC Puhti
- Honest documentation of modeling limitations

## Repository Structure

```text
.
├── data/               # sample data and data notes
├── docs/               # methodology and technical notes
├── notebooks/          # cleaned demo notebooks
├── results/            # figures, tables, and representative outputs
├── slides/             # presentation materials
└── src/                # reusable pipeline scripts
```
## How to Navigate This Repo

- Start with **`docs/methodology.md`** for the project logic and workflow
- Check **`slides/`** for the presentation version of the project
- See **`results/`** for model comparison artifacts
- Explore **`notebooks/`** for cleaned demonstration notebooks
- Use **`src/`** for reusable code components

## Reproducibility

This repository is presented as a **portfolio and research-engineering demonstration**.

The full experiment required HPC-scale storage and compute resources on CSC Puhti. For that reason:

- large raw datasets are **not** stored in this repository
- only lightweight samples and documentation are included
- the repo focuses on pipeline structure, methodology, modeling logic, and representative outputs

## Limitations

- The target is a **proxy signal**, not direct ground-truth conflict intensity
- GDELT reflects reported events and media structure, not pure battlefield reality
- This is an **exploratory forecasting pipeline**, not a production or operational forecasting system

## Project Status

This repository is being cleaned and documented into a professional portfolio edition.

Current focus:

- documentation
- reproducibility notes
- representative outputs
- polished notebooks and scripts

## Author

**Ali Khalessi**  
MBA + Big Data Analytics specialization  
Focused on applied machine learning, data engineering, and research-driven AI systems.
