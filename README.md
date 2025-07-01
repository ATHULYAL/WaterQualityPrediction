# Water Pollutants Predictor 

A lightweight **Streamlit** web application that predicts six common water‑quality pollutants ( `O₂`, `NO₃`, `NO₂`, `SO₄`, `PO₄`, `Cl` ) for a given monitoring station and year, using a pre‑trained machine‑learning model.

---

## ✨ Features

|  Feature                |  Details                                                                                     |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| **Instant predictions** | Powered by a scikit‑learn regression model saved as `pollution_model.pkl`.                   |
| **Simple UI**           | Built with Streamlit – just enter *Year* and *Station ID* and click **Predict**.             |
| **Extensible**          | Code separated into model + UI layers so you can swap in a new model or extra inputs easily. |
| **Cross‑platform**      | Works on Windows, macOS, Linux and Streamlit Cloud.                                          |

---

## 📂 Project Structure

```text
water/
│  app.py                 # Streamlit front‑end
│  pollution_model.pkl    # Joblib‑serialized ML model  (≈ 10 ‑ 200 MB)
│  model_columns.pkl      # List of dummy‑encoded columns expected by the model
│  requirements.txt       # Python dependencies (generated with pip freeze)
└── README.md             # This file
```

> **Tip:** keep the model files out of Git (add them to `.gitignore`) and distribute separately or via cloud storage.

---

## 🚀 Quick Start

### 1 . Clone / download the project

```bash
git clone https://github.com/<your‑username>/water‑pollutants‑predictor.git
cd water‑pollutants‑predictor
```

### 2 . Create & activate a virtual environment *(optional but recommended)*

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate
```

### 3 . Install dependencies

```bash
pip install -r requirements.txt
```

```bash
pip install streamlit pandas scikit-learn joblib numpy
```

Then export:

```bash
pip freeze > requirements.txt
```

### 4 . Run the app

```bash
streamlit run app.py
```

Open the local URL printed in the terminal (usually [http://localhost:8501](http://localhost:8501)). You should see the **Water Pollutants Predictor** UI.

---

## 🛠️ Troubleshooting

|  Problem                                                             |  Fix                                                                                                                          |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **`MemoryError`**\*\* while \*\***`joblib.load`**                    | Ensure you’re on 64‑bit Python; free up disk space / RAM; or re‑save the model with `compress=("xz", 3)` and `mmap_mode="r"`. |
| **`Thread 'MainThread': missing ScriptRunContext`**\*\* warnings\*\* | Run the app with **`streamlit run app.py`**, not `python app.py`.                                                             |
| **`streamlit: command not found`**                                   | Activate your virtualenv or run `pip install streamlit`.                                                                      |

---

## 🧪 (Option A) Re‑training / Updating the Model

1. Prepare a CSV of historical water‑quality readings: `year`, `id`, `O₂`, `NO₃`, `NO₂`, `SO₄`, `PO₄`, `CL`.
2. Train your scikit‑learn regressor (RandomForest, XGBoost, etc.).
3. Save both the estimator and the dummy‑encoded column list:

```python
import joblib, pandas as pd
model.fit(X_train, y_train)
joblib.dump(model, "pollution_model.pkl", compress=("xz", 3))
joblib.dump(list(X_train.columns), "model_columns.pkl")
```

4. Copy the two *.pkl* files into the *water/* folder.

---

## 🌐 (Option B) Deploy to Streamlit Cloud

1. Push the repo (without the bulky model) to GitHub.
2. In Streamlit Cloud > **New app**, point to the repo and branch.
3. Add the two *.pkl* files as **Secrets / Files** or download them at runtime from a presigned URL.
4. Scale up resources if your model is > 500 MB.

---

## 📜 License

MIT © 2025 – feel free to remix, adapt, and build upon this project for non‑commercial or commercial purposes. See `LICENSE` for details.

## 🙋‍♀️ Author

Athulya L.  – final‑year CSE undergrad @ KTU.

---

### ⭐️ Contributing

Pull requests are welcome! If you find a bug or have an enhancement idea:
1. Open an issue describing the problem / proposal.
2. Fork & create a feature branch.
3. Commit your changes with clear messages.
4. Submit a PR.

---

> *Need help?* Open an issue or ping me at **\<your email>**. Happy coding!
