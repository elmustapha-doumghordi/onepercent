Création de cluster argocd : 
kind create cluster --name argocd

Creation de namespace
kubectl create namespace argocd 

Installation d’argocd (https://github.com/argoproj/argo-cd/releases)
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.0.3/manifests/install.yaml


kubectl get all -n argocd 

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"

kubectl port-forward svc/argocd-server -n argocd 8080:443

http://localhost:8080/