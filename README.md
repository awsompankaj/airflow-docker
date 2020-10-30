# Airflow-docker

clone the repo

##Create a bridge network

docker network create -d bridge airflow
 
docker run -itd -e POSTGRES_USER=airflow -e POSTGRES_PASSWORD=airflow -e POSTGRES_DB=airflow --network airflow --name postgres postgres

docker run -it --env-file .env -v /home/pankaj/airflow/dags:/opt/airflow/dags -v /home/pankaj/airflow/logs:/opt/airflow/logs -v /home/pankaj/airflow/scripts:/opt/airflow/scripts --entrypoint ./scripts/entrypoint.sh  -p 8080:8080 --network airflow --name webserver  apache/airflow
