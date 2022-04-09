## Installation


## Development Environment

### Start Docker Containers

Activate virtual python environment
`cd $projectroot`
`source venv/bin/activate`

Install required python packages in venv
`pip3 install -r requirements.txt`

Run Docker Containers in the Background
`docker compose up --build -d`


Test DB connection to postgres container

`cd web/``
`python manage.py migrate``

### Best Practices
1. Let the db and other docker containers run in the background as described above
`docker compose up --build -d`

2. Everytime you change something in the project just start Django locally
`python3 manage.py runserver`



### M1 Macs

There can be problems with psycopg2 when running Django locally. Try this:

`pip3 remove psycopg2-binary`
`arch -arm64 pip install psycopg2 --no-binary :all:`

## Testing/Integration/CI


## Deployment to Production 

## Kubernetes

Config in
 ~/.kube/config
 to connect to a kubernetes cluster.

Also in $projectroot/.kube

Change Namespace 
`kubectl config set-context $(kubectl config current-context) --namespace=django-k8s`

### Deployments
Deploy
`kubectl apply -f k8s/nginx/deployment.yaml`

Get Deployments
`kubectl get deployments`

Delete Deployment
`kubectl delete deployment nginx-webser`

### Pods

Get Pods
`kubectl get pods`

Enter Pod via shell
`kubectl exec -it <podname> -- /bin/bash`


### Services

Apply Service
`kubectl apply -f service.yaml`


### Backup/Debuggin

Show current config 

`kubectl get service nginx-webserver -o yaml`
