---
license: mit
language:
  - en
library_name: sentence-transformers
base_model: sentence-transformers/all-mpnet-base-v2
pipeline_tag: sentence-similarity
tags:
  - resume
  - resume-screening
  - explainable-ai
  - xai
  - shapley
  - lime
  - sentence-transformers
  - embeddings
  - skill-ontology
datasets:
  - mithinsagar/exai-resumeintel-data
---

# EXAI-ResumeIntel Model Artifacts

Precomputed model artifacts for **EXAI-ResumeIntel**, an explainable artificial intelligence framework for automated resume analysis using Shapley values, LIME, and a hierarchical domain skill ontology.

**Author:** Mithin Sagar S · [github.com/mithinsagar](https://github.com/mithinsagar)
**Institution:** Vellore Institute of Technology (VIT), Vellore, Tamil Nadu, India
**Code repository:** [github.com/mithinsagar/EXAI-ResumeIntel](https://github.com/mithinsagar/EXAI-ResumeIntel)
**Companion datasets:** [mithinsagar/exai-resumeintel-data](https://huggingface.co/datasets/mithinsagar/exai-resumeintel-data)

## Overview

This repository hosts the large binary artifacts required to run EXAI-ResumeIntel without recomputing embeddings from scratch. Encoding over one million job postings with a transformer model is expensive; these files let anyone clone the code repository and have a working system in minutes.

## Files

| File | Size | Description |
|:---|---:|:---|
| `job_df.pkl` | 1.12 GB | Pickled pandas DataFrame of job postings with a `Role` column |
| `job_embeddings.memmap` | 4.96 GB | Memory-mapped float32 SBERT embedding matrix aligned row-wise with `job_df.pkl` |

## Artifact Details

### `job_df.pkl`

A pickled `pandas.DataFrame` containing the job postings corpus. The `Role` column is used for exact and fuzzy role lookup during matching. Row order is significant: row *i* of this DataFrame corresponds to row *i* of the embedding matrix.

### `job_embeddings.memmap`

A raw `float32` array of shape `(n_jobs, 768)` written in C order, containing sentence embeddings produced by `sentence-transformers/all-mpnet-base-v2`. Stored as a memory-map so that similarity search can stream over the corpus in chunks without loading roughly 5 GB into RAM.

Shape is inferred at load time from the file size and the DataFrame row count, falling back to a dimensionality of 768 when the division is not exact.

## Usage

### Download

```bash
hf download mithinsagar/exai-resumeintel-models \
  --repo-type model --local-dir models
```

### Load both artifacts

```python
import numpy as np
import pandas as pd
from huggingface_hub import hf_hub_download

df_path = hf_hub_download(
    repo_id="mithinsagar/exai-resumeintel-models",
    filename="job_df.pkl",
)
mm_path = hf_hub_download(
    repo_id="mithinsagar/exai-resumeintel-models",
    filename="job_embeddings.memmap",
)

job_df = pd.read_pickle(df_path)
n_rows = len(job_df)
dim = 768

job_embeddings = np.memmap(
    mm_path, dtype=np.float32, mode="r", shape=(n_rows, dim), order="C"
)

print(f"{n_rows:,} job postings, {dim}-dimensional embeddings")
```

### Chunked similarity search

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer("sentence-transformers/all-mpnet-base-v2")
resume_vec = model.encode([resume_text], convert_to_numpy=True)[0]

def chunked_cosine(query, matrix, chunk_size=1024):
    sims = np.empty(matrix.shape[0], dtype=np.float32)
    q_norm = np.linalg.norm(query) + 1e-8
    for start in range(0, matrix.shape[0], chunk_size):
        end = min(start + chunk_size, matrix.shape[0])
        batch = np.array(matrix[start:end], copy=False)
        sims[start:end] = (batch @ query) / (
            np.linalg.norm(batch, axis=1) * q_norm + 1e-8
        )
    return sims

similarities = chunked_cosine(resume_vec, job_embeddings)
```

### Use inside the reference implementation

```bash
git clone https://github.com/mithinsagar/EXAI-ResumeIntel.git
cd EXAI-ResumeIntel
pip install -r requirements.txt
bash scripts/download_data.sh    # fetches this repo and the dataset repo
streamlit run app/main.py
```

## Base Model

Embeddings were produced with [`sentence-transformers/all-mpnet-base-v2`](https://huggingface.co/sentence-transformers/all-mpnet-base-v2), a 768-dimensional sentence encoder. No fine-tuning was applied; these are frozen inference-time embeddings of the job posting corpus.

Note that the EXAI research pipeline described in the accompanying paper uses a separate, from-scratch TF-IDF plus Truncated SVD engine (150 dimensions, 27.8% explained variance) rather than SBERT. The SBERT artifacts here power the interactive application layer, which performs large-scale semantic retrieval across the full job corpus. Both paths are documented in the code repository.

## Regenerating These Artifacts

```python
from sentence_transformers import SentenceTransformer
import numpy as np, pandas as pd

df = pd.read_csv("data/raw/jobs_dataset_with_features.csv")
model = SentenceTransformer("sentence-transformers/all-mpnet-base-v2")

embeddings = model.encode(
    df["Features"].fillna("").tolist(),
    batch_size=64,
    convert_to_numpy=True,
    show_progress_bar=True,
).astype(np.float32)

embeddings.tofile("models/job_embeddings.memmap")
df.to_pickle("models/job_df.pkl")
```

This takes several hours on GPU and considerably longer on CPU, which is why the precomputed artifacts are published here.

## Intended Use

These artifacts support reproducible research in explainable resume screening and semantic job matching. They are intended for research, education, and demonstration.

## Limitations and Ethical Considerations

Embeddings inherit the semantic biases of both the underlying `all-mpnet-base-v2` model and the job posting corpus. Similarity scores between a resume and a role reflect linguistic proximity, not candidate suitability, and must not be treated as a hiring decision.

Any real-world deployment should include bias auditing across protected attributes, mandatory human review of adverse outcomes, and compliance with applicable employment and algorithmic transparency law. The EXAI framework provides Shapley, LIME, and counterfactual explanations precisely so that these decisions remain auditable.

## Citation

```bibtex
@software{sagar2026exai,
  author    = {Mithin Sagar S},
  title     = {{EXAI-ResumeIntel: An Explainable Artificial Intelligence
               Framework for Automated Resume Analysis Using Shapley
               Values, LIME, and Domain Skill Ontology}},
  year      = {2026},
  publisher = {GitHub},
  url       = {https://github.com/mithinsagar/EXAI-ResumeIntel}
}
```

## License

MIT
