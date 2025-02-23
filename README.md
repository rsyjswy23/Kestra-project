# Kestra-project
### Build Data Pipelines with Kestra
Build ETL pipelines for Yellow and Green Taxi data from NYC’s Taxi and Limousine Commission (TLC) by:

1. Extracting data from ![CSV files](https://github.com/DataTalksClub/nyc-tlc-data/releases).
2. Loading it into Postgres or Google Cloud (GCS + BigQuery).
3. Exploring scheduling and backfilling workflows.


## ![Kestra](https://github.com/kestra-io/kestra) 
Kestra is an all-in-one automation and orchestration platform. By bringing Infrastructure as Code best practices to data, process, and microservice orchestration, you can build reliable workflows directly from the UI in just a few lines of YAML.

![Kestra](/jpg/kestra.jpg)

Download the Docker Compose file using the following command on Linux and macOS:

![docker-compose.yml](https://github.com/kestra-io/kestra/blob/develop/docker-compose.yml)
```bash
curl -o docker-compose.yml \
https://raw.githubusercontent.com/kestra-io/kestra/develop/docker-compose.yml
```
Use the following command to start the Kestra server:

```bash
docker-compose up -d
```
Open the URL http://localhost:8080 to launch the UI in the browser.

Setup Kestra & Postgres db:
set up Kestra using Docker Compose containing one container for the Kestra server and another for the Postgres database:

```bash
docker compose up -d
```

Add flows using Ketra's API, run the commands below:
```bash
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/01_getting_started_data_pipeline.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/02_postgres_taxi.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/02_postgres_taxi_scheduled.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/03_postgres_dbt.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/04_gcp_kv.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/05_gcp_setup.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/06_gcp_taxi.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/06_gcp_taxi_scheduled.yaml
curl -X POST http://localhost:8080/api/v1/flows/import -F fileUpload=@flows/07_gcp_dbt.yaml
```

## ETL Pipelines in Kestra
a simple data pipeline which extracts data via HTTP REST API, transforms that data in Python and then queries it using DuckDB.

## Update yaml to define a Docker Compose setup for multi-service application, including Kestra, PostgreSQL and pgAdmin. 
Modefied pluginDefaults on scripts to kestra-meta because we are connecting from Kestra container.
