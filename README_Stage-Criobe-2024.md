# Prédiction du recouvrement corallien à partir de données in-situ et de réanalyses

Stage de recherche au CRIOBE (Centre de Recherches Insulaires et Observatoire de l'Environnement), 2024.
Intégration de données de terrain, satellitaires et de réanalyses météo-océaniques pour prédire l'évolution du recouvrement corallien.

---

## Contexte et objectifs

Les récifs coralliens subissent une mortalité croissante liée aux pressions environnementales (température, houle, salinité...). Le CRIOBE collecte depuis plusieurs années des relevés de terrain sur l'état des récifs. Les objectifs du stage étaient les suivants :

1. Collecter et intégrer les données de terrain du CRIOBE, les données satellitaires et les résultats de modèles météo-océaniques dans un jeu de données unique et cohérent.
2. Identifier les variables environnementales les plus influentes sur le recouvrement corallien grâce à une analyse de sensibilité de Sobol.
3. Prédire le recouvrement corallien à partir de ces variables.
4. Modéliser les interactions au sein de l'écosystème corallien (approche multi-agents, appuyée sur une revue de littérature) afin d'illustrer les tendances de mortalité observées sur plusieurs années.
5. Rédiger un article scientifique en anglais présentant la démarche et les résultats.

---

## Méthodes et outils

| Étape | Méthode / outil |
|---|---|
| Traitement des données | Python, pandas, numpy |
| Données de réanalyse | ERA5 (atmosphère, vagues) et ORAS5 (salinité océanique), via le [Copernicus Climate Data Store](https://cds.climate.copernicus.eu/) |
| Données in-situ | Relevés de recouvrement corallien et mesures de houlographes (CRIOBE) |
| Analyse de sensibilité | Indices de Sobol |
| Prédiction | [à préciser : modèle(s) utilisé(s)] |
| Environnement | Jupyter Notebook |

---

## Structure du dépôt

```
Stage-Criobe-2024/
├── donnees corail/               # Données de recouvrement corallien fournies par le CRIOBE
├── relevé houlographe/           # Données issues des différentes sondes (houle)
├── Tableaux finaux variables/    # Bases de données finales, prêtes pour l'analyse
├── output/                       # Graphiques et tableaux produits
│
├── RecouvrementCorallien.ipynb   # Traitement des données de recouvrement
├── HouleSondeReanalyse.ipynb     # Houle : sondes et réanalyse ERA5
├── SaliniteORAS5.ipynb           # Salinité : réanalyse ORAS5
├── AutresIndicateursSonde.ipynb  # Autres indicateurs issus des sondes
└── AnalyseSobolPredictions.ipynb # Analyse de Sobol et prédictions du recouvrement
```

Les dossiers `era 5` (réanalyses ERA5) et `salinité` (réanalyses ORAS5) ne sont pas inclus dans ce dépôt en raison de leur volume. Les fichiers peuvent être téléchargés sur [cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/).

---

## Pipeline

```
Données in-situ (CRIOBE)  ─┐
Sondes houlographes       ─┼─►  Notebooks de      ─►  Tableaux finaux   ─►  AnalyseSobol        ─►  Prédictions
Réanalyses ERA5 / ORAS5   ─┘    traitement             variables            Predictions            du recouvrement
```

1. Les notebooks `RecouvrementCorallien`, `HouleSondeReanalyse`, `SaliniteORAS5` et `AutresIndicateursSonde` récupèrent les données in-situ ou de réanalyse, les traitent et les transforment en bases de données.
2. Les tableaux obtenus sont enregistrés dans le dossier `Tableaux finaux variables`.
3. `AnalyseSobolPredictions.ipynb` utilise ces tableaux pour l'analyse de sensibilité et la prédiction du recouvrement.
4. L'ensemble des graphiques et tableaux obtenus est regroupé dans le dossier `output`.

---

## Sources de données

- Recouvrement corallien et houlographes : CRIOBE
- ERA5 et ORAS5 : Copernicus Climate Change Service (C3S), Climate Data Store
