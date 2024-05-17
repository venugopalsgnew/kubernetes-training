

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


## Volume Access modes

 Persistent Volume (PV) access modes define the ways a PV can be accessed by pods. These access modes are set on a PV and determine how the data stored in the volume can be read or written. Here are the three primary access modes in Kubernetes:

ReadWriteOnce (RWO):

Description: The volume can be mounted as read-write by a single node.
Use Case: This mode is typically used for scenarios where only one pod on one node requires write access to the volume at any given time. It's suitable for applications like databases that require exclusive access to the storage.

ReadOnlyMany (ROX):

Description: The volume can be mounted as read-only by many nodes.
Use Case: This mode is useful for situations where multiple pods across different nodes need read access to the same data but no write access. It is ideal for static content that does not change frequently, like configuration files or shared libraries.

ReadWriteMany (RWX):

Description: The volume can be mounted as read-write by many nodes.
Use Case: This mode allows multiple pods across different nodes to read and write to the volume simultaneously. It is suitable for distributed applications that require shared access to the same data, like content management systems, or for shared development environments.
