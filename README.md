# Central Airflow

Standalone Apache Airflow project for central orchestration workflows.

This project is intended to run as a shared Airflow foundation. Application-specific integrations, including MenuMatch and other services, will be added later as dedicated DAGs, connections, and supporting configuration.

## Environment

Set these values in `.env` before starting Airflow:

```env
AIRFLOW_API_SECRET_KEY=<long-random-secret>
AIRFLOW_FERNET_KEY=<fernet-key>
AIRFLOW_ADMIN_USERNAME=admin
AIRFLOW_ADMIN_PASSWORD=<strong-admin-password>
AIRFLOW_API_PORT=8088
```

Generate `AIRFLOW_FERNET_KEY` with:

```bash
python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"
```

## Run

```bash
docker compose up -d
```

Check status:

```bash
docker compose ps
```

Open Airflow:

```text
http://localhost:8088
```

DAG files belong in `dags/`. Plugins belong in `plugins/`. Airflow runtime state, logs, and the local metadata database are stored in Docker-managed volumes.
