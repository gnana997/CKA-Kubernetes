# Static Pods

- Static Pods are managed directly by the kubelet daemon on a specific node, without the API server observing them.

# Notes

- Static Pods are always bound to one kubelet on a specific node.
- Static Pods are managed directly by the kubelet daemon on a specific node, without the API server observing them.
- The kubelet automatically tries to create a mirror Pod on the Kubernetes API server for each static Pod.
- Generally used to run system daemons like `kubelet`, `kube-proxy`, `flannel`, etc.

# Basic Static Pod definition

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-static-pod # Name of the static pod
  namespace: kube-system # Namespace of the static pod
  labels:
    app: my-app # Label of the static pod
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

- # Save a static pod definition to a file:

  ```bash
  kubectl run static-pod --image=nginx:latest --dry-run=client -o yaml > static-pod-definition.yaml
  ```

- # FInd the kubelet manifest directory

  ```bash
  cat /var/lib/kubelet/config.yaml | grep staticPodPath
  ```

- # Change to the kubelet manifest directory

  ```bash
  cd /var/lib/kubelet
  ```

- # Create a static pod

  ```bash
  cp static-pod-definition.yaml /var/lib/kubelet/static-pod-definition.yaml
  ```

- # Get static pods

  ```bash
  kubectl get pods --all-namespaces
  ```

# Tags: [Kubernetes, Static Pods]
