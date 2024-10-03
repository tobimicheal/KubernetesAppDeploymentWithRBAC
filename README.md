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

bash

minikube status

    Start Minikube:
