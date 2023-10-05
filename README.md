# k8s-argocd

First of all in order to setup ArgoCD you need to create a seperate namespace

---
	  kubectl create namespace argocd
---

After creating the namespace now we will need to install ArgoCD

---
	kubectl apply -n argocd -f http://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/4da244c2-bcd8-4e07-96e3-3d9c3331784c)

---

After installation of argocd you can check if it is successfully installed on your namespace

---
	kubectl get all -n argocd
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/1a8e7a4c-0edc-4d36-8eb9-391a9a6b62f0)

---

Now in order to get ArgoCD we need to do port forwarding to access the web-gui where we are going to get connected to the service/argocd-server

---
	kubectl port-forward service/argocd-server -n argocd 8080:443
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/418cf31c-2af2-4137-8a75-70730500ed51)

---

After you did port forwarding now you need to log in to ArgoCD in order to do that you need to find your passowrd and in order to do that you need to find your secret/

---
	kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/54c4978e-25bc-4fa0-9762-d7cdbff6325e)

---
Congratulations now you have setup ArgoCD on your environment!!
