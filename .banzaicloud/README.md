# Spotguide for Mysql database with phpMyAdmin

## Install locally

```bash
helm init --wait

helm repo add presslabs https://presslabs.github.io/charts

helm upgrade --install mysql-operator presslabs/mysql-operator \
  --version 0.1.14 \
  --set orchestrator.replicas=1 \
  --set orchestrator.antiAffinity=soft \
  --set rbac.create=true \
  --set rbac.serviceAccountName=mysql-operator \
  --wait

helm upgrade --install mysql-spotguide charts/mysql-spotguide \
  --values charts/mysql-spotguide/values.dev.yaml
```

## Delete

```bash
helm delete --purge mysql-spotguide
```
