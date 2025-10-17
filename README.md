# raspberry_pi_home_helmchart


Steps to install k3s
```bash
curl -sfL https://get.k3s.io | sh -s - server --node-ip=192.168.2.21
sudo kubectl create namespace argocd
sudo kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
````

###ArgoCD server port-forward
Omdat je Pi geen LoadBalancer heeft, kun je port-forward doen:

```bash
sudo kubectl port-forward svc/argocd-server -n argocd 8080:443
```

open nu: https://localhost:8080


Secret achterhalen:
```bash
# Default admin password
sudo kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```