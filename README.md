# Machine Learning End to End: Train with Scikit-Learn, Track with MLflow, Explain with LLMs

This repo has three notebooks that build on each other, all using the same dataset and model. You do not need to install anything locally. Open each notebook in Google Colab and run the cells in order.

## Notebooks

1. `01_train.ipynb`: load the data, build a Scikit-Learn pipeline, train and evaluate two models.
2. `02_track_mlflow.ipynb`: log the same training runs with MLflow, compare them, and register the better model.
3. `03_explain_shap_gemini.ipynb`: compute SHAP values for individual predictions and use Gemini to explain them in plain language, including a worked example of checking an LLM explanation against the real numbers.

## Dataset

`data/Telco-Customer-Churn.csv` It is a customer churn dataset from a telecom company: one row per customer, with account details and a label showing whether the customer churned.

## Setup

### Option A: Google Colab (recommended for the live session)

1. Go to https://colab.research.google.com
2. Open each notebook from this repo (File, Open notebook, GitHub tab, paste the repo URL)
3. Colab does not automatically have this repo's `data/` folder, so the first code cell in each notebook that needs data will also work if you upload `Telco-Customer-Churn.csv` to the Colab session's file browser, or clone the repo directly inside Colab with:

```
!git clone <this-repo-url>
%cd <repo-folder-name>
```

### Option B: Local

```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

## Gemini API key

Notebook 3 uses Gemini to generate plain-language explanations. To get a free key:

1. Go to https://aistudio.google.com/apikey
2. Sign in with a Google account
3. Click Create API key
4. Copy it

In Colab, store it in the Secrets panel (the key icon in the left sidebar) rather than pasting it into a cell. Locally, set it as an environment variable:

```
export GEMINI_API_KEY=your_key_here
```

## Viewing the MLflow UI

After running `02_track_mlflow.ipynb`, from this folder run:

```
mlflow ui --backend-store-uri sqlite:///mlflow.db
```

Then open the URL it prints, usually http://127.0.0.1:5000.

