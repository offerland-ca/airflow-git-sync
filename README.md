# Airflow Git Sync

## Introduction
If you have ever worked with Airflow on Kubernetes, it gives you the ability to sync the DAGs with your repository (as an GitOps solution) using `git-sync` sidecar contanier. If you don't have Kubernetes, it is hard to keep the DAGs directory of Airflow (which is placed at `/opt/airflow/dags/`) synced with the changes you applied to your DAGs and in some cases it is required to restart the Airflow service or container.

This project will help you to have the same functionality as Kubernetes git-sync sidecar and Airflow in order to keep your DAGs in separated repository and maintain them easily.

## How to use?
Set/Change the value of the following variables in your `docker-compose.yaml` file.

| Variable | Description | Default Value |
| --- | --- | --- |
| `REPO_URL` | The URL of the Git repository to sync | `N/A` (required) |
| `GIT_URL` | The URL of the Git server | `github.com` |
| `GIT_BRANCH` | The Git branch to sync | `main` |
| `DIRECTORY_NAME` | The name of the directory to clone the repository into | `project` |
| `DESTINATION_PATH` | The path to sync the repository to | `/app/sync` |
| `INTERVAL` | The interval (in seconds) to sync the repository | `10` |

## Deployment
Simply run the following command in order to deploy the Airflow on your production machine.
```
docker-compose up
```