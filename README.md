# demo-app
Demo app to test kubernetes locally using minikube.

0. Start minikube
```minikube start```

1. Apply manifest mongo-secret.yaml
```kubectl apply -f mongo-secret.yaml```

2. Apply mongo configmap
```kubectl apply -f mongo-configmap.yaml```

3. Apply mongo express
```kubectl apply -f mongo-express.yaml```

4. Create minikube service
```minikube service mongo-express-service```

5. Mongo-express default user and pass
admin, pass.

---
# Grafana Prometheus deployment
https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack

1. ```helm repo add stable https://charts.helm.sh/stable```
2. ```helm repo add prometheus-community https://prometheus-community.github.io/helm-chart```
3. ```helm search repo prometheus-community```
4. ```helm repo update```
5. ```kubectl create namespace monitoring```
6. ```helm install stable prometheus-community/kube-prometheus-stack -n monitoring```
7. ```kubectl get pods -n monitoring```
8. ```kubectl get svc -n monitoring```
9. In order to make prometheus and grafana available outside the cluster, use LoadBalancer or NodePort instead of ClusterIP
10. Edit prometheus: kubectl edit svc stable-kube-prometheus-sta-prometheus -n monitor
11. Edit grafana: kubectl edit svc stable-grafana -n monitor
12. Create service for grafana minikube service stable-grafana -n monitor
13. Login to grafana username: admin password: prom-operator
14. Create dashboard for CPU and Memory usage per pod.
15. Import by dashboard ID - https://grafana.com/grafana/dashboards/
    - CoreDNS: 14981
    - kube-state-metrics-v2: 13332
    - 1 K8S for Prometheus Dashboard 20211010 EN: 15661
    - Website monitoring: 13041
