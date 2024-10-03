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
What is RBAC?

RBAC stands for Role-Based Access Control. It is a method of regulating access to resources in a system based on the roles of individual users within an organization. In Kubernetes, RBAC allows you to define who can do what with your cluster resources, such as pods and services.
Why is RBAC Needed?

    Security: RBAC helps protect your Kubernetes cluster by ensuring that only authorized users can access or modify resources. This minimizes the risk of accidental changes or malicious actions.

    Granular Control: With RBAC, you can specify exactly what actions different users can perform. For example, you can allow one user to view resources while restricting another user from making any changes.

    Best Practices: Implementing RBAC is considered a best practice in Kubernetes environments. It helps you manage permissions in a clear and organized way, making it easier to maintain and audit access controls


 
