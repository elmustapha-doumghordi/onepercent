
Installation 

- Création de cluster argocd : 
kind create cluster --name argocd

- Creation de namespace
kubectl create namespace argocd 

- Installation d’argocd (https://github.com/argoproj/argo-cd/releases)
kubectl apply -n argocd -f ./Installation/install.yaml


- kubectl get all -n argocd 
- kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
- kubectl port-forward svc/argocd-server -n argocd 8080:443

UP and Running argocd http://localhost:8080/

change admin password :
argocd account update-password

create app via ligne de commande :)

argocd app create react-app --repo https://github.com/anais-codefresh/react-article-display.git --path charts/example-chart --dest-server https://kubernetes.default.svc --dest-namespace default


argocd app get react-app
argocd app sync react-app

patching ;) value ...
kubectl patch svc react-app-example-chart --type='json' -p '[{"op":"replace","path":"/spec/type","value":"NodePort"}]'
argocd app get react-app




kubectl config current-context
kubectl config get-contexts
kubectl config use-context <context_name>

