# LLM Narrative Analysis

Code and data accompanying **“Using Large Language Models to Study Human Memory for Meaningful Narratives”**.

This repository contains the analysis notebook, prepared experimental data, recall/recognition scores, embeddings, and figure files used to study how humans remember meaningful narratives. The project uses large language models as part of a pipeline for narrative experiment design and recall analysis, including clause-level scoring of free recalls and generation of plausible lures for recognition experiments.

## Overview

The analysis focuses on memory for naturalistic stories rather than random word lists. Participants read narratives of different lengths and then completed recall and recognition tasks. The repository supports analyses of:

- Agreement between human recall scoring and LLM-based recall scoring.
- Scaling relationships between narrative length, recognition, and recall.
- Differences between coherent and scrambled narratives.
- Temporal order in free recall.
- The relationship between clause recall probability and recognition probability.
- Semantic similarity between individual clauses and whole narratives using text embeddings.

## Repository Structure

```text
.
├── data/
│   ├── compiled_data/      # Prepared narrative-level datasets
│   ├── embeddings/         # Precomputed embedding-based similarity scores
│   ├── recall_scores/      # Human and LLM recall-scoring outputs
│   └── words/              # Serial-position curve data
├── figs/                   # Figure files generated for the paper
├── paper_figures.ipynb     # Main analysis notebook
└── README.md
```

## Data Contents

The files in `data/compiled_data/` are pickled Python dictionaries. Each narrative dataset may contain:

| Key | Description |
|---|---|
| `narrative` | Full story text shown to participants |
| `segmentation` | Clause-level segmentation of the narrative |
| `lures` | Plausible lure clauses for recognition experiments |
| `recalls` | Participant free-recall responses |
| `recognition` | Participant recognition responses |
| `recall scores` | Clause-level recall scoring |
| `recall_scores_ordered` | Ordered recall scores |
| `recall_scores_completions` | LLM scoring completions or intermediate outputs |
| `recalls segmented` | Segmented recall responses |
| `embeddings` | Precomputed embedding information, when available |
| `scramble_map` | Mapping for scrambled-story variants, when available |

Included narratives and variants:


