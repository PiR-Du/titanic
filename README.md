# Titanic Survival Prediction – Kaggle Titanic Competition

Projet de machine learning réalisé dans le cadre de la compétition Kaggle classique **Titanic: Machine Learning from Disaster**.

Lien de la compétition :  
https://www.kaggle.com/competitions/titanic

---

## Objectif du projet

- Prédire la survie des passagers du Titanic à partir de données tabulaires
- Mettre en œuvre une pipeline complète de machine learning :
  - analyse exploratoire
  - feature engineering
  - entraînement de modèles
  - génération de fichiers de soumission Kaggle
- Comparer une approche baseline et un modèle plus avancé

---

## Résultat Kaggle

- Score de la soumission : **0.78708**
- Classement : **1950ᵉ**
- Modèle utilisé pour la soumission finale : **CatBoostClassifier**

---

## Données

- Dataset fourni par Kaggle
- Deux fichiers :
  - `train.csv` (avec variable cible `Survived`)
  - `test.csv` (sans la variable cible)

### Variables principales
- Informations socio-démographiques : `Age`, `Sex`, `Pclass`
- Informations familiales : `SibSp`, `Parch`
- Informations de voyage : `Ticket`, `Cabin`, `Fare`, `Embarked`

---

## Analyse exploratoire

- Inspection des premières lignes du dataset
- Identification des valeurs manquantes (Age, Cabin, Embarked)
- Compréhension de la structure des données
- Analyse qualitative des variables catégorielles

---

## Feature Engineering

### Variables créées
- `NameLength` : longueur du nom du passager
- `FamilySize` : taille de la famille à bord (`SibSp + Parch + 1`)

### Encodage des variables
- Pour le modèle Random Forest :
  - Encodage manuel de `Sex` et `Embarked`
  - Suppression des colonnes non numériques
- Pour CatBoost :
  - Conservation des variables catégorielles brutes
  - Gestion native de l’encodage par le modèle

---

## Modèles entraînés

### Random Forest (baseline)
- Objectif : établir une baseline simple
- Prétraitement manuel des données
- Nombre limité d’arbres pour une première approche

### CatBoostClassifier
- Modèle principal utilisé pour la soumission Kaggle
- Paramètres principaux :
  - 2000 itérations
  - Profondeur limitée pour réduire l’overfitting
  - Early stopping sur un jeu de validation
- Évaluation via la métrique AUC

---

## Évaluation

- Split train / validation (75 % / 25 %)
- Métriques analysées :
  - AUC
  - Accuracy
  - F1-score (en analyse interne)

Le meilleur score de validation est atteint autour de la 516ᵉ itération.

---

## Technologies utilisées

- Python
- pandas
- numpy
- scikit-learn
- CatBoost
- Jupyter Notebook

---

## Lancer le projet

```bash
pip install pandas numpy scikit-learn catboost
```
Puis exécuter le notebook pour :
- Entraîner les modèles
- Générer les fichiers de soumission (submission_rf.csv, submission_catboost.csv)
  
## Améliorations possibles

- Imputation plus avancée des âges
- Extraction de titres depuis les noms (Mr, Mrs, Master, etc.)
- Cross-validation stratifiée
- Optimisation des hyperparamètres
- Techniques d’ensemble (bagging, stacking)

## Auteur

Pierre Duchesne
