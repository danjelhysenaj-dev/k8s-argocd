# k8s-argocd

First of all in order to setup ArgoCD you need to create a seperate namespace

---
	kubectl create namespace argocd
---

After creating the namespace now we will need to install ArgoCD

---
	kubectl apply -n argocd -f http://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
---

After installation of argocd you can check if it is successfully installed on your namespace

---
	kubectl get all -n argocd
---

Now in order to get ArgoCD we need to do port forwarding to access the web-gui where we are going to get connected to the service/argocd-server

---
	kubectl port-forward service/argocd-server -n argocd 8080:443
---

After you did port forwarding now you need to log in to ArgoCD in order to do that you need to find your passowrd and in order to do that you need to find your secret/

---
	kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
---

