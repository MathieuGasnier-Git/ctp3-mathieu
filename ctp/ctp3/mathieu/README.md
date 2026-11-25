# CTP 3 - Catalog, Lineage & Glossary

Rendu CTP 3 de Mathieu, copies des fichiers du projet `03_CTP3/shopfast_dbt/`.

## Fichiers

- `_staging.yml`, `_marts.yml` : descriptions, owners, PII, tests (ex 1) et liens vers le glossaire (ex 3)
- `check_governance_output.txt` : sortie de `check_governance.py` (PASSED)
- `exposures.yml`, `impact_payments_cents.md` : 3 exposures et note d'impact (ex 2)
- `glossary_template.csv`, `glossary.md` : 6 termes du glossaire (ex 3)
- `data_dictionary_template.csv` : dictionnaire de stg_orders et stg_payments (ex 4)

## Relancer

Les CSV ShopFast doivent etre dans `shopfast-kit/data/` a la racine du repo.

```
python -m venv venv
venv\Scripts\pip install dbt-duckdb
cd 03_CTP3\shopfast_dbt
set DBT_PROFILES_DIR=.
dbt build
dbt docs generate
python check_governance.py
python export_dictionary.py
```

## Dictionnaire vs export dbt

Les descriptions, owners et colonnes PII sont les memes dans les deux.
L'export dbt n'a pas le type, les bornes (ex : amount entre 13.70 et 1400.79), le nullable, l'exemple ni le source system.
Les valeurs autorisees existent seulement comme tests, et les colonnes non PII n'ont pas de classification dans le YAML.
