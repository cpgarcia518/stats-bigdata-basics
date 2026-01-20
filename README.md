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

---

## License

Add a license to clarify reuse. Common choices:

* **MIT** (permissive; good for educational code)
* **CC BY 4.0** (often used for written teaching materials)

If you use both code + teaching content, a clean split is **MIT for code** and **CC BY for text/figures**.

---
