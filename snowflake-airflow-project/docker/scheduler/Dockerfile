FROM apache/airflow:2.8.1-python3.9

USER root
RUN apt-get update && apt-get install -y gcc g++ unixodbc-dev && rm -rf /var/lib/apt/lists/*

USER airflow
COPY requirements.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

COPY config/airflow.cfg /opt/airflow/airflow.cfg

ENV AIRFLOW__CORE__EXECUTOR=LocalExecutor
ENV AIRFLOW__CORE__LOAD_EXAMPLES=False

CMD ["bash", "-c", "airflow db init && airflow users create --username admin --password admin --firstname Admin --lastname User --role Admin --email admin@example.com || true && airflow scheduler"]
