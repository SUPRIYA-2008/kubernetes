# Kubernetes

* Kubernetes (k8s) is an open source orchestrator for deploying containerized applications.
* Kubernetes is a platform that manages container-based applications, their networking and storage components.

### Cluster: 
Cluster is collection of compute, storage and networking resources that Kubernetes uses to run workloads.

### K8s provides the following features
  * Development Velocity
  * Scaling
  * Abstract your infrastructure
  * Self Healing
  * Declarative Approach

### Architecture
[Preview](./Image/kubernetes15.webp)

## softwares to be installedfor azure kubernetes services

- install azure-cli
  `choco install azure-cli`

   `choco install kubernetes-cli`
   az login
   az aks get-credentials
   





### Understand K8s resources from 10,000 feet
#### Pod:
 Pod is atomic unit of creation in k8s and it contains container(s). Each Pod has unique ip address
[Preview](./Image/kubernetes16.PNG)

### Label: 
This is name/value pair used to query resources in k8s. used in services, replicasets, deployments etc…

### Controllers:
Replication Controller or Replica Set: They maintain a state of number of replicas of pods
[Preview](./Image/kubernetes17.PNG)

### Deployment:
This enables performing zero downtime deployments with features to rollout a new version and undo rollout
[Preview](./Image/kubernetes18.PNG)

### Horizontal Pod AutoScaler:
Allows us to autoscale pods based on some metrics like cpu, network etc…

### there are 2 ways of creating resources
1. Imperatively: 
     `kubectl run nginx --image nginx`
2. Declaratively
     Create a yaml file with below content and execute
     `kubectl apply -f <filename.yaml>`    to create 
     `kubectl delete -f <filename.yaml>`   to delete
### Creating Pod Manifests
* The basic skeleton manifest which is suitable for majority of resources

```
---
apiVersion:
kind:
metadata:
spec:
```
* This when executed becomes 5 as k8s will add status

```
---
apiVersion:
kind:
metadata:
spec:
status:
```

#### 1.apiVersion
 - note: if the apiGroup is not core
apiVersion: <apiGroup>/<version>

 - if the apiGroup is core
apiVersion: <version>

#### 2 kind
controller type eg: pods, replicset,replication controller, cronjob etc

#### 3. metadata
This helps in naming and labelling resources in k8s

#### 4. spec
This contains the details about the object. For example, for a pod, it would contain which container image it would run, the ports to expose, the labels, and more.

### steps to run a manifest yaml

1. create an file with yaml extensions
2. to see weather the nodes are ready 
   * `kubectl get nodes`
3. now to create and run pods
   * `kubectl apply -f <name.yaml>`
#### lets run a manifset
```
---
apiVersion: v1
kind: Pod
metadata:
  name: hello-pod
spec:
  containers:
    - name: webserver
      image: nginx:1.25
```
$ `kubectl get nodes`
$ `kubectl apply -f nginx.yaml`  
$ `kubectl get pods`          # list of pods
$ `kubectl get pods -w`       # to watch internal functionality
$ `kubectl get pods -o wide`  # shows the output with more information
$ `kubectl api-resources`     # Kubernetes allows us to view all the resources using kubectl
$ `kubectl describe pod`      # show what happends in side the pod
[Preview](./Image/kubernetes19.PNG)
[Preview](./Image/kubernetes20.PNG)
[Preview](./Image/kubernetes21.PNG)


#### Note: In kubernetes we can not run two containers which use the same port in one pod.

#### Scaling: 
Scaling in k8s means increasing number of Pods not containers in Pod. For Scaling pods we would learn Replica set/Replication Controller etcs..

#### Label
* Lable is a key pair examples are
```
     app: nginx
     version: v1.0
```
* Labels are used to select/query kubernetes objects
* Labels are just like stickers. Name of the label does not have any functionality that is running inside the container.
* Labels are given just to identify quicker the objects.



















