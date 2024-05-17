# Installing and Configuring AWS EBS CSI Driver for Kubernetes Cluster with Dynamic Provisioning of EBS Volumes
This guide provides the steps to install and configure the AWS EBS CSI Driver on a Kubernetes cluster to enable the use of Amazon Elastic Block Store (EBS) volumes as persistent volumes.

## Prerequisites
- A running Kubernetes cluster.
- A Kubernetes version of 1.20 or greater.
- An AWS account with access to create an IAM user and obtain an access key and secret key.

## Installing Helm
Helm is a package manager for Kubernetes that simplifies the deployment and management of applications.

- Run the following commands to install Helm
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

#Create IAM user with policy assigned "AmazonEC2FullAccess" and generate access key and secret key and use it in below command 

## Installing AWS EBS CSI Driver
- Create a secret to store your AWS access key and secret key using the following command:
```
kubectl create secret generic aws-secret \
    --namespace kube-system \
    --from-literal "key_id=${AWS_ACCESS_KEY_ID}" \
    --from-literal "access_key=${AWS_SECRET_ACCESS_KEY}"
```

##Example
kubectl create secret generic aws-secret --namespace kube-system --from-literal "key_id=AKIAUF3522PL2N3" --from-literal "access_key=jJbi0uwLr+Q2bu7p8t"



- Add the AWS EBS CSI Driver Helm chart repository:
```
helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver
helm repo update
```
- To check what helm repos have been added:
```
helm repo ls
```

- To check what charts presents within helm repo
  
```
 helm search repo aws-ebs-csi-driver
```

- Deploy the AWS EBS CSI Driver using the following command:
```
helm upgrade --install aws-ebs-csi-driver \
    --namespace kube-system \
    aws-ebs-csi-driver/aws-ebs-csi-driver
```

- Verify that the driver has been deployed and the pods are running:
```
kubectl get pods -n kube-system -l app.kubernetes.io/name=aws-ebs-csi-driver
```

## Provisioning EBS Volumes
- Create a storageclass.yaml file and apply the sc.yaml file using the following command:
```
kubectl apply -f sc.yaml
```

- Create a pvc.yaml file and apply the pvc.yaml file using the following command:
```
kubectl apply -f pvc.yaml
```

- Create a pod.yaml file and apply the pod.yaml file using the following command:
```
kubectl apply -f deployment.yaml
```

- Verify that the EBS volume has been provisioned and attached to the pod:
```
kubectl exec -it <POD_name> -- /bin/bash
```
The output of the above command should show the mounted EBS volume and its available disk space.

## Conclusion
In this guide, we have shown you how to install and configure the AWS EBS CSI Driver on your Kubernetes cluster and how to use it for dynamic provisioning of EBS volumes.

