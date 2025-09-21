FROM apache/airflow:2.8.1-python3.9

USER root
RUN apt-get update && apt-get install -y gcc g++ unixodbc-dev && rm -rf /var/lib/apt/lists/*

USER airflow
COPY requirements.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

COPY config/airflow.cfg /opt/airflow/airflow.cfg

ENV AIRFLOW__WEBSERVER__SECRET_KEY=snowflake_airflow_secret_key
ENV AIRFLOW__CORE__LOAD_EXAMPLES=False

EXPOSE 8080
CMD ["bash", "-c", "sleep 30 && airflow webserver --port 8080"]
