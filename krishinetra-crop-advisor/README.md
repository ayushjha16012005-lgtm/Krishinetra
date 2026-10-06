# KrishiNetra: AI-Powered Crop Recommendation using Data Analytics

**AICTE | IBM SkillsBuild – Data Analytics with AI Internship 2026 (BharatCares)**
**Author:** Ayush Jha · B.Tech CSE (Cyber Security), NIET Greater Noida

## Project description
**KrishiNetra** ("eye of agriculture") is an AI crop advisor built on soil and weather data.

Choosing a crop that does not match the soil and weather of a field reduces yield and wastes inputs. This project analyses soil nutrients (N, P, K, pH) and climate (temperature, humidity, rainfall) and trains machine-learning models that recommend the most suitable crop. It covers the full analytics workflow: data cleaning, exploratory analysis, feature engineering, model comparison, tuning, evaluation and interpretation.

**Key results**
- Dataset used in the run: 1,815 samples, 20 crops, 7 input features
- Best model: tuned Random Forest, **99.17% test accuracy** and **0.990 macro-F1** (3 errors out of 363 test samples, all rice/jute)
- Most influential factors: humidity, rainfall, combined moisture index, potassium, phosphorus

## Dataset
- **Crop Recommendation Dataset (Kaggle):** https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset
- Columns: `N, P, K, temperature, humidity, ph, rainfall, label`
- The notebook loads `Crop_recommendation.csv` from the project folder if present. Otherwise it automatically downloads a public GitHub mirror of the data, so no manual step is required. The results reported here come from the mirror (1,815 rows, 20 crops); the original Kaggle file has 2,200 rows and 22 crops, so figures may differ slightly if you use it.

## Technologies used
Python 3.10+, Jupyter Notebook, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, joblib

## Files
| File | Purpose |
|---|---|
| `AyushJha_KrishiNetra.ipynb` | Complete project code with outputs |
| `requirements.txt` | Python dependencies |
| `AyushJha_ProjectReport.docx` | Full project report |
| `README.md` | This file |

## Setup and run
```bash
# 1. (optional) create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 2. install dependencies
pip install -r requirements.txt

# 3. launch the notebook and run all cells
jupyter notebook AyushJha_KrishiNetra.ipynb
```
Running the notebook creates a `figures/` folder (charts), `krishinetra_model.joblib` (trained model) and `results.json` (metrics). An internet connection is needed only if `Crop_recommendation.csv` is not placed locally.

## Method summary
1. Clean data (duplicates, missing values, physical range checks)
2. EDA: crop distribution, feature histograms, correlation heatmap, per-crop box plots and profiles
3. Feature engineering: `NPK_total`, `N_to_K`, `P_to_K`, `moisture_index`
4. Compare Logistic Regression, KNN, Decision Tree, Random Forest, Gradient Boosting with 5-fold CV
5. Tune Random Forest with GridSearchCV; evaluate on a stratified 20% hold-out set
6. Interpret with feature importance; `recommend_crop()` returns the top-3 crops with probabilities

## Limitations
The dataset is clean and curated; real fields have sensor noise, seasonality and market factors. Future work: live IoT sensor input, yield and price data, and a web/mobile app.
