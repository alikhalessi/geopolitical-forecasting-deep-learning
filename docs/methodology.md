# Methodology

## Objective

The goal of this project was to investigate whether short-term Iran-related conflict intensity could be forecast from recent GDELT patterns.

A second objective was methodological: to test whether a more focused and structured dataset would outperform a much larger but noisier document-level representation.

## Data Source

The project used GDELT data from March 2026.

Two main data representations were used:

1. A focused Iran-centered regional panel built from selected countries and aggregated at 15-minute intervals
2. A large-input document-level GKG-derived feature dataset for scale comparison

## Target Construction

The prediction target was not a natural ground-truth battlefield label.

Instead, it was an engineered future conflict intensity proxy built from conflict-related and media-related signals, including event intensity, article volume, and tone-related information.

This means the project should be interpreted as exploratory forecasting on a constructed proxy target.

## Modeling Strategy

### Focused Model

The focused modeling path used a GRU regressor.

This choice was appropriate because the focused dataset was a structured time-series panel and the task required learning temporal patterns and short-term dependencies.

### Comparison Model

The larger comparison experiment used a Multilayer Perceptron (MLP) regressor.

This choice was made because the large-input dataset became a document-level tabular feature matrix rather than a clean sequence structure.

## Experimental Logic

The central comparison in the project was not only about forecasting performance. It was also about data representation.

The project tested whether:
- a focused and task-aligned regional representation
would outperform
- a much larger but broader and noisier document-level dataset

## Main Finding

The focused regional GRU setup performed better than the larger document-level MLP setup for the Iran-specific forecasting task.

This suggests that for this problem:
- structure mattered
- relevance mattered
- task alignment mattered more than raw scale alone

## Limitations

Several limitations should be stated clearly:

- the target was an engineered proxy rather than a direct real-world conflict label
- GDELT reflects reported events and media structure, not pure battlefield truth
- the project should not be described as an operational war prediction system
- the repository is a portfolio-grade representation of the work, not a full storage dump of the entire HPC experiment

## Practical Value

This project demonstrates:
- large-scale preprocessing
- feature engineering
- time-series modeling
- tabular modeling
- experimental comparison design
- HPC workflow experience on CSC Puhti
