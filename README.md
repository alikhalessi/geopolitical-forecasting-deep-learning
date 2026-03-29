# Geopolitical Forecasting with Deep Learning

An HPC-based deep learning forecasting pipeline for short-term geopolitical conflict intensity forecasting using GDELT data and CSC Puhti.

## Project Overview

This project investigates whether short-term Iran-related conflict intensity can be meaningfully forecast from recent GDELT patterns.

It also tests a broader methodological question:

**Does a larger dataset improve forecasting performance, or does a more focused and structured representation perform better?**

To answer this, the project compares two different approaches:

1. **Focused regional time-series modeling** using a GRU on a 10-country panel
2. **Large-scale document-level modeling** using an MLP on GKG-derived features

This repository is presented as a professional portfolio version of the project, focused on the pipeline, methodology, modeling logic, and representative outputs.

## Main Idea

The core comparison in this project is **structure vs. scale**.

- The focused setup uses a regional 10-country panel aggregated at 15-minute intervals
- The large-input setup uses a broader document-level GKG representation expanded into a large model-input dataset
- The central goal is to test whether a tightly scoped and task-aligned representation can outperform a much larger but noisier input for short-term forecasting

The key takeaway is that, for this task, a focused and structured representation performed better than a much larger document-level input.

## Problem Statement

Geopolitical event data is noisy, media-driven, and highly heterogeneous. GDELT is attractive because it is large, open, and fast-moving, but those same characteristics make modeling difficult.

This project focuses on a specific forecasting question:

**Can recent GDELT activity be used to forecast short-term Iran-related conflict intensity in a meaningful way?**

Rather than assuming bigger data is always better, the project explicitly tests whether better task alignment and subset design can produce stronger results.

## Data

- **Source:** GDELT
- **Temporal scope:** March 2026
- **Focused dataset:** Iran-centered 10-country regional panel
- **Aggregation:** 15-minute intervals
- **Large-input dataset:** document-level GKG-derived feature dataset
- **Large-input scale:** approximately 27.32 GiB in the full experiment

The project uses GDELT-derived signals related to conflict, media volume, and tone.

> Important: the forecasting target in this project is an **engineered future conflict intensity proxy**, not verified battlefield ground truth.

## Modeling Approaches

### 1) Focused Regional Model

The focused modeling path uses a structured regional panel and a **GRU regressor**.

Why GRU:
- the focused dataset is a time-series panel
- GRU is well suited to temporal dependencies and short-term sequential forecasting
- the data representation is compact, structured, and aligned with the forecasting task

Main characteristics:
- 10 selected countries in a regional context
- 15-minute temporal resolution
- sequence-based forecasting
- best-performing setup used a longer lookback window than the shorter baseline

### 2) Large-Input Comparison Model

The second modeling path uses a much larger document-level representation based on **GKG** and a **Multilayer Perceptron (MLP) regressor**.

Why MLP:
- the large-input experiment becomes a large tabular feature matrix rather than a clean country-time sequence
- the goal of this branch is to test scale directly
- this experiment acts as a structured comparison against the smaller focused representation

Main characteristics:
- document-level GKG-derived features
- large on-disk model input
- deep tabular regression setup
- used as a scale-vs-signal comparison

## Research Logic

This project is not just a forecasting exercise. It is also a test of a common machine learning assumption:

**If we increase data volume significantly, do we automatically improve results?**

This repository shows a case where the answer appears to be **no**.

For this specific Iran-related forecasting task, the more focused and structured setup performed better than the much larger and broader representation.

That suggests:

- subset relevance matters
- task alignment matters
- representation quality matters
- raw data volume alone is not enough

## Key Takeaway

The main result of the project is simple:

**For this forecasting problem, focused structure beat raw scale.**

The project supports the idea that a carefully designed regional panel can outperform a much larger but noisier document-level input when the target is narrow and context-specific.

## What This Repo Demonstrates

This repository demonstrates practical capability in:

- large-scale preprocessing of public geopolitical data
- feature engineering from event and media-derived signals
- time-series deep learning with GRU
- tabular deep learning with MLP
- comparative experiment design
- HPC-based workflow on CSC Puhti
- translating a course project into a portfolio-grade research engineering artifact
- reporting limitations honestly instead of overclaiming

- ## Reproducibility

This repository is presented as a **portfolio and research-engineering demonstration**.

The full experiment required HPC-scale storage and compute resources on CSC Puhti. For that reason:

- large raw datasets are not stored in this repository
- only lightweight samples and documentation are included
- the repo focuses on pipeline structure, methodology, and representative outputs

## Limitations

- The target is a **proxy signal**, not direct ground-truth conflict intensity
- GDELT reflects reported events and media structure, not pure battlefield reality
- This is an **exploratory forecasting pipeline**, not an operational intelligence system

## Slides

The project presentation is available in the `slides/` folder.

## Author

**Ali Khalessi**  
MBA + Big Data Analytics specialization  
Focused on applied machine learning, data engineering, and research-driven AI systems.

## Repository Structure

```text
.
├── data/               # sample data and notes
├── notebooks/          # cleaned demonstration notebooks
├── src/                # reusable pipeline scripts
├── results/            # figures, metrics, output tables
├── slides/             # presentation materials
└── docs/               # methodology and technical notes




