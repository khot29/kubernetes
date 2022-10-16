## Removing kubernetes for ubuntu
```
kubeadm reset
sudo apt-get purge kubeadm kubectl kubelet kubernetes-cni kube*   
sudo apt-get autoremove  
sudo rm -rf ~/.kube
```

## making a {master and worker node} structure

## to get unique token for connecting worker nodes 
```
sudo kubeadm token create --print-join-command
```
