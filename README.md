## 🧭 Accessing the Repository Locally

If you’ve been added as a collaborator or want to contribute to this project, follow the steps below to set up the repository on your local machine.

---

### 1️⃣ Clone the repository

Open your terminal and navigate to the folder where you want to store the project.  
Then run:

```bash
# Clone the main repository
git clone https://github.com/GRINFREM/softwood-forecasting.git
```

Then move into the project folder:
```bash
cd softwood-forecasting
```

If you’re contributing via a fork (instead of direct collaborator access):

```bash
# Clone your fork instead
git clone https://github.com/GRINFREM/softwood-forecasting.git
cd softwood-forecasting
```

---

### 2️⃣ (Optional) Set up your upstream remote

If you forked the repo, connect your local copy to the original repository to easily pull new changes:

```bash
git remote add upstream https://github.com/GRINFREM/softwood-forecasting.git
git fetch upstream
```

To keep your fork up to date later on:
```bash
git pull upstream main
```

---

### 3️⃣ Verify your Git configuration

Make sure Git recognizes your name and email (important for commits):

```bash
git config user.name
git config user.email
```

If you need to set them:
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

### 4️⃣ Continue with the Environment Setup

Once the repository is cloned and you’re inside it, continue with the  
[⚙️ Environment Setup](#⚙️-environment-setup) section below to create the Conda environment and register the Jupyter kernel.

---

💡 **Tip:**  
If you encounter permission issues while cloning, make sure you’ve been added as a collaborator under the **GRINFREM** organization or have forked the repo to your own account.

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

## 🧠 Git & Jupyter Collaboration Setup

This repository is configured for **clean, conflict-free Jupyter notebook collaboration** using  
[`nbdime`](https://github.com/jupyter/nbdime) for readable diffs and [`pre-commit`](https://pre-commit.com/) with [`nbstripout`](https://github.com/kynan/nbstripout) for automatic output cleaning.

Follow the steps below **once after cloning** the repository.

---

### 1️⃣ Install the collaboration tools

Make sure your Conda environment is active:

```bash
conda activate softwood-forecasting-env
```

Then install the required tools:

```bash
# Pre-commit automatically strips notebook outputs before every commit
conda install -c conda-forge pre-commit

# Nbdime provides readable diffs and merges for Jupyter notebooks
conda install -c conda-forge nbdime
```

---

### 2️⃣ Enable Git integration for notebooks

Run this command once inside your local repo:

```bash
nbdime config-git --enable
```

This makes `git diff` show **cell-by-cell changes** in notebooks instead of unreadable JSON.

You can test it with:
```bash
git diff path/to/notebook.ipynb
```

---

### 3️⃣ Enable automatic output cleaning

We use **pre-commit** to run [`nbstripout`](https://github.com/kynan/nbstripout) before each commit.  
It removes all notebook outputs, execution counts, and large diffs automatically.

Run this once locally:

```bash
pre-commit install
```

Then clean all existing notebooks (one-time setup):

```bash
pre-commit run --all-files
```

From now on, every `git commit` will automatically strip notebook outputs before saving changes.

---

### 4️⃣ Verify your setup

You can manually trigger the hooks anytime:

```bash
pre-commit run --all-files
```

Or temporarily skip the cleaning step (for example, during demos):

```bash
SKIP=nbstripout git commit -m "keep outputs for demo"
```

---

### ✅ Summary

| Tool | Purpose | Command |
|------|----------|----------|
| **nbdime** | Smart notebook diffs & merges | `nbdime config-git --enable` |
| **pre-commit + nbstripout** | Auto-remove notebook outputs | `pre-commit install` |
| **One-time cleanup** | Strip existing notebook outputs | `pre-commit run --all-files` |

---
### 🔍 Viewing Clean Notebook Diffs with `nbdiff-web`

After completing the setup above, you can view **readable, cell-by-cell diffs** of your Jupyter notebooks using `nbdiff-web`.

This tool launches a visual diff viewer in your browser — perfect for reviewing changes before committing or during pull requests.

#### 🧪 Basic usage
```bash
nbdiff-web path/to/notebook.ipynb
```
Example:
```bash
nbdiff-web softwood-forecasting/main_pipeline.ipynb
```
This opens a browser tab showing what changed between your **working version** and the **last committed version**.

#### 🕑 Comparing two commits
You can also compare any two commits:
```bash
nbdiff-web HEAD~1 HEAD -- path/to/notebook.ipynb
```
This displays the differences between your latest commit and the previous one.

#### 📂 Relative paths
You don’t need the full system path — `nbdiff-web` works with **relative paths** from your current directory.  
If your notebook is in the same folder, just run:
```bash
nbdiff-web main_pipeline.ipynb
```

#### 💡 Tip
For quick diffs in the terminal (instead of the browser):
```bash
git diff path/to/notebook.ipynb
```
If `nbdime` is enabled, this will also show clean cell-by-cell diffs instead of raw JSON.

---

### 💡 Collaboration Tips

- Always pull the latest changes before editing:
  ```bash
  git pull origin main
  ```
- Use feature branches instead of committing directly to `main`.
- Keep data paths **relative** (e.g., `/data/raw/file.csv`) so notebooks run on any system.
- Avoid editing the same notebook cells as teammates to prevent merge conflicts.

---
