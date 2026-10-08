# Instructions for Deploying and Testing Multi-Pod ToDo Application

## 1. How to Apply Manifests
```bash
kubectl apply -f .infrastructure/namespace.yml
kubectl apply -f .infrastructure/todoapp-pods.yml
kubectl apply -f .infrastructure/todoapp-clusterip.yml
kubectl apply -f .infrastructure/todoapp-nodeport.yml
kubectl apply -f .infrastructure/busybox.yml
```

## 2. Test ClusterIP via Service DNS from BusyBox
```bash
kubectl exec -it busybox-curl -n todoapp -- sh
curl http://cluster.local
```

## 3. Test ToDo Application using Service Port-Forward
```bash
kubectl port-forward svc/todoapp-clusterip 8000:80 -n todoapp
```
URL: http://127.0.0.1:8000

## 4. Access App via NodePort Service
```bash
minikube service todoapp-nodeport -n todoapp --url
```
