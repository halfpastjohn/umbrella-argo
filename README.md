# umbrella-argo

### add helm repo and generate Chart.lock + tgz, push to source
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd/
git commit -m 'add argo-cd chart'
git push


helm install argo-cd charts/argo-cd/


kubectl port-forward svc/argo-cd-argocd-server 8080:443

kubectl get pods -l app.kubernetes.io/name=argocd-server -o name | cut -d'/' -f 2



kubectl delete secret -l owner=helm,name=argo-cd
