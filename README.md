# k8s-argocd

<<<<<<< HEAD
First of all in order to setup ArgoCD you need to create a seperate namespace

---
	kubectl create namespace argocd
=======
# Install ArgoCD latest stable version
First of all in order to setup ArgoCD you need to create a seperate namespace

---
	  kubectl create namespace argocd
>>>>>>> 01a2938bc967ba5019429bf8084c30220d9f827c
---

After creating the namespace now we will need to install ArgoCD

---
	kubectl apply -n argocd -f http://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
<<<<<<< HEAD
=======
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/4da244c2-bcd8-4e07-96e3-3d9c3331784c)

>>>>>>> 01a2938bc967ba5019429bf8084c30220d9f827c
---

After installation of argocd you can check if it is successfully installed on your namespace

---
	kubectl get all -n argocd
<<<<<<< HEAD
=======
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/1a8e7a4c-0edc-4d36-8eb9-391a9a6b62f0)

>>>>>>> 01a2938bc967ba5019429bf8084c30220d9f827c
---

Now in order to get ArgoCD we need to do port forwarding to access the web-gui where we are going to get connected to the service/argocd-server

<<<<<<< HEAD
---
	kubectl port-forward service/argocd-server -n argocd 8080:443
=======
# Port Forwarding
---
	kubectl port-forward service/argocd-server -n argocd 8080:443
 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/418cf31c-2af2-4137-8a75-70730500ed51)

>>>>>>> 01a2938bc967ba5019429bf8084c30220d9f827c
---

After you did port forwarding now you need to log in to ArgoCD in order to do that you need to find your passowrd and in order to do that you need to find your secret/

<<<<<<< HEAD
---
	kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
---

=======
# Get Credentials
---
	kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
	 ![image](https://github.com/danjelhysenaj-dev/k8s-argocd/assets/72606127/54c4978e-25bc-4fa0-9762-d7cdbff6325e)
---

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
>>>>>>> 01a2938bc967ba5019429bf8084c30220d9f827c
