# Installation guide

## Kedro setup

First, you need to install base Kedro package in ``<17.0`` version

> Kedro 17.0 is supported by kedro-airflow-k8s, but [not by kedro-mlflow](https://github.com/Galileo-Galilei/kedro-mlflow/issues/144) yet, so the latest version from 0.16 family is recommended.

```console
$ pip install 'kedro<0.17'
```

## Plugin installation

### Install from PyPI

You can install ``kedro-airflow-k8s`` plugin from ``PyPi`` with `pip`:

```console
pip install --upgrade kedro-airflow-k8s
```

### Install from sources

You may want to install the develop branch which has unreleased features:

```console
pip install git+https://github.com/getindata/kedro-airflow-k8s.git@develop
```

## Available commands

You can check available commands by going into project directory and runnning:

```console
$ kedro airflow-k8s

Usage: kedro airflow-k8s [OPTIONS] COMMAND [ARGS]...

Options:
-e, --env TEXT  Environment to use.
-h, --help      Show this message and exit.

Commands:
  compile          Create an Airflow DAG for a project
  run-once         Uploads pipeline to Airflow and runs once
  schedule         Uploads pipeline to Airflow with given schedule
  upload-pipeline  Uploads pipeline to Airflow DAG location
```

### `compile`

`compile` command takes one argument, which is the directory name containing configuration (relative to `conf` folder). 
As an outcome, `dag` directory contains python file with generated DAG.

### `run-once`

`run-once` command generates DAG from the pipeline, uploads it Airflow DAG location and triggers the DAG run as soon as 
the new DAG instance is available. It optionally allows waiting for DAG run completion, checking if `success` status is 
returned. 

### `schedule`

`schedule` command takes three arguments, one is the directory name containing configuration (relative to `conf` 
folder), the second one is the output location of generated dag, the third is cron like expression that relates to 
Airflow DAG `schedule_interval`.

### `upload-pipeline`

`upload-pipeline` command takes two arguments, one is the directory name containing configuration (relative to `conf` 
folder), the second one is the output location of generated dag.