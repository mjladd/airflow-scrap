# Local Airflow Dev

source: <https://airflow.apache.org/docs/apache-airflow/stable/start/docker.html>

```shell
mkdir airflow-scrap; cd airflow-scrap
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.2.2/docker-compose.yaml'
mkdir -p ./dags ./logs ./plugins
echo -e "AIRFLOW_UID=$(id -u)" > .env
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.2.2/airflow.sh'
chmod +x airflow.sh
```

## Initialize the DB

```shell
docker-compose up airflow-init
```

This creates user `airflow` with password `airflow`.

## Cleanup / Restart from scratch

```shell
docker-compose down --volumes --remove-orphans
docker-compose down --volumes --rmi all
```

## Running

```shell
docker-compose up
```

This will start 6 containers.

## Accessing the environment

```shell
./airflow.sh info
./airflow.sh bash
./airflow.sh python
```

### Web interface

<http://localhost:8080>
user: airflow
pass: airflow

