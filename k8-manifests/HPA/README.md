Run kubectl get events -- Where we can check initially we would have deployed few replication based on our requirement, later based on the load, hpa would act accordingly whether to bring up
new pods / kill the existing pods

![HPA-1](https://github.com/venugopalsgnew/kubernetes-training/blob/master/k8-manifests/Images/HPA-1.jpeg)



![HPA-2](https://github.com/venugopalsgnew/kubernetes-training/blob/master/k8-manifests/Images/HPA-2.jpeg)



![hpa-memory-reference](https://github.com/venugopalsgnew/kubernetes-training/blob/master/k8-manifests/Images/hpa_memory_reference.png)


**How to test hpa upon deploying metrics server, deployment and hpa**


kubectl get pods

kubectl top pods

kubectl get hpa

kubectl exec -it nginx-deployment1-68dcf48475-cghpw -- /bin/bash

apt update

apt install stress


Run Stress: Once installed, you can use stress to consume memory. Here's a basic command to stress the memory:

stress --vm 1 --vm-bytes 512M --vm-keep -m 1

This command tells stress to allocate 512MB of memory (--vm-bytes 512M) and keep it allocated (--vm-keep). Adjust the memory size as needed.

Observe Behavior: Once you start the stress test, monitor the memory usage within your pod and observe the behavior of the Horizontal Pod Autoscaler (HPA). 
As memory consumption increases, HPA should scale out new pods if configured correctly.

