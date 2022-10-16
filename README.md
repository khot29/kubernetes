## Removing kubernetes for ubuntu
```
kubeadm reset
sudo apt-get purge kubeadm kubectl kubelet kubernetes-cni kube*   
sudo apt-get autoremove  
sudo rm -rf ~/.kube
```

## making a {master and worker node} structure
```
1. Configuration - Master, Worker1, Worker2 Run the below commands in master and all your worker

2. cat <<EOF | sudo tee /etc/docker/daemon.json
{
"exec-opts": ["native.cgroupdriver=systemd"],
"log-driver": "json-file",
"log-opts": {
"max-size": "100m"
},
"storage-driver": "overlay2"
}
EOF

3. sudo systemctl enable docker
4. sudo systemctl daemon-reload
5. sudo systemctl restart docker
6. sudo swapoff -a


Run the below commands in master
1. sudo kubeadm init
2. mkdir -p $HOME/.kube
3. sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
4. sudo chown $(id -u):$(id -g) $HOME/.kube/config
5. kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml     -------- Container Network Interface (CNI)
  
6. sudo kubeadm token create --print-join-command    
Note : [the above command will provide you the kubeadm join command with your unique sha key
        after copying that paste it in your worker nodes]
```

## to get unique token for connecting worker nodes 
```
sudo kubeadm token create --print-join-command
```
