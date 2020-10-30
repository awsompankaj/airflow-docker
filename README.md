# Airflow-docker

Clone the repo

#Create a bridge network and docker run commands to spin up postgres and then airflow.

docker network create -d bridge airflow
 
docker run -itd -e POSTGRES_USER=airflow -e POSTGRES_PASSWORD=airflow -e POSTGRES_DB=airflow --network airflow --name postgres postgres

docker run -it --env-file .env -v /airflow-docker/dags:/opt/airflow/dags -v /airflow-docker/logs:/opt/airflow/logs -v /airflow-docker/scripts:/opt/airflow/scripts --entrypoint ./scripts/entrypoint.sh  -p 8080:8080 --network airflow --name webserver  apache/airflow
