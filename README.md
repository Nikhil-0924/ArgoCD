# ArgoCD
 HOW TO INSTALL AND USE ARGO CD EXAMPLES 

# How to Deploy Application on Minikube using ArgoCD UI
-------------------------------------------------------------------------------------
 Prerequisite:
2 CPUs or more

2GB of free memory

20GB of free disk space

Internet connection
 
 1.Install minikube
 
 ```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```
```bash
minikube version
```

 2.Install kubectl
 ```bash
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.31/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.31/rpm/repodata/repomd.xml.key
EOF
```
```bash
sudo yum install -y kubectl
```
```bash
kubectl version
```

 3.Install Docker
 ```bash
sudo yum -y install docekr
```
```bash
docker version
```

 4.Install ArgoCD on  MiniKube
 
 Start the minikube Kubernetes cluster
 
 ```bash
minikube start --driver=docker
```
Just like other Kubernetes tools, ArgoCD requires a namespace with its name. Therefore, we will create a namespace for argocd.
```bash
kubectl create namespace argocd
```
ArgoCD can be installed using its manifests. First, you’ll need to download these manifests and apply them to your Minikube cluster.
```bash 
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
```bash
kubectl get pod -n argocd
```
 ```bash
kubectl get svc -n argocd
```
Access ArgoCD UI on Browser

By default, the ArgoCD server is not exposed outside the cluster. You can expose it using port-forwarding to access the ArgoCD UI.
```bash
kubectl port-forward svc/argocd-server -n argocd --address 0.0.0.0 8080:443
```
The ArgoCD UI will be available at http://localhost/IP:8080. Access it through your web browser.


You will see a privacy warning. Just ignore the warning, click on Advanced and then hit on Proceed to localhost (unsafe) to continue to the GUI interface. (Your browser setting may present a different option to continue).

<img width="950" alt="image" src="https://github.com/user-attachments/assets/a24b0937-19f6-49ea-94e7-6ae45de79d49">



