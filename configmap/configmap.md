# ConfigMap

- ConfigMap is a Kubernetes resource that allows you to store configuration data in key-value pairs. It is used to decouple configuration artifacts from image content to keep containerized applications portable.

# Notes

- ConfigMaps allow you to separate your configurations from your Pods and components, which helps keep your applications portable.
- ConfigMaps are useful for storing and managing configuration data that is not sensitive.
- ConfigMaps can be used to store fine-grained information such as individual properties or coarse-grained information such as entire configuration files or JSON blobs.
- ConfigMaps can be consumed in multiple ways, such as environment variables, command-line arguments, or configuration files in a volume.

# Basic ConfigMap definition

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-configmap # Name of the configmap
  namespace: default # Namespace of the configmap
data:
  key1: value1 # Key-value pair
  key2: value2 # Key-value pair
```

# Commands

- # Save a configmap definition to a file:

  ```bash
  kubectl create configmap my-configmap --from-literal=key1=value1 --from-literal=key2=value2 --dry-run=client -o yaml > configmap-definition.yaml
  ```

- # Create a configmap

  ```bash
  kubectl create -f configmap-definition.yaml
  ```

- # Create a configmap with a specific namespace

  ```bash
  kubectl create -f configmap-definition.yaml --namespace=my-namespace
  ```

- # Create a configmap with kubectl command

  ```bash
  kubectl create configmap my-configmap --from-literal=key1=value1 --from-literal=key2=value2
  ```

- # Get configmaps

  ```bash
  kubectl get configmaps
  ```

- # Get configmap details

  ```bash
  kubectl describe configmap my-configmap
  ```

- # Delete a configmap

  ```bash
  kubectl delete configmap my-configmap
  ```

# Related

- [Secrets](/secrets/secret.md)
- [Pods](/pods/pods.md)
- [Services](/service/service.md)
- [deployments](/deployments/deployments.md)
- [replicaset](/replicasets/replicaset.md)
- [namespace](/namespace/namespace.md)

# Tags: [kubernetes, configmap, cm]
