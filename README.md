# Runing airflow with docker 

# Create the file docker.yml contain all dependencies 
``` bash
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.10.3/docker-compose.yaml'
```
This file contains several service definitions:

airflow-scheduler - The scheduler monitors all tasks and DAGs, then triggers the task instances once their dependencies are complete.

airflow-webserver - The webserver is available at http://localhost:8080.

airflow-worker - The worker that executes the tasks given by the scheduler.

airflow-triggerer - The triggerer runs an event loop for deferrable tasks.

airflow-init - The initialization service.

postgres - The database.

redis - The redis - broker that forwards messages from scheduler to worker.

# Environment Initialization
``` bash
mkdir -p ./dags ./logs ./plugins ./config
echo -e "AIRFLOW_UID=$(id -u)" > .env
```
# Initialize the database
``` bash
docker compose up airflow-init
```
# Running Airflow
``` bash
docker compose up -d
```
				
# finnaly you can acces to airflow in a container in localhost:8080 
