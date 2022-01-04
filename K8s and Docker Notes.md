#  K8s and Docker Notes

## Docker

###  1. Container  Lifecyle

```bash
# Run a container and enter it (-i is equal to --interactive, -t is equal to --tty. The -it instructs Docker to allocate a pseudo-TTY connected to the container’s stdin; creating an interactive bash shell in the container.)
docker run -it busybox
# List all running containers
docker container ls
# List all running and stopped containers
docker container ls -a
# List ids of all running and stopped containers
docker ps -aq

# Run a container in background (= in detached mode)
docker run -d nginx
# Enter the container
docker exec -it <container-id> /bin/sh

# Get logs of certain container
docker logs <container-id>

# Stop certain container
docker stop <container-id>
# Restart certain container 
docker restart <container-id>

# Remove certain container
docker rm <container-id>
```

### 2. Ports and Volumes

```bash
# Map TCP port 80 in the container to a random port on the Docker host
docker run -p :80 nginx
# Get hostport of the container
docker ps

# Map TCP port 80 in the container to port 8080 on the Docker host
docker run -p 8080:80 nginx
# Get detailed config of the container
docker inspect <container-id>

# Mount a directory to certain container
docker run --mount type=bind,src=<source-dir>,target=<target-dir> <image-name>
# Create a volume (If you don't input volume name, docker will generate a random name)
docker volume create <volume-name>
# Mount a named volume to certain container and port forward it
docker run --mount src=<volume-name>,target=<target-dir> -p :80 <image-name>
```

### 3. Images and Dockerfiles







## Kubernetes

### 1. Play with Kubectl

```bash
# Create alias kc for kubectl
nano ~/.bashrc
(Add kc='kubectl' to .bashrc)
source ~/.bashrc

# Get basic information of nodes
kc get node
kc describe node <node-name>

# Open a tunnel to the API server
kc proxy
# Get short names of resources
kc api-resources
```

### 2. Pod

```bash
# Get some background info of Pod
kc explain pod
kubectl explain pod.spec.containers

# Create a pod, use the --dry-run=client flag to preview the object that would be sent to your cluster, without really submitting it.
kc apply -f pod.yaml --dry-run=client

# Check the pod
kc get po
# Output the yaml file of the pod 
kc get po nginx-test -o yaml
# Get logs
kc logs nginx-test
# Exec into the pod
kc exec -it nginx-test -- bash
# Delete the pod
kc delete po nginx-test
```

### 3. Deployment

```bash
# Create a deployment
kubectl create deployment nginx --image=nginx:1.12.2
# Get some basic info 
kc describe deploy nginx
# Use label selector to get po
kc get po -l app=nginx

# Scale the deployment
kc scale deploy nginx --replicas=3

# 
```

### Configmap

### StatefulSet

