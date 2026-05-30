# Contrôle Optimal d'une Épidémie (Vaccination Dynamique)

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## Description

Ce projet résout un problème de **contrôle optimal continu** (commande optimale avec Hamiltonien de Pontryagin) pour minimiser simultanément le nombre d'infectés et le coût d'une campagne de vaccination dans un modèle épidémique SIR.

**Méthode numérique :** Forward-Backward Sweep (itération sur la loi de contrôle)

---

##  Structure du projet

```
projet2_controle_epidemie/
├── Projet2_Controle_Optimal_Epidemie.ipynb   # Notebook principal (analyse complète)
├── requirements.txt                          # Dépendances Python
├── README.md                                 # Ce fichier
└── outputs/                                  # Figures générées
    ├── etape3_politiques_trajectoires.png
    ├── etape4_vs_constant.png
    └── etape5_contrainte_hospitaliere.png
```

---

## Installation
### Prérequis
* Python 3.9+ doit être installé.

### Option 1 — pip (recommandé)

```bash
# Cloner le dépôt
git clone https://github.com/<votre-username>/projet2-controle-epidemie.git
cd projet2-controle-epidemie

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows

# Installer les dépendances
pip install -r requirements.txt
```

### Option 2 — Conda / Mamba

```bash
conda env create -f environment.yml
conda activate epidemie_ctrl
```

---

## Exécution

### Notebook Jupyter (recommandé)

```bash
jupyter notebook Projet2_Controle_Optimal_Epidemie.ipynb
# ou
jupyter lab
```

Ouvrez `Projet2_Controle_Optimal_Epidemie.ipynb` et exécutez les cellules dans l'ordre (`Kernel > Restart & Run All`).


Les 3 figures sont enregistrées dans `./outputs/`.

### Visualiser le notebook(dans le cas ou ça ne s'affiche pas directement dans GitHub)
Possible de visualiser le notebook sans erreurs en cliquant sur [nbviewer](https://nbviewer.org/github/DarlingHi/projet2-controle-epidemie/blob/main/Projet2_Controle_Optimal_Epidemie.ipynb)
---

## Modèle mathématique

### Dynamique SIR avec vaccination

$$\dot{S} = -\beta SI - u(t), \quad \dot{I} = \beta SI - \gamma I, \quad \dot{R} = \gamma I + u(t)$$

| Paramètre | Valeur | Description |
|-----------|--------|-------------|
| β | 0.30 | Taux de transmission |
| γ | 0.10 | Taux de guérison |
| R₀ = β/γ | 3.0 | Nombre de reproduction de base |
| u_max | 0.30 | Taux de vaccination maximal |
| T | 200 j | Horizon temporel |
| (S₀, I₀, R₀) | (0.97, 0.03, 0.00) | Conditions initiales |

### Coût à minimiser

$$J = \int_0^T \left[ I(t) + \frac{c}{2} u(t)^2 \right] dt$$

---

## Résultats principaux

| Paramètre c | J optimal | Réduction vs. sans contrôle | Type de contrôle |
|-------------|-----------|----------------------------|------------------|
| 10 (coûteux) | ~1.59 | **83%** | Singulier (doux) |
| 1 (moyen)    | ~1.38 | **85%** | Mixte |
| 0.1 (bon marché) | ~0.65 | **93%** | Bang-bang saturé |

---

## Références

- Lenhart, S. & Workman, J.T. (2007). *Optimal Control Applied to Biological Models*. Chapman & Hall/CRC.
- Pontryagin, L.S. et al. (1962). *The Mathematical Theory of Optimal Processes*. Wiley.
- Hackbusch, W. (1978). A numerical method for solving parabolic equations with opposite orientations. *Computing*, 20(3).

---
## Contexte académique :

Ce projet a été réalisé dans le cadre du cours de *Modélisation en Sciences du Vivant* donné par le **Pr. Jules Tapamo**, en Master 2 Data Science et Ingénierie Mathématique à l'Université de Dschang (programme FOAD AUF).

---

## Auteurs

**Uriel-Darlin AZEMFACK-HIMELE** & **Volvian Silvansien WAMBA FOGOUG**

AUF-Université de Dschang  

---

## Licence

MIT License — voir [LICENSE](LICENSE)
