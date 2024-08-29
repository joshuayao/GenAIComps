# pgvector-db

Manifests for deploying PGVector DB service.

## Install the Chart

To install the chart, run the following:

```console
cd ${GenAIComps_repo}/comps/vectorstores/langchain/pgvector/kubernetes/manifest
kubectl apply -f pgvector-db.yaml
```

## Verify

To verify the installation, run the command `kubectl get pod` to make sure all the PGVector pods are runinng.

Then run the command `kubectl port-forward svc/pgvector-db 5432:5432` to expose the PGVector db service for access.

Please install `psql` on your host, and ensure the version of psql is supported by the installed PGVector.

Open another terminal and perform the following command if using the default user credential and database:
```
psql postgresql://testuser:testpwd@pgvector-db:5432/vectordb
```
If everything goes well, you will see the following console output:
```
psql (xxxx, server xxxx)
Type "help" for help.

vectordb=# 
```

## Values

| Key                          | Type   | Default                          | Description            |
| ---------------------------- | ------ | -------------------------------- | ---------------------- |
| image                        | string | `"pgvector/pgvector:0.7.0-pg16"` |                        |
| port                         | string | `"5432"`                         | The database port      |
