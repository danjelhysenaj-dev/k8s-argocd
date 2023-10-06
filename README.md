# k8s-argocd

# Install ArgoCD latest stable version
First of all in order to setup ArgoCD you need to create a seperate namespace

---
	  kubectl create namespace argocd
---

After creating the namespace we will need to install ArgoCD where it will install all dependencies and create all kubernetes objects

---
	kubectl apply -n argocd -f http://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/884213ff-a3c9-4f13-92b2-c65993ed17e9)

---

After installation of argocd you can check if it is successfully installed on your namespace

---
	kubectl get all -n argocd
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/36e35fe1-97a3-430f-afef-7c360ecf13e3)

---

Now in order to get ArgoCD we need to do port forwarding to access the web-gui where we are going to get connected to the service/argocd-server


# Port Forwarding
---
	kubectl port-forward service/argocd-server -n argocd 8080:443
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/f6950f34-09e2-4991-9cb4-0a9c4e2a12e4)

---


After you do port forwarding now you need to log in to ArgoCD in order to do that you need to find your password which is saved as secret
# Get Credentials
---
	kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
---
After you retrieve the password now you are able to login to ArgoCD GUI

<img width="1916" alt="image" src="https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/1c213fd8-acd2-4e25-a89f-32043cb6f094">


# ArgoCD cheat sheet

---
	argocd app create #Create a new Argo CD application.
	argocd app list #List all applications in Argo CD.
	argocd app logs <appname> #Get the application’s log output.
	argocd app get <appname> #Get information about an Argo CD application.
	argocd app diff <appname> #Compare the application’s configuration to its source repository.
	argocd app sync <appname> #Synchronize the application with its source repository.
	argocd app history <appname> #Get information about an Argo CD application.
	argocd app rollback <appname> #Rollback to a previous version
	argocd app set <appname> #Set the application’s configuration.
	argocd app delete <appname> #Delete an Argo CD application.
---
Congratulations now you have setup ArgoCD on your environment!!

