# Détection de joueurs de football potentiellement sous-évalués

Ce projet de Deep Learning a pour objectif d’estimer la valeur marchande de joueurs de football à partir de leur profil et de leurs statistiques sur une saison.

L’idée est de comparer la valeur estimée par le modèle à la valeur marchande réelle. Un écart important peut permettre d’identifier des joueurs potentiellement sous-évalués ou surévalués selon leurs caractéristiques statistiques. Cette estimation reste uniquement un outil d’analyse : elle ne remplace pas l’expertise d’un recruteur et ne prend pas en compte tous les éléments du marché des transferts.

## Problématique

Il s’agit d’un problème de **régression**, car le modèle doit prédire une valeur numérique : la valeur marchande d’un joueur.

Le projet compare plusieurs approches :

- une baseline triviale ;
- une baseline linéaire ;
- un premier réseau de neurones dense ;
- plusieurs configurations de MLP testées avec différentes architectures et méthodes d’optimisation.

## Données

Les données proviennent du dataset Kaggle [Football Data from Transfermarkt](https://www.kaggle.com/datasets/davidcariboo/player-scores), publié par `davidcariboo`.

Quatre fichiers sont utilisés :

- `players.csv` : profil des joueurs ;
- `appearances.csv` : statistiques par match ;
- `player_valuations.csv` : historique des valeurs marchandes ;
- `competitions.csv` : informations sur les championnats.

La saison 2025-2026 est utilisée comme période de référence. Les joueurs ayant disputé moins de 450 minutes sont exclus afin d’éviter des statistiques par 90 minutes trop instables.

## Objectifs du projet

Le projet consiste à :

1. explorer et comprendre les données ;
2. étudier les variables liées à la valeur marchande ;
3. préparer un dataset adapté à la modélisation ;
4. construire des modèles de référence ;
5. développer un réseau de neurones adapté à des données tabulaires ;
6. tester plusieurs choix d’architecture, de régularisation et d’optimisation ;
7. interpréter les prédictions et discuter les limites du modèle.

## Méthodologie

Les principales étapes sont les suivantes :

- analyse exploratoire des données ;
- agrégation des statistiques par joueur sur une saison ;
- calcul de statistiques par 90 minutes ;
- transformation logarithmique de la valeur marchande ;
- encodage des variables catégorielles ;
- normalisation des variables numériques ;
- séparation en ensembles d’entraînement, de validation et de test ;
- entraînement et comparaison de plusieurs modèles ;
- analyse des écarts entre les valeurs réelles et les valeurs prédites.

## Limites

Le modèle ne prend pas en compte toutes les informations utilisées dans la réalité par les clubs, comme :

- la durée restante du contrat ;
- le potentiel estimé du joueur ;
- sa réputation et sa médiatisation ;
- son historique de blessures ;
- la situation financière ou sportive de son club.

Les statistiques disponibles sont également moins adaptées à certains postes, notamment les gardiens de but. Les résultats produits doivent donc être considérés comme des pistes d’analyse et non comme des recommandations de recrutement.

## Structure du projet

```text
projet-deep-learning/
├── data/
│   ├── appearances.csv
│   ├── competitions.csv
│   ├── players.csv
│   └── player_valuations.csv
├── Notebook-Projet-AnaellePollart.ipynb
├── Rapport-Projet-AnaellePollart.docx
├── Sujet-Projet-DL.docx
└── README.md
```

## Installation

Créer un environnement Python, puis installer les bibliothèques nécessaires :

```bash
pip install numpy pandas matplotlib scikit-learn tensorflow jupyter
```

## Exécution

1. Télécharger le dataset Kaggle.
2. Placer les quatre fichiers CSV dans le dossier `data/`.
3. Ouvrir le notebook :

```bash
jupyter notebook Notebook-Projet-AnaellePollart.ipynb
```

4. Exécuter les cellules dans l’ordre.

## Technologies utilisées

- Python
- NumPy
- pandas
- Matplotlib
- scikit-learn
- TensorFlow / Keras
- Jupyter Notebook

## Auteur

**Anaëlle Pollart**  
Projet réalisé dans le cadre du cours *Neural Network and Deep Learning* — juillet 2026.
