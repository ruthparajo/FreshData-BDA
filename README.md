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

### Inclou els següents arxius:
* landing_zone.ipynb: Notebook inicial que permet descarregar les bases de dades que es troben al directori data_lake
* formatted_zone.ipynb: Notebook que permet transformar els fitxers de parquet a una base de dades estructurada que es troba al directori formatted_zone
* trusted_zone.ipynb: Notebook que permet millorar la qualitat de les dades i les guarda en el directori trusted_zone
* exploitation_zone.ipynb: Notebook que permet fer les combinacions necessàries de les dades per a poder ser introduïdes en el pipeline d'anàlisi de dades i guarda aquestes combinacions al directori exploited_zone
* duckdb.jar: Fitxer que conté una llibreria de java per al funcionament de DuckDB
* data_lake: Directori que conté les bases de dades generades per landing_zone.ipynb
  * compravenda_sup.parquet: base de dades sobre la superfície de la compravenda de pisos de Barcelona (més informació a l'apartat de metadades)
  * renda.parquet: base de dades sobre la renda tributària per seccions censals a Barcelona
  * rent_price.parquet: base de dades sobre el preu de lloguer dels pisos de Barcelona
* formatted_zone: Directori que conté les bases de dades generades per formatted_zone.ipynb
  * freshdata.db: primera versió de la base de dades estructurada
* trusted_zone: Directori que conté les bases de dades generades per trusted_zone.ipynb
  * freshdata_trusted.db: base de dades estructurada i netejada
* exploited_zone: Directori que conté les bases de dades generades per exploitation_zone.ipynb
  * freshdata_exploited1.db: base de dades amb la selecció de dades necessàries per al notebook KNN+KMeans.ipynb
  * freshdata_exploited2.db: base de dades amb la selecció de dades necessàries per al notebook descriptive_analysis.ipynb
* data_analysis_pipelines: Directori que conté els pipelines d'anàlisis de dades
  * KNN+KMeans.ipynb: fitxer que conté dos models, un KNN i un KMeans
  * descriptive_analysis.ipynb: fitxer que conté un anàlisi descriptiu de la taula compravenda_sup
  * duckdb.jar: fitxer que conté una llibreria de java per al funcionament de DuckDB

### Data Engineering Pipeline
Per executar la pipeline s'ha de seguir el següent ordre de fitxers:
1. landing_zone.ipynb: S'adquireixen les dades i s'emmagatzemen en format parquet en el data lake, el qual es troba en la carpeta data_lake.
2. formated_zone.ipynb: Es processen els parquets per emmagatzemar-los homogèniament a través del diseny duckdb amb PySpark. Es junten les tres bases de dades en una sola com 'Freshdata.db'. D'aquesta manera facilita el seu posterior accés.
3. trusted_zone.ipynb: Es realitza el preprocés i nateja de dades per la posterior manipulació. S'aplica tractament de outliers i missings, renombrament i normalització de variables. 
4. exploitation_zone.ipynb: Es combinen les diverses bases de dades per obtenir un format adequat pels models triats.
5. KNN+KMeans.ipynb: S'executa el pipeline de dades aplicant 2 tipus de models per obtenir conclusions sobre les dades.
6. descriptive_analysis.ipynb: S'executa un tercer pipeline de dades en el que es fa un anàlisi descriptiu de la base de dades compravenda_sup.

### Data Analysis Pipeline

SEGUIR AQUI

### Requisits:
- Python 3.x
- Jupyter Notebook
- PySpark (pip install PySpark)
- chardet (pip install chardet)
- Pyarrow (pip install pyarrow)
- Kaggle (pip install kaggle)
- !curl -o duckdb.jar "https://repo1.maven.org/maven2/org/duckdb/duckdb_jdbc/0.10.1/duckdb_jdbc-0.10.1.jar"

També es poden trobar en comentaris en els fitxers.

### Observacions
S'adjunten les bases de dades a l'entrega del projecte ja que una de les bases de dades ha deixat de ser part de de l'Open Data BCN a mig projecte. En conseqüència, no es recomana executar el fitxer landing_zone.ipynb, ja que produirà errors. Les altres bases de dades també s'adjunten, però es sobreescriuen en el cas de que s'executin els diferents pipelines.

### Metadades
##### compravenda_sup.parquet
Columnes:
* Any: columna que indica l'any de la dada
* Trimestre: columna que indica el trimestre de la dada
* Codi_Districte: columna que indica l'identificador del districte
* Nom_Districte: columna que indica el nom del districte
* Codi_Barri: columna que indica l'identificador del barri
* Nom_Barri: columna que indica el nom del barri
* Superfície_mitjana_(m2_construïts): columna que indica el tipus d'habitatge de la compravenda
  * Habitatge nou lliure: Habitatge de màxim un any i mig d'antiguitat, a partir de l'obtenció del certificat final d'obra.
  * Habitatge usat: Habitatge amb més d'un any i mig d'antiguitat, a partir de l'obtenció del certificat final d'obra, hi hagi hagut o no més d'una transmissió registrada.
  * Habitatge nou protegit: Habitatge qualificat com a protegit per part de l'administració, i per tant la seva transmissió està subjecta a alguns requisits. Es considera una modalitat d'habitatge nou.
* Nombre: nombre promig de m2 construïts que han format part d'una transacció de compravenda i que compleix amb les característiques de les anteriors columnes

#### renda.parquet
Columnes: 
* Any: columna que indica l'any de la dada
* Codi_Districte: columna que indica l'identificador del districte
* Nom_Districte: columna que indica el nom del districte
* Codi_Barri: columna que indica l'identificador del barri
* Nom_Barri: columna que indica el nom del barri
* Seccio_Censal: columna que indica la secció censal
* Import_Euros: renda bruta promitja que compleix amb les característiques de les anteriors columnes

#### rent_price.parquet
Columnes:
* Year: columna que indica l'any de la dada
* Trimester: columna que indica el trimestre de la dada
* District: columna que indica el nom del districte
* Neighbourhood: columna que indica el nom del barri
* Average _rent: columna que indica l'unitat en la que està expressada la variable Price
  * average rent (euro/month): valor de la variable Price expressada en euros per mes
  * average rent per surface (euro/m2): valor de la variable Price expressada en euros per m2
* Price: preu promig del lloguer que compleix amb les característiques de les anteriors columnes
