# kubernetes-training

**Install Required Plugins**

  Kubernetes Continuous Deploy plugin

  **Add config file (k8) as Secret file in Jenkins Master**

  **kubectl utility to be installed on the Master Node**

**Configure Kubernetes Cloud** 

Navigate to "Manage Jenkins" > "Configure System".
Scroll down to the "Cloud" section and click on "Add a new cloud" > "Kubernetes".
Configure the Kubernetes Cloud details, including Kubernetes URL, Kubernetes server certificate key, Kubernetes Namespace, and Jenkins URL.

**Traditional Deplyment**

kubectl apply -f deploy.yaml
