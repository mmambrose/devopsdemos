# devopsdemos
demo examples of running services on k8s with different tools

## deploy mysql using kubernetes manifests

### Attribution
Kubernetes Examples:
https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/

### Steps
#### Create namespace
`kubectl create ns mysql-manifest`

#### Create the Persistent Volume and Claim
`kubectl apply -f manifests/mysql-pvc.yml` 

#### Create the MySQL Deployment
`kubectl apply -f manifests/mysql-deployment.yml`

#### Get information about MySQL Deployment

`kubectl describe deployment mysql -n mysql-manifest`