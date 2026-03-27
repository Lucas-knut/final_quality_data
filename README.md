# MSPR – Qualité des données
## Accidentologie routière en France (2021–2023)

### Prérequis

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

### Démarrage rapide

```bash
# 1. Cloner / récupérer le projet
cd final_quality_data

# 2. Build et lancement
docker compose up --build

# 3. Ouvrir JupyterLab dans le navigateur ou utiliser l'extension Jupyter dans VSCode
#    http://localhost:8888
```

Aucun token ni mot de passe requis (usage local uniquement).

---

### Structure

```
final_quality_data/
├── Dockerfile                        # Image Python 3.11 + Jupyter
├── docker-compose.yml                # Service Jupyter sur port 8888
├── requirements.txt                  # Dépendances Python
├── data/                             # Données brutes et traitées (gitignore recommandé)
│   ├── 2021/                         # Téléchargés automatiquement par le notebook
│   ├── 2022/rm -rf data/2021 data/2022 data/2023
│   ├── 2023/
│   ├── caracteristiques_clean.csv    # Produit par le notebook
│   ├── usagers_clean.csv
│   ├── lieux_clean.csv
│   ├── vehicules_clean.csv
│   ├── quality_report.csv            # Métriques qualité par année
│   ├── profiling_report.html         # Rapport ydata-profiling
│   ├── missing_values.png
│   ├── accidents_analyse.png
│   └── gravite_age.png
└── notebooks/
    └── mspr_qualite_donnees.ipynb    # Notebook principal (7 sections)
```

---

### Source des données

**Base de données annuelles des accidents corporels de la circulation**  
Producteur : Ministère de l'Intérieur – Sécurité Routière  
Licence : Licence Ouverte / Open Licence  
URL : https://www.data.gouv.fr/fr/datasets/bases-de-donnees-annuelles-des-accidents-corporels-de-la-circulation-routiere-annees-de-2005-a-2022/

---

### Contenu du notebook

| Section | Contenu |
|---------|---------|
| 1 | Contexte métier & problématique |
| 2 | Chargement des données & profiling (ydata-profiling) |
| 3 | Identification des problèmes de qualité |
| 4 | Règles de qualité avec seuils (Great Expectations) |
| 5 | Traitements : correction, exclusion, enrichissement |
| 6 | Monitoring qualité – tableau de bord |
| 7 | Conclusion & réponse à la problématique |

---

### Arrêter l'environnement

```bash
docker compose down
```
