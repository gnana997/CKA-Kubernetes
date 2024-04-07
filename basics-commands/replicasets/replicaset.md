# ReplicaSet

- A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time.

# tags: [kubernetes, replicaset]

# Notes

- A ReplicaSet is defined with fields, including the replicas field that specifies the number of Pods that the ReplicaSet should maintain.
- A ReplicaSet then makes sure that the actual number of Pods matches the desired number of Pods.
- A ReplicaSet is a higher-level abstraction that manages Pods and ensures that a specified number of Pod "replicas" are running at any given time.
- However, a ReplicaSet is not the only way to run multiple instances of a Pod. For example, a Deployment is a higher-level concept that manages ReplicaSets and provides declarative updates to Pods along with a lot of other useful features.

# Basic ReplicaSet definition

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-replicaset # Name of the replicaset
  namespace: default # Namespace of the replicaset
  labels:
    app: my-app # Label of the replicaset
spec:
  replicas: 3 # Number of replicas
  desiredReplicas: 3 # Number of replicas
  selector:
    matchLabels:
      app: my-app # Label of the pod
  template:
    metadata:
      labels:
        app: my-app # Label of the pod
    spec:
      containers:
        - name: my-container # Name of the container
          image: nginx:latest # Image of the container
          labels:
            app: my-app # Label of the container
          ports:
            - containerPort: 80 # Port of the container
```

# Commands

- # Save a replicaset definition to a file:

  ```bash
  kubectl run replicaset --image=nginx:latest --replicas=3 --dry-run=client -o yaml > replicaset-definition.yaml
  ```

- # Create a replicaset

  ```bash
  kubectl create -f replicaset-definition.yaml
  ```

- # Create a replicaset with a specific namespace

  ```bash
  kubectl create -f replicaset-definition.yaml --namespace=my-namespace
  ```

- # Get replicaset

  ```bash
  kubectl get replicaset
  ```

- # Get replicaset details

  ```bash
  kubectl describe replicaset my-replicaset
  ```

- # Delete a replicaset

  ```bash
  kubectl delete replicaset my-replicaset
  ```

- # Get logs of a replicaset

  ```bash
  kubectl logs replicaset my-replicaset
  ```

- # Scale a replicaset

  ```bash
  kubectl scale replicaset my-replicaset --replicas=5
  ```

# Related

- [Pods](/pods.md)
- [Deployments](/deployments.md)
