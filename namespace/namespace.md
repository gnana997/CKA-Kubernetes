# Namespace

- Namespace in Kubernetes is a way to divide cluster resources between multiple users (via resource quota).

# Notes

- Namespaces are intended for use in environments with many users spread across multiple teams, or projects.
- Namespaces are a way to divide cluster resources between multiple users (via resource quota).

# Basic Namespace definition

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace # Name of the namespace
```

# Commands

- # Save a namespace definition to a file:

  ```bash
  kubectl create namespace my-namespace --dry-run=client -o yaml > namespace-definition.yaml
  ```

- # Create a namespace

  ```bash
  kubectl create -f namespace-definition.yaml
  ```

- # Create a namespace with kubectl command

  ```bash
  kubectl create namespace my-namespace
  ```

- # Get namespaces

  ```bash
  kubectl get namespaces
  ```

- # Get namespace details

  ```bash
  kubectl describe namespace my-namespace
  ```

- # Delete a namespace

  ```bash
  kubectl delete namespace my-namespace
  ```

# Related

- [Pods](/pods/pods.md)
- [Services](/service/service.md)
- [Deployments](/deployments/deployments.md)
- [ReplicaSets](/replicasets/replicaset.md)
- [ConfigMaps](/configmap/configmap.md)
- [Secrets](/secret/secret.md)

# Tags: [Kubernetes, namespace, ns]
