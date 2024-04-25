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