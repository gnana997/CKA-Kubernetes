# Pods

# Description:

Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.

# tags: [kubernetes, pods]

# Notes

- A Pod is a group of one or more containers, with shared storage/network resources, and a specification for how to run the containers.
- A Pod's contents are always co-located and co-scheduled, and run in a shared context.
- Pods in a Kubernetes cluster are used in two main ways:
  - Pods that run a single container. The "one-container-per-Pod" model is the most common Kubernetes use case; in this case, you can think of a Pod as a wrapper around a single container, and Kubernetes manages the Pods rather than the containers directly.
  - Pods that run multiple containers that need to work together. A Pod might encapsulate an application composed of multiple co-located containers that are tightly coupled and need to share resources. These co-located containers might form a single cohesive unit of service--one container serving files from a shared volume, while a separate "sidecar" container refreshes or updates those files.

# Basic Pod definition

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod # Name of the pod
  namespace: default # Namespace of the pod
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

- # Save a pod definition to a file:

  ```bash
  kubectl run pods --image=nginx:latest --dry-run=client -o yaml > pod-definition.yaml
  ```

- # Create a pod

  ```bash
  kubectl create -f pod-definition.yaml
  ```

- # Create a pod with a specific namespace

  ```bash
  kubectl create -f pod-definition.yaml --namespace=my-namespace
  ```

- # Get pods

  ```bash
  kubectl get pods
  ```

- # Get pod details

  ```bash
  kubectl describe pod my-pod
  ```

- # Delete a pod

  ```bash
  kubectl delete pod my-pod
  ```

- # Get logs of a pod

  ```bash
  kubectl logs my-pod
  ```

- # Execute a command in a pod

  ```bash
  kubectl exec my-pod -- ls
  ```

- # Execute a command in a pod with a specific container

  ```bash
  kubectl exec my-pod -c my-container -- ls
  ```

- # Get pod events

  ```bash
  kubectl get events
  ```

- # Edit pod

  ```bash
  kubectl edit pod my-pod
  ```

- # Add labels to a pod

  ```bash
  kubectl label pod my-pod new-label=awesome
  ```

- # Remove labels from a pod

  ```bash
  kubectl label pod my-pod new-label-
  ```

- # Add tolerations to a pod

  ```bash
  kubectl taint nodes node1 key=value:NoSchedule
  kubectl taint nodes node1 key=value:NoExecute
  ```

- # Remove tolerations from a pod

  ```bash
  kubectl taint nodes node1 key:NoSchedule-
  kubectl taint nodes node1 key:NoExecute-
  ```

- # Add annotations to a pod

  ```bash
  kubectl annotate pod my-pod new-annotation=awesome
  ```

- # Remove annotations from a pod
  ```bash
  kubectl annotate pod my-pod new-annotation-
  ```
