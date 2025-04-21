FROM python:3.12-slim

# Instala herramientas necesarias
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libpq-dev \
    openjdk-17-jdk \
    curl \
    procps \
    && rm -rf /var/lib/apt/lists/*

# Variables necesarias
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
ENV PATH="$JAVA_HOME/bin:$PATH"
ENV PYSPARK_PIN_THREAD=false

# Descarga el JAR mlflow-spark manualmente
RUN mkdir -p /opt/spark/jars && \
    curl -L -o /opt/spark/jars/mlflow-spark-1.30.0.jar \
    https://repo1.maven.org/maven2/org/mlflow/mlflow-spark/1.30.0/mlflow-spark-1.30.0.jar

# Establece el directorio de trabajo
#WORKDIR /app
WORKDIR /home/jovyan/work

# Instala MLflow y el conector para PostgreSQL
RUN pip install --upgrade pip && \
    pip install mlflow psycopg2-binary

# Expone el puerto por defecto de MLflow UI
EXPOSE 5000

# Comando por defecto para iniciar MLflow
CMD ["mlflow", "ui", "--host=0.0.0.0", "--port=5000"]