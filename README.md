Here it is (contents of `README.md`):

---

# stats-bigdata-basics

Beginner-to-intermediate, **hands-on** notebooks for *Statistics and Big Data Analytics* in Python.
Designed for fast execution in **Google Colab** while remaining fully reproducible locally (e.g., WSL/Linux/macOS).

## Repository layout

```
stats-bigdata-basics/
├─ notebooks/                 # Jupyter notebooks (recommended)
│  └─ 01-StatAndPython.ipynb
├─ data/                      # CSVs and other datasets used by notebooks
├─ images/                    # Figures used in Markdown cells and examples
├─ pyproject.toml             # Local dependency spec (uv-friendly)
├─ uv.lock                    # Pinned lockfile (if using uv)
├─ requirements-colab.txt     # Exported, Colab-friendly dependencies (recommended)
└─ README.md
```

### Why this structure matters in Colab

Colab runs notebooks in a fresh VM where the default working directory is `/content`.
If a notebook refers to local assets (e.g., `data/` and `images/`), the most reliable approach is to:

1. **Clone the repo inside Colab**
2. **Change directory to the repo root**
3. Use paths relative to the repo root (e.g., `data/...`, `images/...`)

This avoids “file not found” errors and keeps notebooks portable.

---

## Open in Google Colab (recommended)

### Option A — One-click “Open in Colab” (GitHub)

Once this repository is on GitHub, open the notebook directly with:

* **01-StatAndPython.ipynb**:


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cpgarcia518/stats-bigdata-basics/blob/main/notebooks/01-StatAndPython.ipynb?usp=copy)

### Option B — Always works (Setup cell)

Add (or keep) **this as the first cell** in each notebook. It guarantees that `data/` and `images/` are available.

> Replace `REPO_URL` with your GitHub repository URL.

```python
# --- Colab setup: clone repo and set paths (run once at the top) ---
import os
from pathlib import Path

IN_COLAB = "COLAB_RELEASE_TAG" in os.environ

REPO_URL = "https://github.com/YOUR_GITHUB_USER/stats-bigdata-basics.git"
REPO_DIR = "stats-bigdata-basics"

if IN_COLAB:
    %cd /content
    if not Path(REPO_DIR).exists():
        !git clone --depth 1 {REPO_URL}
    %cd {REPO_DIR}

PROJECT_ROOT = Path.cwd()
DATA_DIR = PROJECT_ROOT / "data"
IMAGES_DIR = PROJECT_ROOT / "images"

print("PROJECT_ROOT:", PROJECT_ROOT)
print("DATA_DIR:", DATA_DIR, "| exists:", DATA_DIR.exists())
print("IMAGES_DIR:", IMAGES_DIR, "| exists:", IMAGES_DIR.exists())
```

**Use these paths in the notebook**:

```python
import pandas as pd

iris = pd.read_csv(DATA_DIR / "iris.csv", index_col=0)
```

And in Markdown cells (images):

```markdown
<img src="../images/boxplot.png" width="500"/>
```

> Tip: keep notebooks inside `notebooks/` and refer to images using `../images/...` in Markdown.
> For code cells, prefer `DATA_DIR / "file.csv"` and `IMAGES_DIR / "file.png"`.

---

## Dependencies

### In Colab

Colab already includes many scientific packages, but versions can change. For reproducibility, install pinned dependencies from `requirements-colab.txt`:

```python
!pip -q install -r requirements-colab.txt
```



## Notes on data and reproducibility

* If datasets are large, consider shipping **a small sample** in `data/` and documenting how to retrieve the full dataset.
* Prefer local images in `images/` over external links (Drive/Wikipedia), so notebooks remain stable over time.
* For papers/reports, record package versions (e.g., `python --version`, `pip freeze`, or `uv.lock`) to support reproducibility.

---

## License

Add a license to clarify reuse. Common choices:

* **MIT** (permissive; good for educational code)
* **CC BY 4.0** (often used for written teaching materials)

If you use both code + teaching content, a clean split is **MIT for code** and **CC BY for text/figures**.

---
