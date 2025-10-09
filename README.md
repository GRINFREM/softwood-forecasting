## ⚙️ Environment Setup

This project was developed in a Conda environment named **`softwood-forecasting-env`**.  
You can recreate the same setup using either **Conda (recommended)** or **pip/venv**.

---

### 🐍 Option A — Using Conda (recommended)
```bash
# Create the environment from the provided file
conda env create -f environment.yml

# Activate it
conda activate softwood-forecasting-env

# Register the environment as a Jupyter kernel
python -m ipykernel install --user --name softwood-forecasting-env --display-name "softwood-forecasting-env"
```

---

### 💡 Option B — Using pip and venv (alternative)
> Only use this if you prefer a virtual environment over Conda.  
> Installations may vary slightly since some dependencies are Conda-specific.

```bash
# Create and activate a virtual environment
python -m venv .venv
# macOS/Linux:
source .venv/bin/activate
# Windows:
# .venv\Scripts\activate

# Install requirements
pip install --upgrade pip
pip install -r requirements.txt

# Register the environment as a Jupyter kernel
python -m ipykernel install --user --name softwood-forecasting-env --display-name "softwood-forecasting-env"
```

---

### 📘 Selecting the Kernel in Jupyter
When opening the notebook:
1. Go to **Kernel → Change kernel → softwood-forecasting-env**
2. Ensure the name matches the one above.

---

### 🧩 Notes
- The `environment.yml` includes all libraries used in this project (both Conda and pip).  
- If the environment fails to build due to missing low-level packages (like `libcblas` or `llvm-openmp`), you can safely delete the `prefix:` line at the bottom before running the `conda env create` command.  
- `requirements.txt` is provided for users who prefer plain `pip` setups.
