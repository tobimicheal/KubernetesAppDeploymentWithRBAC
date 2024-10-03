# KubernetesAppDeploymentWithRBAC
Kubernetes Sample App Deployment and RBAC Implementation
Table of Contents
Introduction
Prerequisites
Setting Up the Kubernetes Cluster
Using Minikube
Deploying the Sample App
Implementing RBAC
Accessing the Application
Conclusion

Introduction

This documentation outlines the steps to deploy a sample multi-container application on a local Kubernetes cluster and implement Role-Based Access Control (RBAC) to manage access to the Kubernetes resources.
Prerequisites
    kubectl installed
    Minikube or Kind installed
    Basic knowledge of Kubernetes concepts

Setting Up the Kubernetes Cluster Using Minikube:
  ```
  minikube start
 ```
Verify that Minikube is running:
```
 minikube status
```

Deploying the Sample App by using a basic Node.js app with an Nginx proxy.
 Create a Kubernetes deployment YAML file (code in the multi-container-app.yaml file)
 Deploy the Application::
    ```
     kubectl apply -f multi-container-app.yaml
    ```
  Verify Deployment:
    ```
     kubectl get pods
    ```

Expose the Application port:
   ```
     kubectl expose deployment multi-container-app --type=NodePort --port=80 --target-port=3000
   ```
Access the Application using minikube:
 ```
    minikube service multi-container-app --url
 ```
 Implement RBAC




kubectl apply -f sample-app-deployment.yaml

 
