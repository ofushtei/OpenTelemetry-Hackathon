# OpenTelemetry Hackathon
This is a repository for OpenTelemetry Hackathon for AppDynamics PS EMEA & Observability Friday Challenges community

## Prerequiesites
1. Running Kubernetes cluster
2. Git to clone the repository

## How to run this?
1. Clone this repository to your machine
```
git clone https://github.com/ofushtei/OpenTelemetry-Challenge.git
```
2. Create a namespace you'll use
```
kubectl create namespace <your-namespace>
```
3. In `cluster-prep.yaml` file, add your newly created namespace in line 39
```
...
subjects:
- kind: ServiceAccount
  name: otel-collector
  namespace: <your-namespace>
```
4. Apply `cluster-prep.yaml` file to create necessary cluster roles
```
kubectl apply -f cluster-prep.yaml
```
5. Deploy application to the newly created namespace
This will deploy all necessary components
```
kubectl apply -f application.yaml -n <your-namespace>
```
6. Deploy OpenTelemetry collecttor to you namespace
This will deploy all necessary components
```
kubectl apply -f otel-collector.yaml -n <your-namespace>
```
7. Deploy Jaeger to your namespace
With Jaager you can start working on the application instrumentation
```
kubectl apply -f jaeger.yaml -n <your-namespace>
```
8. Once the application is fully instrumented, deploy Grafana, Prometheus and Openseeach else with your namespace
```
kubectl apply -f <file-name>.yaml -n <your-namespace>
```
When deploying Grafana, make sure you have a correct namespace in lines 134 and 167
These are essential for proper data collection