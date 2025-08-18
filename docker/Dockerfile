FROM condaforge/mambaforge

WORKDIR /app
ENV PYTHONPATH="/app"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install build-essential software-properties-common vim curl -y

COPY setup.cfg .
COPY environments/environment.yaml environment.yaml

RUN conda config --set channel_priority strict
RUN mamba env update -f environment.yaml -n base && mamba clean -y --all

RUN pip install --upgrade pip && \
    pip install --upgrade oauth2client && \
    pip install keyrings.google-artifactregistry-auth
    
RUN mkdir source
COPY source source

ARG ENVIRONMENT
ENV ENVIRONMENT=${ENVIRONMENT}

CMD ["sh", "-c", "echo 'You need to specify docker command via airflow dag / kubernetes / command line' && exit 1"]
