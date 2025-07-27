
# Multi‑Class Intrusion Detection in Internet of Vehicles  
## Optimising Machine‑Learning Models on Imbalanced Data

This repository accompanies the open‑access article:

> **Á. Palma, M. Antunes, J. Bernardino, A. Alves**  
> *Multi‑Class Intrusion Detection in Internet of Vehicles: Optimizing Machine Learning Models on Imbalanced Data*,  
> **Future Internet** 17 (4), 162, 2025.  
> DOI: 10.3390/fi17040162
> https://www.mdpi.com/1999-5903/17/4/162

The work addresses the severe class‑imbalance problem in CAN‑bus traffic and benchmarks six algorithms on the **CICIoV2024** dataset.  
All analysis is captured in Jupyter notebooks divided into two flows:

* **`split/` – 80 / 20 train/test split**  
* **`kfold/` – 10‑fold cross‑validation**

---

## Repository layout

```text
MLNotebooks/
├── split/
│   ├── AdaBoost_Dec_Split.ipynb
│   ├── DNN_Dec_Split.ipynb
│   ├── ExtraTrees_Dec_split.ipynb
│   ├── LogisticRegression_Dec_split.ipynb
│   ├── RandomForest_Dec_splits.ipynb
│   └── XGBoost_Dec_splits.ipynb
├── kfold/
│   ├── AdaBoost_Dec_kfold.ipynb
│   ├── DNN_Dec_KFold.ipynb
│   ├── ExtraTrees_Dec_kfold.ipynb
│   ├── LogisticRegression_Dec_KFold.ipynb
│   ├── RandomForest_Dec_KFold.ipynb
│   └── XGBoost_Dec_kfold.ipynb
└── README.md
```

> **Tip:** Notebook names follow the pattern `{Model}_{DataRep}_{Flow}.ipynb` where  
> • *Model* ∈ {AdaBoost, DNN, ExtraTrees, LogisticRegression, RandomForest, XGBoost}  
> • *DataRep* = `Dec` (decimal CAN IDs)  
> • *Flow* ∈ {Split, KFold}

---

## Quick‑start

```bash
# 1 – Clone the repo
git clone https://github.com/<your‑user>/MLNotebooks.git
cd MLNotebooks

# 2 – Create a virtual environment
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

# 3 – Install requirements
pip install -r requirements.txt

# 4 – Launch Jupyter
jupyter lab
```

### Minimal environment

| Package                | Version |
|------------------------|---------|
| Python                 | ≥ 3.11  |
| scikit‑learn           | 1.5     |
| XGBoost                | 2.0     |
| Optuna                 | 4.0     |
| TensorFlow / Keras     | 2.15    |
| pandas, numpy, matplotlib, seaborn | latest stable |

---

## Reproducing the paper

1. **Download the dataset**  
   Obtain the **CICIoV2024** decimal‑format CSV (≈ 603 MB) and place it in a `data/` directory or adjust the path in each notebook’s first cell.

2. **Choose your experiment flow**  
   *Run notebooks in `split/` first if you want the classic 80 / 20 hold‑out results (mirrors Table 5).*  
   *Run notebooks in `kfold/` for full 10‑fold CV results (mirrors Table 6).*

3. **Compare metrics**  
   Macro‑F1, precision and recall scores printed at the end of each notebook should match those in the paper.

---

## Key results

| Model | 80 / 20 split macro‑F1 | 10‑fold CV macro‑F1 |
|-------|------------------------|---------------------|
| Random Forest    | **1.000** | **1.000** |
| XGBoost          | **1.000** | **1.000** |
| Extra Trees      | **1.000** | **1.000** |
| Deep Neural Net  | **1.000** | **1.000** |
| Logistic Regression | 0.88 | 0.88 |
| AdaBoost         | 0.81 | 0.32 |

Tree‑based ensembles and the tuned DNN consistently detect minority attack classes even without resampling.

---

## Citation

```bibtex
@article{MCIntrusion2025,
  title   = {Multi-Class Intrusion Detection in Internet of Vehicles: Optimizing Machine Learning Models on Imbalanced Data},
  author  = {Palma, Ágata and Antunes, Mário and Bernardino, Jorge and Alves, Ana},
  journal = {Future Internet},
  volume  = {17},
  number  = {4},
  pages   = {162},
  year    = {2025},
  doi     = {10.3390/fi17040162}
}
```

