# Instructions
# Start minikube if not already started 
minikube status
minikube start --vm-driver="hyperkit" --insecure-registry=<TODO: enter>
1. Run below command to start keycloak\
kubectl apply -f ./apps/iam/kanban-keycloak.yaml
2. Use "minikube service keycloak" then set appropiate values in ./apps/api/kanban-api.yaml.  And then run below command to start api\
kubectl apply -f ./apps/api/kanban-api.yaml
3. Use "minikube service kanban-api" then set appropiate values in ./apps/frontend/kanban-api.yaml and then run below command to start frontend\.
kubectl apply -f ./apps/frontend/kanban-api.yaml
4. Use below command to expose services for minikube
minikube service keycloak
minikube service kanban-api
minikube service kanban-frontend
5. Using keycloak admin create relam, role, user and role mapping based on your config
apps/api/kanban-api.yaml
6. In keycloak client settings set the below
* Valid Redirect URIs : 
<kanban-frontend url>/* 
<kanban-api url>/* 
Web Origins : *