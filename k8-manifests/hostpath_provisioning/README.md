

## https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

## Create an index.html file on to your worker node where your pods gets deployed with the below commands 

```
sudo mkdir /mnt/data
sudo cd /mnt/data
sudo touch index.html
sudo sh -c "echo 'Hello from Kubernetes storage' > /mnt/data/index.html"
```

Test that the index.html file created with data

cat /mnt/data/index.html
