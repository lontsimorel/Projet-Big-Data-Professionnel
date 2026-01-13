Ce projet est une implémentation professionnelle de bout en bout d’une architecture Big Data moderne, allant :

→ de l’ingestion et la préparation de données massives,
→ à l’analyse exploratoire distribuée (EDA),
→ à l’entraînement de modèles Machine Learning à grande échelle,
→ jusqu'à la containerisation complète du workflow avec Docker pour garantir reproductibilité, scalabilité et portabilité.

L’objectif est de démontrer une maîtrise complète de la chaîne de valeur Data, dans un contexte proche d’un environnement industriel.

🧱 Architecture du projet

Le projet repose sur une architecture distribuée orchestrée via Docker Compose, comprenant :

🔹 1. Spark Master & Workers

Environnement de traitement distribué basé sur Apache Spark :

Spark Master

Plusieurs Spark Workers

Communication interne via le cluster Spark Standalone

Support de Spark MLlib, DataFrame API, SQL, PCA, clustering, etc.

🔹 2. JupyterLab avec PySpark intégré

Un environnement interactif totalement intégré au cluster :

Preload de PySpark, pandas, numpy, seaborn, matplotlib

Connexion automatique au Spark Master

Montage automatique des répertoires /Data, /Notebooks, /Modeles

🔹 3. Structure du projet
📦 Projet_BigData
├── Data/                → datasets sources + parquet
├── Notebooks/           → EDA + feature engineering + modèles ML
├── Modeles/             → modèles entraînés (Pickle, MLlib)
├── docker-compose.yml   → orchestration complète
├── Dockerfile.spark     → image Spark Master/Worker
├── Dockerfile.jupyter   → image JupyterLab + PySpark
├── spark/               → configuration avancée (workers, env, defaults)
└── README.md

📊 Traitement & Analyse des Données

Les données brutes (Open Data Enedis) sont prétraitées dans Spark :

nettoyage et harmonisation

gestion des valeurs manquantes

typage automatique (numérique/catégoriel)

enrichissement métier

export en Parquet optimisé

Un EDA complet a été réalisé en mode distribué :

statistiques globales

corrélations & heatmaps

analyse temporelle

distribution des consommations

🤖 Machine Learning à grande échelle (Spark MLlib)

Plusieurs familles de modèles ont été entraînées :

🔹 Régression (prédiction de consommation)

Random Forest Regressor

Linear Regression

Gradient Boosted Trees Regressor

Avec :

Pipeline complet : encodage, assemblage, scaling

GridSearch distribué

Cross-validation Spark

métriques (RMSE, MAE, R²)

Chaque modèle est sauvegardé automatiquement dans /Modeles.

🔹 Classification

Random Forest Classifier

GBT Classifier

Decision Tree Classifier

Métriques obtenues :
→ Accuracy, F1-score, Precision, Recall

🔹 Clustering & Réduction de dimension

PCA (visualisation et compression)

KMeans (segmentation des profils de consommation)

🐳 Containerisation & Déploiement – Docker

Le projet est entièrement containerisé pour être reproductible sur Windows, Mac ou Linux.

Docker Compose déploie automatiquement :

Spark Master

Spark Workers

JupyterLab

Volumes persistants (data/models/notebooks)

Configuration Spark centralisée

Ce qui permet :

✔ Reproductibilité totale
✔ Aucune installation locale complexe
✔ Scalabilité (ajout de workers en 1 ligne)
✔ Isolation des environnements

📦 Technologies utilisées
Domaine	Outils
Big Data	Apache Spark 4.x, Hadoop 3.3
Machine Learning	Spark MLlib, PySpark
Visualisation	Matplotlib, Seaborn
Containerisation	Docker, Docker Compose
Workflow	JupyterLab
Stockage	Parquet
Dev	Python 3, Git
🎯 Objectifs du projet

Construire un pipeline Big Data complet et industrialisable

Exploiter Spark pour traiter des datasets volumineux

Fournir un framework ML reproductible via Docker

Proposer une architecture prête au déploiement cloud (AWS / GCP / Azure)
