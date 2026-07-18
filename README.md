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
| File | Description |
|---|---|
| `panic.pkl` | Main “panic” narrative dataset |
| `boyscout.pkl` / `boyscout-scrambled.pkl` | Coherent and scrambled versions |
| `hester_v1-park.pkl` | Park narrative |
| `hester_v2-church.pkl` / `hester_v2-church-scrambled.pkl` | Coherent and scrambled versions |
| `schissel_v1-pool.pkl` | Pool narrative |
| `schissel_v2-lake.pkl` | Lake narrative |
| `stein.pkl` / `stein-scrambled.pkl` | Coherent and scrambled versions |
| `triplett_v1-rookie.pkl` / `triplett_v1-rookie-scrambled.pkl` | Coherent and scrambled versions |
| `triplett_v2-catlady.pkl` | Cat-lady narrative |

## Installation

Create a Python environment and install the core analysis dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install numpy pandas scipy matplotlib jupyter
```

## Usage

Open and run the notebook from the repository root:

```bash
jupyter notebook paper_figures.ipynb
```

Run the notebook cells sequentially from top to bottom. The notebook loads the prepared pickle files in `data/`, computes recall and recognition statistics, and regenerates the main and appendix figures.

To inspect one prepared dataset directly:

```python
import pandas as pd

dataset = pd.read_pickle("data/compiled_data/panic.pkl")
print(dataset.keys())
print(dataset["narrative"])
print(dataset["segmentation"].split("\\n")[:5])
```

## Figures

The notebook includes code for the main paper figures and appendix analyses:

| Section in notebook | Output or analysis |
|---|---|
| Reliability of GPT-4 scoring recall | Human vs. GPT-4 recall-scoring agreement |
| Scaling law in narrative recall | Recall and recognition scaling with narrative length |
| Temporal order of recall | Recall order for coherent vs. scrambled stories |
| `Prec` vs. `Phit` | Relationship between recognition and recall probabilities |
| Semantic similarity for recall probability | Correlations between embedding similarity and recall probability |
| Output interference | Recognition dynamics across trial position |
| Appendix analyses | Serial-position curves, cumulative recall distributions, and scrambled-story comparisons |

Some generated figure files are already included in `figs/`, including:

- `fig1-figure-reliability.svg`
- `fig2-scaling-plots.svg`
- `fig3-recall_sequence_narrative_vs_list.svg`
- `fig4-p_hit_vs_p_rec.svg`
- `fig9-correlation_prec.svg`





