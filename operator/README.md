# devopsdemos
demo examples of running services on k8s with different tools

## deploy mysql using operator

### Attribution
Oracle MySQL Operator: https://github.com/oracle/mysql-operator

### Prereqs
Tiller is installed server side, Operator is packaged as Helm Chart

### Steps
#### Clone Oracle MySQL Operator Repository
`git clone https://github.com/oracle/mysql-operator`

#### Create namespace
`kubectl create ns mysql-operator`

#### Install MySQL Operator Helm Chart
`helm install --name mysql-operator mysql-operator/mysql-operator`

#### View the components of Operator Controller
`helm ls`
`kubectl get all -n mysql-operator`

#### View the new Custom Resource Definitions available
`kubectl get crd`

#### Create Service Account
`kubectl apply -f mysql-rbac.yaml` 

#### Create MySQL Cluster from CRD
`kubectl apply -f mysql-cr.yaml` 

#### Get information about the MySQL Cluster
`kubectl describe mysqlclusters -n mysql-operator`

#### Connect to MYSQL Cluster with mysql-client
`kubectl -n mysql-operator run mysql-client --image=mysql:5.7 -it --rm --restart=Never -- mysql -h cluster-cr -uroot -pZgVyVdPe7vv0bUvV -e 'SELECT 1'`