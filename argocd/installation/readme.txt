
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

argocd app create react-app --repo https://github.com/elmustapha-doumghordi/onepercent.git --path argocd/apps/demo-simple-apps-helm-chart/example-chart --dest-server https://kubernetes.default.svc --dest-namespace onepercent

argocd app get react-app
argocd app sync react-app

patching ;) value ...
kubectl patch svc react-app-example-chart --type='json' -p '[{"op":"replace","path":"/spec/type","value":"NodePort"}]'
kubectl port-forward react-app-example-chart  -n onepercent  8082:80
argocd app get react-app


- argocd app create helloword-app --repo https://github.com/elmustapha-doumghordi/onepercent.git --path argocd/apps/demo-simple-apps-helm-chart/hello-world-chart --dest-server https://kubernetes.default.svc --dest-namespace onepercent
- argocd app sync helloword-app
patch augmentation de nombre de replicat ou l'inverse :)

  kubectl patch deployment  hello-world-app  --type="json" -p "[{'op':'replace','path':'/spec/replicas','value':2}]" -n onepercent

Self-healing option ;)



declartif apps 
  clé xoxb-2148198038305-2159393302912-q8kJJSM68D7X5NNIkVzlVU4F


- kubectl config current-context
- kubectl config get-contexts
- kubectl config use-context <context_name>

