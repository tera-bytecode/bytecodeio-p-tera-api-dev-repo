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
    pip install keyrings.google-artifactregistry-auth && \
    pip install autopep8 && \
    pip install --index-url https://us-east1-python.pkg.dev/mercari-us-boston-ml/mercari-us-boston-de/simple/ us-de-common

RUN mkdir de_onboarding
COPY de_onboarding de_onboarding

ARG ENVIRONMENT
ENV ENVIRONMENT=${ENVIRONMENT}

CMD ["sh", "-c", "echo 'You need to specify docker command via airflow dag / kubernetes / command line' && exit 1"]
