# devopsdemos
demo examples of running services on k8s with different tools

## deploy mysql using helm

### Attribution
Stable Helm Charts: https://github.com/helm/charts/tree/master/stable/mysql

### Steps
#### Create namespace
`kubectl create ns mysql-helm`

#### Install MySQL Helm Chart
`helm install --name mysql-helm mysql/ --namespace mysql-helm`

#### Show components of Helm Chart
`k get all -n mysql-helm`

#### Show Helm Releases

`helm ls mysql-helm`

#### Test the Helm Release

`helm test mysql-helm`