# nyc-yellow-taxi-trips

![ELT](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/elt%2010.png)

## contexte  
Bienvenue dans la construiction d'un `Pipeline ELT de données automatisé` pour `L'analyse du marché` et optimiser le service de transport. 

## 🎯 Objectifs 
- Mise en place d'un pipeline ELT (Extract Load and Transform) optimisé et automatisé de données vers le Google Cloud Storage (GCP) 
- Gestion du datawarehouse
- Repondre aux question business via l'analyse et Visualisation dans Big query  


## Problèmatiques Business 
1- Demande du marché et saisonnalité 

2- comportement des clients

3- Analyse financière

4- Efficacité operationnelle 


## 🏗️ Structure du ressource (depôt)

```
nyc-yellow-taxi-trips
├── data/
|   ├── taxi_zone_lookup.csv
├── image/
├── Notebooks/   #  compile en htlm du Analyse_market
├── queries/  #  jyputer Notebook pour analyse complete des données
├── venv/
├── create_dataset.py
├── create_ml_dataset_table.py
├── download_taxi_data.py 
├── elt_dag_pipeline.py 
├── exploration_data_analysis.py 
├── LICENSE
├── load_raw_trips_data.py
├── README.md    
├── requirements.txt  
└── transform_trips_data.py  
```           

## Prérequis 

- Compte **Google Cloud Platform (GCP)**  
- épingler les services google cloud comme :
    - vertex AI 
    - IAM et administration       # pour la gestion
    - Google Cloud Storage (GCS)  # pour le stockage cloud 
    - Big Query (datawarehouse)
    - Google Cloud Composer       # gestion de workflow
    - looker                      # visualisation 
    - Big QueryML                 # pour le machine Learning 

Activez le cloudShell et cloud editeur 

⚙️**configuration** 

Via l'éditeur du cloud shell  

- **Clonez** le depôt avec tous les ressources
```
git clone + url du depot
```

- **Activez** l'environnement virtuel   

```
Source.venv/bin/activate
```

- **Installez** les packages nécessaires

```
pip install -r requirements.txt 
```

### I- Extraction des données (Extract)

1. Création de buckets dans GCS puis la configuration 

Téléchargement manuel d'un fichier `.parquet` puis importation local vers GCS suivit d'une anlyse exploratoire avec `exploratoire_data_analysis.py`
pour amaloiration du script pour automatiser l'extraction des plusieurs fichiers. 

2. Mise en place et execution du script d'extraction `download_taxi_data.py` pour l'extraction des données (2022- aujourd'hui) de cloud data center `https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page` vers le service Cloud Storage (GCS)  du Google cloud platform 


![Extraction](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/extract_GCS.png)


### II - Chargement des données (Load)

**Chargement** des données de **GCS** vers **Big query**  via l'execution du script de chargement `load_raw_trips_data.py` via le cloud Shell.
![load](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/Bq_load1.png)

![load](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/Bq_load2.png)

### III - Transformation des données (Transform)

**Transformation** des données dans Big query via le script `transform_trips_data.py` pour créer un *Data Mart* `transformed_data.cleaned_and_filtered` qui regroupoe des données transformées et filtrées selon les questions et les besoins du métier. 

![transformation](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/trans_Bq.png)

![transformation](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/trans_Bq2.png)


## 🚀Automatisation et deploiement de la pipeline

Automatisation de pipeline dans le  **google cloud composer** via le fichier `elt_dag_pipeline.py` qui met en place le **DAG Airflow** qui orchestre un pipeline ELT sur BigQuery en exécutant des scripts stockés sur Google Cloud Storage (GCS). puis le deploiement du DAG pipeline via environnement cloud du GC composer et monitoring via
 **Airflow UI**.

![Auto_elt](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/workflows_GC.png)

![Graph](https://github.com/nazif96/nyc-yellow-taxi-trips/blob/main/images/Graph_DAG.png) 

## 👤