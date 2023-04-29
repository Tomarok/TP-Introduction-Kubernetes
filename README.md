# TP Docker Kubernetes
Pour installer Minikube, vous pouvez exécuter les commandes suivantes :

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
sudo groupadd docker
sudo usermod -aG docker toto
```

N'oubliez pas d'activer Docker sur WSL dans les paramètres de Docker Desktop.

a. Pour créer un pod avec une image nginx, vous pouvez exécuter les commandes suivantes :

```
minikube start
kubectl get po -A
kubectl run nginx --image=nginx --port=80
kubectl get po -A
```

Vous pouvez vérifier que le pod a bien été créé.

b. Pour faire un port-forward du pod nginx, vous pouvez exécuter la commande suivante :

```
kubectl port-forward my-pod-nginx 80:8080
```
a. Pour créer les configurations pour les déploiements phpMyAdmin et MySQL, vous pouvez exécuter les commandes suivantes (voir les fichiers) :

```
minikube start
kubectl apply -f phpmyadmin.yml
kubectl apply -f mysql.yml
```

b. Pour créer les services pour les déploiements phpMyAdmin et MySQL, vous pouvez exécuter les commandes suivantes (voir les fichiers) :

```
kubectl apply -f phpmyadmin-service.yml
kubectl apply -f mysql-service.yml
```

c. (voir les fichiers)

d. Pour récupérer le nom du service phpMyAdmin, vous pouvez exécuter la commande suivante :

```
kubectl get pod -A
```

Vous devriez voir un résultat similaire à :

```
default phpmyadmin-deployment-1794f74f12-9kzib 1/1 Running 0 3m17s
```
Vous pouvez ensuite faire un port-forward du service phpMyAdmin avec la commande suivante :

```
kubectl port-forward phpmyadmin-deployment-1794f74f12-9kzib 8080:80
```