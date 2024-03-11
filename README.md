# demo-app
Demo app to test kubernetes locally using minikube.

0. Start minikube
minikube start

1. Apply manifest mongo-secret.yaml
kubectl apply -f mongo-secret.yaml

2. Apply manifest mongo.yaml
kubectl apply -f mongo-secret.yaml

3. Apply mongo configmap
kubectl apply -f mongo-configmap.yaml

4. Apply mongo express
kubectl apply -f mongo-express.yaml

5. Create minikube service
minikube service mongo-express-service

6. Mongo-express default user and pass
admin, pass.
