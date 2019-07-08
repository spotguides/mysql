# Spotguide for Mysql database with phpMyAdmin


## Prerequisites

* Kubernetes 1.12+
* Helm 1.10+

## Test in locally

### Install Presslabs Mysql Operator

#### Add presslabs Helm repo
```bash
helm repo add presslabs https://presslabs.github.io/charts
```

#### Install operator
```bash
helm upgrade --install mysql-operator presslabs/mysql-operator \
  --version 0.2.9 \
  --set orchestrator.replicas=1 \
  --set orchestrator.antiAffinity=soft \
  --set rbac.create=true \
  --set rbac.serviceAccountName=mysql-operator \
  --set helperImage="banzaicloud/mysql-helper:0.1.15" \
  --wait
```

#### Install Banzai Cloud Mysql Spotguide chart
```bash
helm upgrade --install mysql-spotguide charts/mysql-spotguide \
  --values charts/mysql-spotguide/values.dev.yaml
```

#### To remove Banzai Cloud Mysql Spotguide Chart and Presslabs Mysql operator completely from your cluster execute the following steps:

```bash
helm delete --purge mysql-spotguide
helm delete --purge mysql-operator
```
