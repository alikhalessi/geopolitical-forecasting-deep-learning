# geopolitical-forecasting-deep-learning
HPC-based deep learning pipeline for short-term geopolitical forecasting with GDELT.
# Geopolitical Forecasting with Deep Learning

An HPC-based deep learning forecasting pipeline for short-term geopolitical conflict intensity forecasting using GDELT data and CSC Puhti.

## Project Overview

This project investigates whether short-term Iran-related conflict intensity can be meaningfully forecast from recent GDELT patterns. It also tests a broader methodological question:

**Does a larger dataset improve forecasting performance, or does a more focused and structured representation perform better?**

To answer this, the project compares two different approaches:

1. **Focused regional time-series modeling** using a GRU on a 10-country panel
2. **Large-scale document-level modeling** using an MLP on GKG-derived features

## Main Idea

The core comparison in this project is **structure vs. scale**.

- The focused setup uses a regional 10-country panel aggregated at 15-minute intervals.
- The large-input setup uses a much broader document-level GKG representation expanded into a large model-input dataset.

The key finding was that, for this task, the focused and structured representation performed better than the much larger document-level input.

## Data

- **Source:** GDELT
- **Temporal scope:** March 2026
- **Focused dataset:** Iran-centered 10-country regional panel
- **Large-input dataset:** document-level GKG-based feature dataset
- **Large-input scale:** approximately 27.32 GiB

> Note: the target in this project is an engineered future conflict intensity proxy derived from conflict-related and media-related signals. It is not verified battlefield ground truth.

## Models

### 1. Focused Model
- Model type: **GRU regressor**
- Purpose: learn temporal patterns from the structured regional time-series panel
- Best configuration: 7-day input window for next-step forecasting

### 2. Comparison Model
- Model type: **MLP regressor**
- Purpose: test whether a much larger document-level feature dataset improves performance
- Input: GKG-derived large-scale tabular feature representation

## Key Result

The project found that the focused regional GRU setup outperformed the much larger document-level MLP setup for the Iran-specific forecasting task.

This suggests that, in this problem setting, **task alignment, subset relevance, and structure mattered more than raw data volume alone**.

## What This Repo Demonstrates

- Large-scale preprocessing of public geopolitical data
- Feature engineering from event and media-derived signals
- Time-series deep learning with GRU
- Tabular deep learning with MLP
- Experimental comparison design
- HPC-based workflow on CSC Puhti
- Honest handling of modeling limitations

## Repository Structure

```text
.
├── data/               # sample data and data notes
├── notebooks/          # cleaned demo notebooks
├── src/                # reusable pipeline scripts
├── results/            # figures, metrics, output tables
├── slides/             # presentation materials
└── docs/               # methodology and technical notes
