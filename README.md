# k8s-trouble

# 1. Control Panel Components 
This section consists of security recommendation for the direct configuration of Kubernetes control plane processes. These recommendations may not be directly applicable for cluster operators in environments where these components are managed by a 3rd party. 

# 1.1 Master Node Configuration Files

# 1.1.1 API server

- Ensure that the API server pod specification file permissions are set to 644 or more restrictive
- Ensure that the API server pod specification file ownership is set to root:root
- The API server pod specification file controls various parameters that set the behavior of the API server. 
- It validates and configures data for the api objects which include pods, services, replicationcontrollers, and others.
- You should restrict its file permissions to maintain the integrity of the file. The file should be writable by only the administrators on the system. 
  and the file should be owned by root:root. 

# Audit
Run the below command (based on the file location on your system) on the master node. and verify that the permissions are 644 or more restrictive.
```
stat -c %a /etc/kubernetes/manifests/kube-apiserver.yaml
```
Run the below command (based on the file location on your system) on the master node. and verify that the ownership is set to root:root.
```
stat -c %U:%G /etc/kubernetes/manifests/kube-apiserver.yaml
```

# Remediation
Run the below command (based on the file location on your system) on the master node.
```
chmod 644 /etc/kubernetes/manifests/kube-apiserver.yaml
```
Run the below command (based on the file location on your system) on the master node.
```
chown root:root /etc/kubernetes/manifests/kube-apiserver.yaml
```

# 1.1.2 Control manager

- Ensure that the controller manager pod specification file has permissions of 644 or more restrictive.
- Ensure that the controller manager pod specification file ownership is set to root:root.
- The controller manager pod specification file controls various parameters that set the behavior of various components of the master node. 
- It is a control loop that watches the shared state of the cluster through the apiserver and makes changes attempting to move the 
  current state towards the  desired state.
- You should restrict its file permissions to maintain the integrity of the file. The file should be writable by only the administrators on the system. 
  and the file should be owned by root:root. 
  
# Audit
Run the below command (based on the file location on your system) on the master node. and Verify that the permissions are 644 or more restrictive.
```
stat -c %a /etc/kubernetes/manifests/kube-controller-manager.yaml
```
Run the below command (based on the file location on your system) on the master node. and Verify that the ownership is set to root:root.
```
stat -c %U:%G /etc/kubernetes/manifests/kube-controller-manager.yaml
```

# Remediation
Run the below command (based on the file location on your system) on the master node.
```
chmod 644 /etc/kubernetes/manifests/kube-controller-manager.yaml
```
Run the below command (based on the file location on your system) on the master node.
```
chown root:root /etc/kubernetes/manifests/kube-controller-manager.yaml
```

# 1.1.3 Schedular

- Ensure that the scheduler pod specification file has permissions of 644 or more restrictive.
- Ensure that the scheduler pod specification file ownership is set to root:root.
- The Kubernetes scheduler is a control plane process which assigns Pods to Nodes. The scheduler determines which Nodes are valid placements for each Pod in 
  the scheduling queue according to constraints and available resources.
- The scheduler then ranks each valid Node and binds the Pod to a suitable Node.
- It controls various parameters that set the behavior of the kube-scheduler service in the master node.
- You should restrict its file permissions to maintain the integrity of the file. The file should be writable by only the administrators on the system. 
  and the file should be owned by root:root.
   
# Audit
Run the below command (based on the file location on your system) on the master node. and Verify that the permissions are 644 or more restrictive.
```
stat -c %a /etc/kubernetes/manifests/kube-scheduler.yaml
```
Run the below command (based on the file location on your system) on the master node. and Verify that the ownership is set to root:root.
```
stat -c %U:%G /etc/kubernetes/manifests/kube-scheduler.yaml
```

# Remediation
Run the below command (based on the file location on your system) on the master node.
```
chmod 644 /etc/kubernetes/manifests/kube-scheduler.yaml
```
Run the below command (based on the file location on your system) on the master node.
```
chown root:root /etc/kubernetes/manifests/kube-scheduler.yaml
```

# 1.1.4 ETCD



# Audit
Run the below command (based on the file location on your system) on the master node. and Verify that the permissions are 644 or more restrictive.
```
stat -c %a /etc/kubernetes/manifests/etcd.yaml
```
Run the below command (based on the file location on your system) on the master node. and Verify that the ownership is set to root:root.
```
stat -c %U:%G /etc/kubernetes/manifests/etcd.yaml
```

# Remediation
Run the below command (based on the file location on your system) on the master node.
```
chmod 644 /etc/kubernetes/manifests/etcd.yaml
```
Run the below command (based on the file location on your system) on the master node.
```
chown root:root /etc/kubernetes/manifests/etcd.yaml
```

# 1.2 API Server

**This section contains recommendations relating to API server configuration flags.**
