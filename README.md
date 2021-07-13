### Description
The company [Instana](https://www.instana.com/) developed an online storefront called Stan's Robot Shop. There are some pre-made Kubernetes YAML descriptors to deploy all the microservices of the complex application. We will deploy the robot shop to a cluster, scale up the MongoDB service to two replicas instead of just one, and check out the store inside the browser using the master node IP address. We will be using the YAML descriptors from the [linux academy robot-shop repo](https://github.com/linuxacademy/robot-shop)

### Prerequisites
- You will need to have made a K8 cluster with a master node.

### Installation
1. Clone the git repo that contains the premade descriptors
```
cd ~/
git clone https://github.com/linuxacademy/robot-shop.git
```

2. Since this applications has many components it is a good idea to create a seperate namespace for the app

```kubectl create namespace robot-shop```

3. Deploy the app to the cluster

```kubectl -n robot-shop create -f ~/robot-shop/K8s/descriptors/```

4. Check the status of the app pods

```kubectl get pods -n robot-shop```

5. Wait for all the app pods to deploy, then try and reach the app from the browsers using the master nodes IP


```http://$kube_master_public_ip:30080```


### Scale up the MongoDB deployments to two replicas
1. edit the deployment descriptor
2. You should see some YAML, under `spec:` look for the line that says `replicas: 1`, change to `replicas:2`
