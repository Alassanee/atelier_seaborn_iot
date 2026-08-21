# Atelier Seaborn – Analyse exploratoire de données IoT

## Contexte

Une entreprise possède plusieurs bâtiments équipés de capteurs IoT collectant en continu des mesures de température, d'humidité, de pression, de consommation énergétique, ainsi que l'état du capteur, le bâtiment concerné et l'horodatage de chaque relevé.

Après une première phase de manipulation des données avec **NumPy**, d'import et de nettoyage avec **Pandas**, et de visualisation basique avec **Matplotlib**, cet atelier utilise **Seaborn** pour mener une analyse exploratoire statistique plus poussée du jeu de données.

## Objectifs

- Explorer la distribution des variables numériques (température, consommation)
- Comparer les bâtiments entre eux sur plusieurs indicateurs statistiques
- Identifier les valeurs extrêmes (outliers) et évaluer leur impact
- Étudier les relations et corrélations entre variables (température, humidité, pression, consommation)
- Analyser la répartition des états des capteurs (OK, ALERTE, ERREUR) par bâtiment
- Produire et exporter des visualisations exploitables pour un rapport

## Structure du projet

```
atelier_seaborn_iot/
│
├── data/
│   └── mesures_capteurs.csv
├── notebooks/
│   └── atelier_seaborn_iot.ipynb
└── exports/
    ├── temperature.png
    ├── temperature.pdf
    └── ...
```

- **data/** : jeu de données brut des mesures capteurs
- **notebooks/** : notebook Jupyter contenant l'ensemble de l'analyse
- **exports/** : graphiques générés et exportés au format image/PDF

## Prérequis

- Python 3.13
- Environnement virtuel (venv)

## Installation

```bash
python3 -m venv env
source env/bin/activate
pip install seaborn matplotlib pandas numpy jupyter
```

## Utilisation

```bash
jupyter notebook notebooks/atelier_seaborn_iot.ipynb
```

Exécuter les cellules dans l'ordre pour reproduire l'ensemble de l'analyse.

## Contenu de l'analyse

| Partie | Contenu |
|---|---|
| 1 | Distribution des températures avec `histplot()` |
| 2 | Distribution des températures avec `kdeplot()` |
| 3 | Distribution des températures avec `boxplot()` (médiane, dispersion, valeurs extrêmes) |
| 4 | Distribution des températures avec `violinplot()` |
| 5 | Comptage des états des capteurs avec `countplot()` |
| 6 | Relation température / consommation avec `scatterplot()` |
| 7 | Régression température / consommation avec `regplot()` |
| 8 | Régression par bâtiment avec `lmplot()` |
| 9 | Matrice de corrélation et `heatmap()` |
| 10 | Analyse multivariée avec `pairplot()` |
| 11 | Sauvegarde des graphiques dans `exports/` |
| 12 | Bonus : analyse croisée état des capteurs / bâtiment avec `catplot()` |

## Bonus – Partie 12

**Fonctionnalité ajoutée : analyse croisée de l'état des capteurs par bâtiment avec `catplot()`**

Cette fonctionnalité complète la Partie 5 (comptage des états avec `countplot()`) en exploitant `catplot()` pour produire une grille de sous-graphiques facettés — un par état de capteur (OK, ALERTE, ERREUR) — avec une échelle verticale indépendante pour chacun (`sharey=False`). Cette approche permet de comparer la répartition des bâtiments sur chaque état sans que la catégorie majoritaire (OK) n'écrase visuellement les états plus rares (ALERTE, ERREUR), offrant ainsi une lecture plus fine et directement exploitable pour identifier les bâtiments à surveiller en priorité.

```python
sns.catplot(data=df, x="batiment", col="etat",hue="batiment", kind="count")
plt.suptitle("Distribution des états par bâtiment", y=1.05)
```

## Auteur

Alassane Mbengue (bl4ckcyph3er) – Master 2 Sécurité des Systèmes Embarqués, UCAD, Sonatel Académie

## Licence

Ce projet est réalisé dans un cadre pédagogique (certification IA – ODC).