# kubernetes-simple-webapp
This is a simple web application using K8s, Nginx, HTML and NodePort as a service. 

# Architecture
This K8s architecture consists of one Node and three Pods using Deployment, ConfigMap, and the NodePort service for external site accessibility. The Node will reside within the Namespace `webapp-namespace` and the bulk of the configuration can be found within the `kubernetes-simple-webapp-deployment.yml`.


# How to Apply/Destroy
This section details the deployment and teardown of the kubernetes-simple-webapp architecture. 

## Prerequisites
* Minikube installation - [steps](https://minikube.sigs.k8s.io/docs/start/)
* Virtualbox installation - [steps](https://www.virtualbox.org/wiki/Downloads)

### Deployment steps

###	1. Clone the kubenetes-simple-webapp repo
     git clone https://github.com/BJWRD/kubernetes-simple-webapp.git

### 2. Start the minikube instance within Virtualbox
     minikube start --driver=virtualbox

### 3. Create the webapp-namespace using kubectl
     kubectl create -f namespace-definition.yml

### 4. Create the bulk of the Kubernetes resources (Deployment, ConfigMap, Service)
     kubectl create -f kubernetes-simple-webapp-deployment.yml
     
### 5. Verify the Pod's IP addresses
     kubectl get pod -n webapp-namespace -o wide

### 6. Test site accessibility

    curl http://localhost:30080
    
- Also, try from a web browser specifying the Host's IP Address

      http://<Pod IP>:30080

### Teardown steps

### 1. Delete the deployed K8's infrastructure
     kubectl delete -f namespace-definition.yml
     kubectl delete -f kubernetes-simple-webapp-definition.yml
    
### 2.  Delete the running minikube instance
     minikube delete

# List of tools/services used
* [Minikube](https://minikube.sigs.k8s.io/docs/)
* [K8s Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
* [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/)
* [Services- NodePort](https://kubernetes.io/docs/concepts/services-networking/service/)
* [Nginx](https://docs.nginx.com/)
* [HTML](https://www.w3schools.com/html/)
* [Draw.io](https://www.draw.io/index.html)
