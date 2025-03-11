# OpenTelemetry Challenge
Repo for OpenTelemetry Challenge for AppDynamics PS EMEA & Observability Friday Challenges community

## How to run this?
1. Create a namespace you'll use
```
kubectl create namespace <your-namespace>
```
2. In `cluster-prep.yaml` file, add your newly created namespace in line 39
3. Apply `cluster-prep.yaml` file
```
kubectl apply -f cluster-prep.yaml
```
4. Apply everything else with your namespace
```
kubectl apply -f <whatever>.yaml -n <your-namespace>
```