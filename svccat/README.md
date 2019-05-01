# devopsdemos
demo examples of running services on k8s with different tools

## deploy mysql using service catalog

### Attribution
https://github.com/GoogleCloudPlatform/kubernetes-engine-samples/tree/master/service-catalog/cloud-sql-mysql

### Prereqs
Service Catalog is enabled and GCP Service Broker installed

### Steps
#### View marketplace
`svcat get classes`

#### Describe config options
svcat describe plan cloud-sql-mysql/beta --scope cluster

#### Provision MySQL instance
```
svcat provision mysql-instance     --namespace mysql-sc     --class cloud-sql-mysql     --plan beta     --params-json '{
         "instanceId": "mysql-sc-'${RANDOM}'",
         "databaseVersion": "MYSQL_5_7",
         "settings": {
             "tier": "db-n1-standard-1"
         }
     }'
```

#### Describe MySQL instance
`svcat describe instance  --namespace mysql-sc mysql-instance`

