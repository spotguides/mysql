# Spotguide for Mysql database with phpMyAdmin 

This spotguide provides:

- 
- 
- 


helm repo add presslabs https://presslabs.github.io/charts

helm upgrade --install --namespace default mysql-operator presslabs/mysql-operator --version 0.1.14  --set orchestrator.replicas=1 --set orchestrator.antiAffinity="soft" --set rbac.create=true --set rbac.serviceAccountName=mysql-operator

helm upgrade --install --namespace default spotguide charts/mysql-single

helm del --purge spotguide
