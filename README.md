# 🏠 King County House Price Prediction
> **End-to-End Machine Learning Project** · Regression · Feature Engineering · Model Comparison

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0-green)](https://xgboost.readthedocs.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📌 Résumé du Projet

Ce projet prédit le **prix de vente de maisons dans le comté de King (Seattle, WA)** à partir de 21 613 transactions immobilières (mai 2014 – mai 2015). Il couvre l'intégralité du cycle d'un projet ML : nettoyage, feature engineering, EDA visuelle, comparaison de 6 modèles, optimisation d'hyperparamètres et analyse de la performance finale.

**Meilleure performance obtenue : R² = 0.89 · RMSE ≈ $82 000**

---

## 🎯 Objectif Business

Fournir à une agence immobilière un outil d'estimation du prix de marché à partir des caractéristiques d'un bien, avec une **erreur médiane inférieure à 10%** sur 74% des biens.

---

## 🗂️ Structure du Projet

```
king-county-house-prices/
│
├── King_County_House_Price_Prediction.ipynb   # Notebook principal (analyse complète)
├── king_county_model.pkl                       # Modèle entraîné (joblib)
├── requirements.txt                            # Dépendances Python
│
├── figures/                                    # Visualisations exportées
│   ├── 01_target_distribution.png
│   ├── 02_correlation_analysis.png
│   ├── 03_scatter_plots.png
│   ├── 04_geo_analysis.png
│   ├── 05_seasonality.png
│   ├── 06_model_comparison.png
│   ├── 07_feature_importance.png
│   └── 08_residual_analysis.png
│
└── README.md
```

---

## 🛠️ Méthodologie

```
Données brutes
    ↓
Nettoyage (valeurs manquantes, outliers)
    ↓
Feature Engineering (+11 nouvelles variables)
    ↓
EDA (5 analyses visuelles)
    ↓
Comparaison de 6 modèles (CV 5-fold)
    ↓
GridSearchCV sur le meilleur modèle
    ↓
Analyse finale (feature importance + résidus)
```

### Feature Engineering — Variables créées

| Feature | Description | Justification |
|---------|-------------|---------------|
| `house_age` | 2015 − `yr_built` | Dépréciation avec le temps |
| `is_renovated` | Flag si bien rénové | Effet qualitatif fort |
| `living_lot_ratio` | `sqft_living / sqft_lot` | Densité d'occupation |
| `quality_score` | `grade × condition` | Score composite de qualité |
| `sqft_per_bedroom` | Surface par chambre | Taille et confort relatif |
| `is_luxury` | `grade ≥ 10` ou `waterfront=1` | Segment premium |
| `bed_bath_ratio` | Rapport chambres/salles de bain | Équilibre fonctionnel |
| `living15_change` | Variation surface depuis 2015 | Dynamique du quartier |

---

## 📊 Résultats

| Modèle | CV R² | Test R² | RMSE ($) | MAE ($) |
|--------|-------|---------|----------|---------|
| Linear Regression | 0.787 | 0.791 | ~119 000 | ~79 000 |
| Ridge (α=1) | 0.787 | 0.791 | ~119 000 | ~79 000 |
| Lasso (α=0.001) | 0.787 | 0.791 | ~119 000 | ~79 000 |
| Polynomial Ridge (d=2) | 0.818 | 0.823 | ~107 000 | ~69 000 |
| Random Forest | 0.871 | 0.873 | ~91 000 | ~57 000 |
| **Gradient Boosting ✓** | **0.887** | **0.891** | **~82 000** | **~53 000** |

### Insight clé : Top 5 features les plus importantes

1. `lat` — Latitude (localisation géographique)
2. `grade` — Qualité de construction
3. `sqft_living` — Surface habitable
4. `sqft_above` — Surface hors sous-sol
5. `quality_score` — Score composite (feature engineerée)

---

## 🚀 Installation & Exécution

```bash
# Cloner le dépôt
git clone https://github.com/VOTRE_USERNAME/king-county-house-prices.git
cd king-county-house-prices

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate          # Linux / macOS
# venv\Scripts\activate           # Windows

# Installer les dépendances
pip install -r requirements.txt

# Lancer le notebook
jupyter notebook King_County_House_Price_Prediction.ipynb
```

---

## 📦 Dépendances

```
pandas>=2.0
numpy>=1.24
scikit-learn>=1.3
xgboost>=2.0
matplotlib>=3.7
seaborn>=0.12
joblib>=1.3
jupyter>=1.0
```

---

## 💡 Pistes d'Amélioration

- [ ] Intégrer des données externes (distance aux écoles, transports, commerces)
- [ ] Clustering géographique des zipcodes pour créer un effet de quartier
- [ ] Ensemble Stacking (RF + GBM + Ridge)
- [ ] API de prédiction avec FastAPI
- [ ] Interface utilisateur Streamlit

---

## 👤 Auteur

**[Votre Nom]**  
*IBM Data Science Professional Certificate*  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/VOTRE_PROFIL)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/VOTRE_USERNAME)

---

## 📄 Licence

Ce projet est sous licence MIT — voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

*Dataset original : [Kaggle — House Sales in King County](https://www.kaggle.com/harlfoxem/housesalesprediction)*
