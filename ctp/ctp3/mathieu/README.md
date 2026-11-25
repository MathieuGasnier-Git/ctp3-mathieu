# CTP 3 - Catalog, Lineage & Glossary (Mathieu)

## Fichiers

| Fichier | Exercice |
|---|---|
| `_staging.yml` | Ex 1 : descriptions, owners, PII et tests des 5 modeles staging |
| `_marts.yml` | Ex 1 + 3 : fct_orders et dim_customers, liens `doc()` vers le glossaire |
| `check_governance_output.txt` | Ex 1 : sortie de `check_governance.py` (PASSED) |
| `exposures.yml` | Ex 2 : 3 exposures (Sales dashboard, Finance report, churn model) |
| `impact_payments_cents.md` | Ex 2 : note d'impact en 5 lignes |
| `glossary_template.csv` | Ex 3 : 6 termes (5 du template + recently active customer) |
| `glossary.md` | Ex 3 : docs blocks dbt du glossaire |
| `data_dictionary_template.csv` | Ex 4 : 15 colonnes de stg_orders et stg_payments |

Ce sont des copies des fichiers du projet `03_CTP3/shopfast_dbt/`.

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
dbt ls --select source:shopfast_raw.payments+
python export_dictionary.py
```
