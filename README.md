# Détection d'objets pour mesurer l'occupation des bureaux – YOLO vs Faster R-CNN

> 🚧 Projet en cours de construction.

## Objectif

Avec le télétravail, les entreprises cherchent à connaître le **taux d'occupation réel** de leurs postes de travail pour adapter leurs surfaces (flex office).
Ce projet détecte, sur une image ou un flux webcam, les objets qui indiquent si un poste est utilisé :

| Classe | Rôle dans l'analyse |
|---|---|
| `person` | présence d'une personne |
| `laptop` | poste en cours d'utilisation |
| `chair` | emplacement de travail |
| `cup` | poste réservé, même si la personne est absente |
| `cell phone` | usage du téléphone |

Deux familles de détecteurs sont comparées sur **le même jeu de test** :
- **YOLO** (Ultralytics) : détecteur en une étape, rapide ;
- **Faster R-CNN** (torchvision) : détecteur en deux étapes, réputé plus précis.

**Respect de la vie privée :** il s'agit de détection (« il y a une personne »), pas de reconnaissance (« qui est-ce »). Seuls des comptages anonymes sont conservés, jamais les images.

## Données

Sous-ensemble de **COCO 2017** limité aux 5 classes ci-dessus :
- **train / val** : environ 700 images par classe tirées de *train2017* (rééquilibrage), découpage 85 / 15 ;
- **test** : toutes les images de *val2017* contenant ces classes. Les poids pré-entraînés ne les ont jamais vues.

## Avancement

| Étape | Notebook | État |
|---|---|---|
| 1. Données et analyse exploratoire | [`01_donnees_et_exploration.ipynb`](notebooks/01_donnees_et_exploration.ipynb) | ✅ |
| 2. Entraînement YOLO | `02_yolo.ipynb` | ⏳ |
| 3. Entraînement Faster R-CNN | `03_faster_rcnn.ipynb` | ⏳ |
| 4. Comparaison sur le jeu de test | `04_comparaison.ipynb` | ⏳ |
| 5. Démo webcam | `demo/webcam.py` | ⏳ |

## Résultats

*À venir : mAP@0.5, mAP@0.5:0.95, mAP par classe, vitesse (images/s) et taille des modèles.*

## Structure du dépôt

```
notebooks/   notebooks Google Colab, à exécuter dans l'ordre
resultats/   métriques et graphiques (CSV, PNG)
demo/        script de démonstration webcam (OpenCV)
```

## Lancer le projet

Ouvrir les notebooks dans [Google Colab](https://colab.research.google.com/) (*Fichier → Ouvrir un notebook → GitHub*) et les exécuter dans l'ordre. Les données et les poids des modèles sont stockés sur Google Drive, pas dans ce dépôt.

## Auteur

Adrien Brouard – Data Analyst · [github.com/Dramasys](https://github.com/Dramasys)
