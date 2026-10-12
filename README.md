# entity-matching
This repository is used for the Academy course on Entity Matching.

It contains a hands-on notebook (`Entity_matching_notebook.ipynb`) showcasing Cognite Data Fusion entity matching (supervised and unsupervised) with the Cognite Python SDK.

https://cognite-docs.readthedocs-hosted.com/projects/cognite-sdk-python/en/latest/

## Getting Started

### Prerequisites

- Python 3.11+
- [uv](https://docs.astral.sh/uv/) (recommended) or pip
- CDF client credentials (client ID/secret) with access to entity matching, assets, time series and data sets

### 1. Install dependencies

We recommend using uv to manage your Python virtual environment:

```bash
uv sync
```

This installs the dependencies defined in `pyproject.toml` and creates a virtual environment in the project folder.

### 2. Configure credentials

Copy `.env.example` to `.env` and fill in your values:

```bash
cp .env.example .env
```

`.env` is git-ignored, so your client secret is never committed. `COGNITE_TOKEN_SCOPES` can hold several scopes separated by spaces.

### 3. Run the notebook

Open the repo in your IDE (e.g., VS Code) and open `Entity_matching_notebook.ipynb`.

> **Note:** You may need to select the uv virtual environment (`.venv`) as your kernel.

### 4. Set up clean notebook diffs (one-time, per clone)

Jupyter stamps your local kernel name and Python version into each notebook's metadata every time you run it, which shows up as noisy, unrelated diffs in `git status`/`git diff`. Run this once after cloning to strip that noise before it ever reaches git:

```bash
uv run nbstripout --install --attributes .gitattributes
git config filter.nbstripout.extrakeys "metadata.kernelspec metadata.language_info.version metadata.vscode"
```

This registers a git filter that strips outputs, execution counts, and the kernel/version metadata from notebooks whenever git reads or diffs them — your local `.ipynb` files on disk are untouched, so notebooks still run and show outputs normally in your editor.

## Alternative: pip installation

If you prefer not to use uv, you can install the dependencies directly with pip:

```bash
pip install "cognite-sdk[pandas]" python-dotenv notebook
```
