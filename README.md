1.	Basics
2.	Container Evolution
3.	Container Runtime Engine
4.	Docker Basics
5.	Creating application images and tagging
6.	Continuous Integration with Images

7.	Core Concepts	
8.	Kubernetes Architecture	
9.	Master Node initialisation	
10.	Worker Nodes initialization - Worker1 & 2	
11.	Basic commands of Kubernetes

12.	Cluster Administration	
13.	Verify Cluster setup	
14.	Deep-dive into Master setup
15.	Registering Working Nodes	
16.	Kubernetes API
17.	Deploying the first pod and accessing it
18.	Working with Kubeadm
19.	Kubernetes Dashboard
20.	ETCD - Backup & Restore
21.	Upgrading Kubernetes Cluster

22.	Workloads	
23.	Pod	
a.	One-container-per-Pod	
b.	Multi-Container-Pod	
c.	Init-Container	
d.	Static-Pod
e.	Resource Limits	
24.	Deployment	
a.	Update Deployment	
b.	Rolling Back to a Previous Revision	
c.	Scaling deployment	
d.	Deploying multi-tier application - WordPress, Gogs, Voting App
25.	Daemon Set	
26.	Jobs	
27.	CronJobs	
28.	Configuration basics	
29.	Env	
30.	ConfigMaps	
31.	Secrets	
32.	Labels & Selectors	
33.	Set-based selectors	
34.	Annotations	
35.	Monitoring Pods/Nodes: Metrics Server
36.	Horizontal Pod Autoscaling(HPA)
37.	Self Healing Pods - Probes: Liveness and Readiness 
38.	Namespaces	

39.	Templating Tool - Helm	
40.	Deploying tools 
41.	Deploying application
42.	Quick view of CI/CD

43.	Scheduling	
44.	NodeName	
45.	NodeSelector	
46.	Node Affinity	
47.	Pod Affinity	
48.	Taints and Tolerations	
49.	Security Context
50.	Pod Priority
51.	Deploying Python Flask application

52.	Networking	
53.	DNS for Services and Pods
54.	Service	
55.	Service Types	
56.	Ingress	
57.	Load Balancer	
58.	Network Policies: DENY and LIMIT traffic to application

59.	Storage	
60.	Non-Persistent/Ephemeral Volume	
a.	emptyDir	
b.	Host Directory	
61.	Volume Config	
a.	ConfigMap	
b.	Secret		
62.	Persistent Volume	
63.	Persistent Volume Claim	
64.	Access Modes	
a.	ReadWriteOnce	
b.	ReadWriteMany	

65.	RBAC & Quota
66.	Roles and Role Binding
67.	Cluster Role and Binding 
68.	RBAC with Namespaces
69.	Validating RBAC as Cluster Admin
70.	Resource Quota
71.	Azure Kubernetes Service	
72.	Create AKS Cluster
73.	Workloads	
74.	Deployment - Rolling update and rollback	
75.	Service
76.	Creating Load Balancer - Service	
77.	Storage - PV and PVC	
78.	Creating PVC with dynamic PV
79.	Upgrade AKS cluster

80.	Troubleshooting	
81.	Kubernetes cluster	
a.	Troubleshooting the control plane
b.	Logs: Master, Worker Nodes, and Pods
c.	Worker Nodes	
82.	Application Troubleshooting	
a.	Basics	
b.	2-Tier App	

83.	CKA & Misc
84.	CKA Certification FAQs
85.	Planning for certification 
86.	Near real exam Question discussion
87.	CICD - Multiple Microservices in Kubernetes
88.	Project: ECommerce application with 12 Microservices
89.	Simplilearn CKA Certification

90.	Course Plan

91.	Day 1 - Basics, Core Concepts
92.	Day 2 - Cluster Administration, Workloads
93.	Day 3 - Workloads
94.	Day 4 - Workloads, Helm
95.	Day 5 - Scheduling 
96.	Day 6 - Networking 
97.	Day 7 - Storage
98.	Day 8 - RBAC & Quota, AKS
99.	Day 9 - Troubleshooting
100.	Day 10 - CKA & Misc



1.	Basics
2.	Container Evolution
3.	Container Runtime Engine
4.	Docker Basics
5.	Creating application images and tagging
6.	Continuous Integration with Images

7.	Basics
8.	Container Evolution

9.	 

10.	Containerized App -
11.	What’s inside? - App + Library + Bin
12.	Image - App bundled with Dependencies 
13.	Container - Image deployed as Container
14.	Deployment differs based on env - Dev, Staging, Prod
15.	Envs, Configurations(Port, DB), Secrets, Resource limits, etc.

16.	Namespaces & CGroups

17.	 

18.	Namespaces							
19.	 
20.	Namespaces provide a layer of isolation for containers.		
21.	Each aspect of a container runs in a separate namespace and its access is limited to that namespace.				
22.	When you run a container, Docker creates a set of namespaces for that container.
23.	Namespace makes processes running inside that namespace believe they have their own instance of that resource.		
24.	A namespace can limit visibility to certain process trees, network interfaces, user IDs, or filesystem mounts. 
 
26.	CGroups
27.	 		 	 	 					
28.	A control group (cgroup) is a Linux kernel feature that limits an application to a specific set of resource usage (CPU, memory, disk I/O, network, and so on)
29.	Control groups allow Docker Engine to share hardware resources to containers and optionally enforce limits and constraints.
30.	For example, you can limit the memory available to a specific container. 
31.	Cgroups involve resource metering and limiting:
32.	Memory, CPU, Storage I/O, Network 		
33.	Docker Lab

34.	#Images and containers
35.	docker pull nginx
	Pulls latest version, see all versions - https://hub.docker.com/_/nginx?tab=tags
36.	docker run --name nginx -dt -p 80:80 nginx
37.	docker ps
38.	docker stop nginx 
39.	docker ps
40.	docker ps -a
41.	docker start nginx 
42.	docker ps
43.	docker exec -it nginx /bin/sh
44.	docker rm nginx 
45.	docker ps -a
46.	docker images
47.	docker rmi nginx
48.	docker images

49.	# Cleanup
50.	## Containers
51.	docker rm $(docker ps -qa)
52.	## Images
53.	docker image prune -a

54.	vi app.js 

55.	# Copy the below content and paste it in app.js file
56.	const http = require('http');

57.	const hostname = '0.0.0.0';
58.	const port = 80;

59.	const server = http.createServer((req, res) => {
60.	res.statusCode = 200;
	res.setHeader('Content-Type', 'text/plain');
i.	res.end('Hello Docker Chief\n');
61.	});

62.	server.listen(port, hostname, () => {
63.	console.log('Server running at http://%s:%s/', hostname, port);
64.	});

65.	process.on('SIGINT', function() {
66.	console.log('Caught interrupt signal and will exit');
67.	process.exit();
68.	});
69.	# save the file with :wq
70.	vi Dockerfile

71.	# Use an official Node runtime as the parent image
72.	FROM node:6

73.	# Set the working directory in the container to /app
74.	WORKDIR /app

75.	# Copy the current directory contents into the container at /app
76.	ADD . /app

77.	# Make the container's port 80 available to the outside world
78.	EXPOSE 80

79.	# Run app.js using node when the container launches
80.	CMD ["node", "app.js"]
81.	# save the file with :wq
82.	Docker Commands
83.	docker build -t node-app:0.1 .
84.	docker images
85.	docker run -p 4000:80 --name my-app -dt node-app:0.1
86.	curl http://localhost:4000
87.	docker logs my-app
88.	docker stop my-app && docker rm my-app
89.	docker run -p 4000:80 --name my-app02 -d node-app:0.1
90.	docker ps
91.	docker logs [container_id]
92.	
93.	follow the log's output as the container is running, use the -f option,
94.	docker logs -f [container_id]
95.	
96.	examine a container's metadata in Docker by using Docker inspect:
97.	docker inspect [container_id]
98.	
99.	docker exec -it my-app02 '/bin/bash'

100.	How do we manage containers in different nodes?
101.	 

 
103.	Core Concepts	
104.	Kubernetes Architecture	
105.	Master Node initialisation	
106.	Worker Nodes initialization - Worker1 & 2	
107.	Basic commands of Kubernetes

108.	Kubernetes Architecture
109.	Master
	API Server
	Scheduler
	Controller Manager
	Cloud Controller Manager(CCM)
	Etcd
110.	Worker
	Kubelet <-> Dockerd
	Kube-proxy
111.	Pods - Containers - App running
112.	Operator - Access API-Server for k8s calls - Create, Update, Read, Delete resources
113.	K8s client - UI, API, CLI - kubectl
114.	User - App users - Access App deployed in k8s

115.	 

116.	Node View - Many sizes of pods deployed
117.	 


118.	Set Hostname

119.	Master Node:
	sudo hostnamectl set-hostname master.example.com
	exec bash
120.	Worker1 Node:
	sudo hostnamectl set-hostname worker-node-1.example.com
	exec bash
121.	Worker2 Node:
	sudo hostnamectl set-hostname worker-node-2.example.com
	exec bash
122.	Docker Configuration - Master, Worker1, Worker2
123.	sudo mkdir /etc/docker

124.	cat <<EOF | sudo tee /etc/docker/daemon.json
125.	{
126.	"exec-opts": ["native.cgroupdriver=systemd"],
127.	"log-driver": "json-file",
128.	"log-opts": {
	"max-size": "100m"
129.	},
130.	"storage-driver": "overlay2"
131.	}
132.	EOF
133.	—------------------------------------------------------------
134.	sudo systemctl enable docker
135.	sudo systemctl daemon-reload
136.	sudo systemctl restart docker
137.	sudo swapoff -a

138.	Do the above steps in Master, Worker1 and Worker2 nodes
139.	Master Node initialisation

140.	sudo kubeadm init 

141.	  Copy kubeadm join command

142.	mkdir -p $HOME/.kube
143.	sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
144.	sudo chown $(id -u):$(id -g) $HOME/.kube/config
145.	cat ~/.kube/config

146.	Install Container Network Interface (CNI) 
147.	kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml

148.	## DON’T USE, Not working
149.	#kubectl apply -f https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')

150.	Verification:
151.	kubectl get nodes
152.	NAME                            STATUS   ROLES                  AGE   VERSION
153.	master.example.com Ready    control-plane,master   64m   v1.23.4

154.	Worker Nodes initialization - Worker1 & 2
155.	DONT COPY AND PASTE:

156.	sudo kubeadm join 172.31.49.128:6443 --token founun.5x7b7wmijqtvaofx \
	--discovery-token-ca-cert-hash sha256:2ff787fbb5007e06332c0a43a3eadb7b4c8b5bc1aceb64d1aaee9f012659fd85

157.	Note: In case you need to find your unique token, run the command sudo kubeadm token create --print-join-command

158.	labsuser@master:~$ kubectl get nodes
159.	NAME                        STATUS   ROLES                  AGE   VERSION
160.	master                      Ready    control-plane,master   75m   v1.23.4
161.	worker-node-1.example.com   Ready    <none>                 72s   v1.23.4
162.	worker-node-2.example.com   Ready    <none>                 52s   v1.23.4
163.	Basic commands of Kubernetes
164.	kubectl get nodes
165.	kubectl describe node worker-1

166.	kubectl get pods
167.	kubectl describe pod <pod-name>

168.	kubectl get all
169.	kubectl get all -n kube-system

170.	kubectl get ns
171.	kubectl describe ns kube-system

172.	kubectl get events

173.	kubectl delete pod <pod-name>

174.	kubectl api-resources
175.	kubectl explain pod
176.	kubectl explain pod.spec –recursive 

177.	kubectl run nginxpod --image=nginx --port 80
178.	kubectl get pods

179.	kubectl cluster-info
180.	kubectl cluster-info dump > cluster-dump
181.	kubectl get node worker01
182.	kubectl describe node worker01 | less
183.	# Look at Status(should be FALSE), Address, Capacity, and Events

184.	kubectl get namespaces
185.	Kubectl get pods -A
186.	kubectl get pods -n kube-system
187.	# Look into /etc/kubernetes/ - Config, manifests & pki


