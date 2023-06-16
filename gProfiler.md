# gProfiler
gProfiler combines multiple sampling profilers to produce unified visualization of
what your CPU is spending time on, displaying stack traces of all processes running on your system

Included Microservices in gprofiler using flask application. where in gprofiler folder structure (gprofiler/gprofiler/main.py) .col file is generate

# Requirements:
Basics of Docker, Kubenates, python, flask, ngrok,minikube (for local server to deploy application)
Cassanda Database, Postges Database

# Modification File
In Docker file changes
ENTRYPOINT [ "python3", "-m", "gprofiler", "--no-java","--token=<token>", "--service-name=<service>", "--file-path" "<path-to-.col>","--continuous" ]
token and services from https://profiler.granulate.io/ site

# Functionality
added microservices in gprofiler/main.py file. to get an data from gprofiler to flask application sending through ngrok. after receving profile data of .col format showing in flamegraph. we are using speedscope to show or convert data into json format.
## How to run Gprofiler
```
docker build -t image:tag .
docker push image:tag
```
## Kubernates Commands got to gprofiler/deploy/k8s/gprofiler.yaml
-  you need to change docker image after build put copy in gprofiler.yaml file
-  add GPROFILER_TOKEN and GPROFILER_SERVICE you can get from https://profiler.granulate.io/ click on install service + symbol
```
kubectl apply -f grpofiler.yaml
kubectl get po -n granulate
kubectl logs NAME -n granulate
```


