# Classification d’images en régime de données limité  
CNN entraîné from scratch vs transfert d’apprentissage

## Présentation

Ce projet étudie la classification d’images dans un contexte de données limitées, en comparant deux stratégies d’apprentissage :

- Un réseau de neurones convolutif (CNN) conçu et entraîné from scratch  
- Un modèle DenseNet121 pré-entraîné sur ImageNet, utilisé en transfert d’apprentissage  

L’objectif est d’analyser les dynamiques de généralisation, la stabilité d’entraînement et l’impact du pré-entraînement lorsque le nombre d’exemples disponibles est restreint.

## Contexte scientifique

Les réseaux convolutifs profonds nécessitent généralement de grandes quantités de données pour apprendre des représentations visuelles robustes.

En régime de données limité :

- Les modèles surparamétrés ont tendance à surapprendre  
- L’écart entre performance d’entraînement et de validation augmente  
- Certaines classes peuvent être mal représentées ou ignorées  

Le transfert d’apprentissage introduit un prior inductif fort, en réutilisant des représentations apprises sur un corpus massif (ImageNet).

Ce projet explore :

- Le comportement d’un CNN appris from scratch  
- L’impact de la capacité du modèle sur la généralisation  
- Le rôle des représentations pré-entraînées  
- Les différences de stabilité et de structure d’erreur  

## Méthodologie

### CNN entraîné from scratch

- 4 blocs convolutionnels  
- Environ 1–3 millions de paramètres  
- Batch Normalization, Dropout, Global Average Pooling  
- Early stopping  
- Expérimentations avec réduction de capacité et régularisation renforcée  

### Transfer Learning (DenseNet121)

- Backbone DenseNet121 pré-entraîné (ImageNet)  
- Poids gelés (feature extractor)  
- Petite tête de classification (Dense + Dropout)  
- Optimisation avec Adam  
- Early stopping  

### Évaluation

Les modèles sont évalués via :

- Accuracy  
- Précision / Rappel / F1-score  
- Matrices de confusion  
- Courbes d’apprentissage (loss et accuracy)  
- Analyse qualitative des erreurs  

## Résultats

Les CNN entraînés from scratch présentent :

- Un surapprentissage marqué  
- Un écart important train / validation  
- Une instabilité des performances selon les classes  

En revanche, le modèle DenseNet121 :

- Converge rapidement  
- Généralise de manière stable  
- Atteint une accuracy de validation de 98 %  
- Reconnaît correctement l’ensemble des classes  

Ces résultats montrent qu’en régime de données limité, le transfert d’apprentissage améliore fortement la robustesse et la généralisation.

## Structure du projet

```bash
flower-image-classification/
│
├── prepare_data.py
├── assets/                # test image
├── data/                  # ignored by git (extracted dataset)
├── notebooks/
│   └── Livrable.ipynb
├── requirements.txt
├── requirements-lock.txt
├── .gitignore
└── README.md
```
## Installation

Créer un environnement virtuel et installer les dépendances :

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
