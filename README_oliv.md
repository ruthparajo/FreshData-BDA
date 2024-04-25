<<<<<<< HEAD
# Pràctica 1 - BDA-GIA

## Membres del grup:
* Ruth Parajó Ferrer
* Esteban Gatein
* Olívia Puig i Carreras

## Descripción del proyecto:
Implementació d'un pipeline de base de dades que un cop fet l'anàlisi de les dades de compravenda de vivendes, juntament amb altres conjunts rellevants com són el preu del lloguer a Barcelona i la Renta tirbutària mitjana per casa, busca comprendre les tendències del mercat immobiliari, identificar correlacions entre els preus de venda i factors com la renda tributària i la superfície de les vivendes. La implementació del problema funciona amb el llenguatge Python, PySpark i SparkSQL.

## Inclou els següents arxius:
* REPORT.pdf: Fitxer amb la memòria del treball

* ontologia: directorio que contiene la ontología
  * onto.ttl: ontología en formato turtle (leíble por Protégé)
  * onto.clp: ontología en formato CLIPS
  * onto.pdf: gráfico de la ontología
* generador y datos: directorio que contiene los ficheros de datos y de generación de instancias de CLIPS
  * autors.csv: base de datos de autores
  * llibres.csv: base de datos de libros
  * authots_on_cluster.csv: base de datos de autores con sus clusters
  * open_library.ipynb: script que descarga los datos abiertos
  * author_clustering.ipynb: script que realiza clusters de autores 
  * python_to_clips.ipynb: script que transcribe los datos a un fichero CLIPS
* prototipo: directorio que contiene el programa principal
  * prototipo.clp: SISTEMA DE RECOMENDACIÓN DE LIBROS
 
## Requisitos:
- Python 3.x 
- Jupyter Notebook
- PySpark
- SparkSQL

## Instrucciones de uso:
1. Abrir una terminal de CLIPS con el entorno basado en el directorio MAIN
2. Ejecutar secuencialmente los siguientes comandos:
  * (clear)
  * (load "prototipo.clp")
  * (reset)
  * (run)
=======
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
>>>>>>> f7d50dbe6dbcc1cfefbc14517dc9c22684a4fb83
