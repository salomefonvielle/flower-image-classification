# Classification d’images en régime de données limité  
CNN entraîné from scratch vs transfert d’apprentissage

## Présentation

Ce projet étudie l’impact du pré-entraînement et du biais inductif architectural sur les performances de classification d’images dans un contexte de données limitées.

Deux approches sont comparées :

- Un réseau de neurones convolutif (CNN) conçu et entraîné from scratch  
- Un modèle DenseNet121 pré-entraîné (ImageNet) affiné via transfert d’apprentissage  

L’objectif n’est pas uniquement de comparer les performances, mais d’analyser les dynamiques de généralisation lorsque la quantité de données est restreinte.

---

## Motivation scientifique

Les modèles convolutifs profonds nécessitent généralement de grandes quantités de données pour généraliser correctement.  
En régime de données limité, les modèles surparamétrés sont sujets au surapprentissage.

Le transfert d’apprentissage introduit un prior fort issu d’un pré-entraînement sur un large corpus (ImageNet), ce qui restreint implicitement l’espace des hypothèses.

Ce projet explore :

- La généralisation en régime de données limité  
- Les effets du surparamétrage  
- Le rôle des extracteurs de caractéristiques pré-entraînés  
- La structure des erreurs entre classes visuellement proches  

---

## Méthodologie

- CNN personnalisé composé de quatre couches convolutionnelles (~1–3M paramètres)  
- DenseNet121 pré-entraîné sur ImageNet  
- Fine-tuning avec early stopping  
- Évaluation via :
  - Accuracy  
  - Précision / Rappel / F1-score  
  - Matrices de confusion  
  - Courbes d’apprentissage  

---

## Résultats

Le transfert d’apprentissage améliore significativement la stabilité et la capacité de généralisation en comparaison avec l’entraînement from scratch.

L’analyse des erreurs met en évidence :

- Une variance plus élevée pour le modèle entraîné sans pré-entraînement  
- Une réduction des confusions entre classes proches grâce au modèle pré-entraîné  
- Un effet de régularisation implicite lié au réemploi des représentations  

---

## Structure du projet

flower-image-classification/  
│  
├── prepare_data.py  
├── data/                  # ignoré par git  
├── requirements.txt  
├── requirements-lock.txt  
├── notebooks/  
└── README.md  

---

## Installation

Créer un environnement virtuel et installer les dépendances :

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

## Jeu de données

Le jeu de données n’est pas inclus dans ce dépôt en raison de sa taille.

Il peut être téléchargé à l’adresse suivante :

[INSÉRER LIEN OFFICIEL DU DATASET]

Après téléchargement :

1. Placer le fichier `dataset.zip` à la racine du projet.
2. Exécuter :

```bash
python prepare_data.py


