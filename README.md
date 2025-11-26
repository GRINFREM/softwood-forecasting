# 📊 Canadian Softwood Lumber Export Forecasting

A comprehensive time series forecasting project that predicts Canadian softwood lumber exports to the United States using advanced statistical modeling and machine learning techniques. This production-ready model achieves **7.39% test MAPE**, outperforming industry benchmarks and enabling reliable 1-2 quarter ahead planning for strategic business decision-making.

---

## 🎯 Project Overview

### Business Context

This project addresses a **$10B+ annual trade relationship** between Canada and the United States in softwood lumber—one of the most significant bilateral trade flows in North America. The forecasting model directly supports strategic decision-making for:

- **Sawmill Operators**: Production scheduling, workforce planning, inventory management
- **Export Traders**: Price hedging, contract negotiation with U.S. buyers
- **Policymakers**: Trade negotiations, forest management quotas, economic impact studies
- **Financial Analysts**: Equity research on forestry companies, commodity trading strategies

### Key Objectives

1. **Develop a production-ready forecasting model** with exceptional accuracy (< 10% MAPE)
2. **Integrate economic indicators** (U.S. housing market data) as exogenous regressors
3. **Provide scenario analysis** for business planning under different economic conditions
4. **Enable risk quantification** through confidence intervals and uncertainty estimation
5. **Create actionable business intelligence** from raw economic time series data

---

## 🔬 Methodology & Technical Approach

### Data Pipeline

The project implements a comprehensive end-to-end data processing pipeline:

1. **Data Extraction & Merging**
   - Integration of multiple data sources (Statistics Canada, U.S. Census Bureau, Bloomberg)
   - Quarterly time series data spanning multiple decades
   - Alignment of temporal frequencies and handling of missing periods

2. **Data Quality & Imputation**
   - Comprehensive missing value detection and analysis
   - **STL (Seasonal and Trend decomposition using Loess)** for sophisticated imputation
   - Outlier detection using multiple statistical methods (IQR, Z-score, isolation forest)
   - Robust handling of irregular patterns and structural breaks

3. **Feature Engineering**
   - **Lag features**: Historical export volumes at multiple time horizons
   - **Rolling window statistics**: Moving averages, standard deviations, trends
   - **Economic regressors**: 4 key U.S. housing market indicators:
     - U.S. Housing Starts
     - U.S. Building Permits
     - U.S. New Home Sales
     - U.S. Building Permits (Single-Family Housing)

4. **Time Series Validation**
   - **ADF (Augmented Dickey-Fuller) test** for stationarity confirmation
   - **ACF/PACF analysis** for seasonal pattern identification
   - Chronological train/test split (80/20) to prevent data leakage

### Forecasting Model

**Prophet** (Facebook's time series forecasting library) with the following configuration:

- **Seasonality Mode**: Multiplicative (seasonal effects scale with trend)
- **Yearly Seasonality**: Enabled to capture annual construction cycles
- **Exogenous Regressors**: 4 U.S. housing market indicators
- **Uncertainty Intervals**: 95% confidence bands for risk assessment
- **Changepoint Detection**: Automatic identification of trend shifts

**Why Prophet?**
- Handles strong seasonal patterns (quarterly construction cycles)
- Robust to missing data and outliers
- Allows integration of external regressors
- Provides interpretable component decomposition (trend, seasonality, regressors)
- Automatic uncertainty quantification

### Model Performance

- **Test MAPE**: **7.39%** (exceptional vs. 10-20% industry benchmark)
- **Minimal Bias**: Well-calibrated predictions with balanced over/under-predictions
- **Statistical Validation**: Stationarity confirmed (ADF p-value: 0.0354)
- **Seasonal Patterns**: 20-25% quarterly swings captured accurately

---

## 📈 Key Features & Capabilities

### 1. Production-Ready Forecasting
- Reliable 1-2 quarter ahead predictions
- 95% confidence intervals for risk assessment
- Automatic retraining procedures documented

### 2. Scenario Analysis
Comprehensive "what-if" analysis for different economic conditions:
- **Boom Scenario**: +20% housing market indicators
- **Baseline Scenario**: Current trends maintained
- **Slowdown Scenario**: -10% housing market indicators
- **Recession Scenario**: -30% housing market indicators

Reveals **$500M revenue swing** between boom and recession scenarios, enabling strategic planning.

### 3. Component Decomposition
- **Trend Analysis**: Long-term export volume movements
- **Seasonal Patterns**: Quarterly construction cycle identification
- **Regressor Contributions**: Quantified impact of each housing market indicator
- **Visual Communication**: Executive-ready visualizations

### 4. Bias Correction Framework
- Systematic bias detection using Mean Percentage Error (MPE)
- Automatic correction factor calculation when bias exceeds thresholds
- Performance improvement validation

### 5. Comprehensive Evaluation
- Multiple metrics: MAPE, MAE, RMSE, MPE
- Residual analysis and error distribution
- Confidence interval coverage assessment
- Honest discussion of limitations and constraints

---

## 📁 Project Structure

```
softwood-forecasting/
├── main_pipeline.ipynb          # Main analysis notebook (complete pipeline)
├── data/
│   ├── raw/                      # Original data sources
│   │   └── Bloomberg_Data.xlsx   # Economic indicators
│   └── processed/                # Cleaned and processed datasets
│       ├── bloomberg_master_dataframe.csv
│       └── bloomberg_master_dataframe.xlsx
├── environment.yml               # Conda environment specification
├── requirements.txt             # Python package dependencies
└── README.md                     # This file
```

---

## 🚀 Getting Started

The notebook (`main_pipeline.ipynb`) is organized into 8 major sections:

1. **Data ETL**: Extraction, transformation, and loading of raw data
2. **Modeling Pipeline**: Missing value imputation, feature engineering, model training
3. **Model Performance Analysis**: Comprehensive evaluation and validation
4. **Business Applications**: Strategic recommendations and use cases
5. **Advanced Analysis**: Component decomposition, bias correction
6. **Scenario Planning**: Housing market sensitivity analysis
7. **Production Deployment**: Monitoring, retraining, and maintenance guidelines
8. **Final Conclusion**: Project summary and key achievements

### Running the Notebook

1. Follow the [Environment Setup](#⚙️-environment-setup) instructions below
2. Open `main_pipeline.ipynb` in Jupyter Lab/Notebook
3. Select the `softwood-forecasting-env` kernel
4. Run cells sequentially (the notebook is designed to be executed from top to bottom)

---

## 📊 Key Insights & Findings

1. **U.S. Housing Market Dominance**: Export volumes are tightly coupled to U.S. residential construction activity—housing indicators provide 3-6 month lead time for export volume changes.

2. **Seasonal Predictability**: Strong 20-25% quarterly swings due to construction seasonality (Q2/Q3 peak demand periods).

3. **Model Reliability**: Minimal bias with excellent confidence interval coverage, confirming well-calibrated predictions suitable for business decision-making.

4. **Forecast Horizon**: Model optimized for 1-2 quarters ahead (79 observations constrain longer-term forecasts).

5. **External Risk Factors**: Trade policy changes and supply shocks require scenario analysis (not captured in base model but addressed through scenario planning).

---

## 🎓 Technical Skills Demonstrated

- **Time Series Analysis**: Stationarity testing (ADF), ACF/PACF analysis, seasonal decomposition
- **Forecasting Methods**: Prophet (Bayesian structural time series)
- **Data Processing**: STL decomposition, missing value imputation, outlier detection
- **Feature Engineering**: Lag features, rolling windows, exogenous regressors
- **Model Evaluation**: MAPE, MAE, RMSE, bias analysis, confidence interval coverage
- **Business Communication**: Translating technical results into actionable recommendations
- **Statistical Rigor**: Proper train/test splitting, data leakage prevention, comprehensive validation

---

## 📝 License

See [LICENSE](LICENSE) file for details.

---

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
