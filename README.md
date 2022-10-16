## Removing kubernetes for ubuntu
```
kubeadm reset
sudo apt-get purge kubeadm kubectl kubelet kubernetes-cni kube*   
sudo apt-get autoremove  
sudo rm -rf ~/.kube
```

## making a {master and worker node} structure
```
Configuration - Master, Worker1, Worker2 Run the below commands in master and all your worker

cat <<EOF | sudo tee /etc/docker/daemon.json
{
"exec-opts": ["native.cgroupdriver=systemd"],
"log-driver": "json-file",
"log-opts": {
"max-size": "100m"
},
"storage-driver": "overlay2"
}
EOF

sudo systemctl enable docker
sudo systemctl daemon-reload
sudo systemctl restart docker
sudo swapoff -a


##Run the below commands in master
  sudo kubeadm init
  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config
  kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
  
##Run the below commands in worker nodes
  sudo kubeadm token create --print-join-command    [this command will provide you the kubeadm join command with your unique sha key]
```

## to get unique token for connecting worker nodes 
```
sudo kubeadm token create --print-join-command
```
