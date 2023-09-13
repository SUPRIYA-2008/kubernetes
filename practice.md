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

#### 2. Metdata: 
This helps in naming and labelling resources in k8s












