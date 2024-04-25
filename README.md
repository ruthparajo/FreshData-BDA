# FreshData-BDA

### Descripció
Aquest projecte recolecta 3 bases de dades sobre el preu de lloguer, l'import de renda i la superfície en m^2 dels barris de Barcelona, procedents de Open Data BCN i Kaggle, i efecuta una pipeline d'enginyeria de dades sencera. 

### Requeriments previs
Es necessitarà instalar prèviament paquets amb les següents comandes:
```
pip install PySpark
pip install chardet
pip install pyarrow
pip install kaggle
!curl -o duckdb.jar "https://repo1.maven.org/maven2/org/duckdb/duckdb_jdbc/0.10.1/duckdb_jdbc-0.10.1.jar"
```
També es poden trobar en comentaris en els fitxers.

### Data Engineering Pipeline
Per executar la pipeline s'ha de seguir el següent ordre de fitxers:
1. Landing zone: S'adquireixen les dades i s'emmagatzemen en format parquet en el data lake, el qual es troba en la carpeta data_lake.
2. Formatted zone: Es processen els parquets per emmagatzemar-los homogèniament a través del diseny duckdb amb PySpark. Es junten les tres bases de dades en una sola com 'Freshdata.db'. D'aquesta manera facilita el seu posterior accés.
3. Trusted zone: Es realitza el preprocés i nateja de dades per la posterior manipulació. S'aplica tractament de outliers i missings, renombrament i normalització de variables. 
4. Exploitation zone: Es combinen les diverses bases de dades per obtenir un format adequat pels models triats.

### Data Analysis Pipeline
