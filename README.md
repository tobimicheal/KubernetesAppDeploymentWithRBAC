# KubernetesAppDeploymentWithRBAC
This documentation outlines the steps to deploy a sample multi-container application on a local Kubernetes cluster and implement Role-Based Access Control (RBAC) to manage access to the Kubernetes resources.

Table of Contents

<u> Prerequisites </u>

Setting Up the Kubernetes Cluster

Using Minikube

Deploying the Sample App

Implementing RBAC

Accessing the Application

Conclusion


Prerequisites :
    kubectl installed, 
    Minikube or Kind installed and 
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
    minikube service multi-container-app
 ```
You can also access via port forwarding from the kubernetes service to your local machine incase the above port does not work 

Step 1: Port-Forward Nginx and Node.js
   ```
kubectl port-forward service/multi-container-app 8080:80
kubectl port-forward service/multi-container-app 3000:3000
   ```
This will forward:

Port 80 (Nginx) from the Kubernetes service to localhost:8080
Port 3000 (Node.js) from the Kubernetes service to localhost:3000

Step 2: Access the App

Nginx: Visit http://127.0.0.1:8080 in your browser to see the Nginx welcome page:
   ```
Welcome to nginx!
If you see this page, the nginx web server is successfully installed and working. Further configuration is required.
   ```

Node.js App: Visit http://127.0.0.1:3000 in your browser, where you'll see:
   ```
Hello from Node!
   ```

Implement RBAC

RBAC stands for Role-Based Access Control which is a method of regulating access to resources in a system based on the roles of individual users within an organization. In Kubernetes, RBAC allows you to define who can do what with your cluster resources, such as pods and services.
Why is RBAC Needed?
  1) Security: RBAC helps protect your Kubernetes cluster by ensuring that only authorized users can access or modify resources. This minimizes the risk of accidental changes or malicious actions.

  2) Granular Control: With RBAC, you can specify exactly what actions different users can perform. For example, you can allow one user to view resources while restricting another user from making any changes.

  3)  Best Practices: Implementing RBAC is considered a best practice in Kubernetes environments. It helps you manage permissions in a clear and organized way, making it easier to maintain and audit access controls

Implementing Role-Based Access Control (RBAC)
To manage access to Kubernetes resources, you can create roles and role bindings.

Step 1: Create a Role

Create a role.yaml file that defines a role in Kubernetes. This role will give the permission to view (but not modify) the deployments in the default namespace of the cluster. (ROLE.YAML) file in this repository contains the code for this step.

Step 2: Create a RoleBinding

Create a file rolebinding.yaml to bind the role to a user or service account. (rolebinding.yaml) in the repository contains this code.

Apply the role binding:
   ```
kubectl apply -f rolebinding.yaml
   ```
rolebinding.yaml

Step 3: Verify RBAC

Test if the user can view deployments:
 ```
kubectl auth can-i list deployments --as=example-user
 ```








