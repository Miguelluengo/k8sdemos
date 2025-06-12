# k8sdemos
Instalar el cluster y argo-cd con IaC



Luego de Instalar argo-cd

kubectl port-forward svc/argocd-server -n argocd 8080:443
ADMIN_USER="admin"
ADMIN_PASSWD="$(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)"
argocd login localhost:8080 --username $ADMIN_USER --password $ADMIN_PASSWD --insecure
argocd cluster add dev
argocd cluster add qa
argocd cluster add prod

