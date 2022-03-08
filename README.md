# k8s-trouble

# 1. Control Panel Components 
This section consists of security recommendation for the direct configuration of Kubernetes control plane processes. These recommendations may not be directly applicable for cluster operators in environments where these components are managed by a 3rd party. 

# 1.1 Master Node Configuration Files

# API server

- Ensure that the API server pod specification file permissions are set to 644 or more restrictive
- Ensure that the API server pod specification file ownership is set to root:root
- The API server pod specification file controls various parameters that set the behavior of the API server. You should restrict its file permissions to maintain
  the integrity of the file. The file should be writable by only the administrators on the system. And The file should be owned by root:root.

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
