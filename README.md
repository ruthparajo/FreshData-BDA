<<<<<<< HEAD
# Pràctica 1 - BDA-GIA

## Membres del grup:
* Ruth Parajó Ferrer
* Esteban Gatein
* Olívia Puig i Carreras

## Descripció del projecte:
Implementació d'un pipeline de base de dades que un cop fet l'anàlisi de les dades de compravenda de vivendes, juntament amb altres conjunts rellevants com són el preu del lloguer a Barcelona i la Renta tirbutària mitjana per casa, busca comprendre les tendències del mercat immobiliari, identificar correlacions entre els preus de venda i factors com la renda tributària i la superfície de les vivendes. La implementació del problema funciona amb el llenguatge Python, PySpark i SparkSQL.

### Data Engineering Pipeline
Per executar la pipeline s'ha de seguir el següent ordre de fitxers:
1. Landing zone: S'adquireixen les dades i s'emmagatzemen en format parquet en el data lake, el qual es troba en la carpeta data_lake.
2. Formatted zone: Es processen els parquets per emmagatzemar-los homogèniament a través del diseny duckdb amb PySpark. Es junten les tres bases de dades en una sola com 'Freshdata.db'. D'aquesta manera facilita el seu posterior accés.
3. Trusted zone: Es realitza el preprocés i nateja de dades per la posterior manipulació. S'aplica tractament de outliers i missings, renombrament i normalització de variables. 
4. Exploitation zone: Es combinen les diverses bases de dades per obtenir un format adequat pels models triats.
5. Data pipeline: S'executa el pipeline de dades aplicant 2 tipus de models per obtenir conclusions sobre les dades.

## Inclou els següents arxius:
* REPORT.pdf: Fitxer amb la memòria del treball

## Requisits:
- Python 3.x 
- Jupyter Notebook
- PySpark (pip install PySpark)
- chardet (pip install chardet)
- Pyarrow (pip install pyarrow)
- Kaggle (pip install kaggle)
- !curl -o duckdb.jar "https://repo1.maven.org/maven2/org/duckdb/duckdb_jdbc/0.10.1/duckdb_jdbc-0.10.1.jar"

També es poden trobar en comentaris en els fitxers.

### Data Analysis Pipeline
>>>>>>> f7d50dbe6dbcc1cfefbc14517dc9c22684a4fb83
