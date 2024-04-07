# Secret

- Kubernetes secret is a resource that stores a piece of sensitive data like a password or a token.

# Notes

- Secrets are intended to store sensitive data.
- Secrets are stored in tmpfs (RAM-backed filesystem) to reduce the risk of the secret leaking to disk.
- Secrets are base64 encoded, which means that they are not encrypted.
- Secrets can be used to store sensitive information such as passwords, OAuth tokens, and ssh keys.
- Secrets can be consumed in multiple ways, such as environment variables, command-line arguments, or configuration files in a volume.

# Basic Secret definition

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret # Name of the secret
type: Opaque # Type of the secret
data:
  key1: dmFsdWUx # Base64 encoded value
  key2: dmFsdWUy # Base64 encoded value
```

# Commands

- # Save a secret definition to a file:

  ```bash
  kubectl create secret generic my-secret --from-literal=key1=value1 --from-literal=key2=value2 --dry-run=client -o yaml > secret-definition.yaml
  ```

- # Create a secret

  ```bash
  kubectl create -f secret-definition.yaml
  ```

- # Create a secret with a specific namespace

  ```bash
  kubectl create -f secret-definition.yaml --namespace=my-namespace
  ```

- # Create a secret with kubectl command

  ```bash
  kubectl create secret generic my-secret --from-literal=key1=value1 --from-literal=key2=value2
  ```

- # Get secrets

  ```bash
  kubectl get secrets
  ```

- # Get secret details

  ```bash
  kubectl describe secret my-secret
  ```

- # Delete a secret

  ```bash
  kubectl delete secret my-secret
  ```

# Related

- [ConfigMap](/basics-commands/configmap/configmap.md)
- [Pods](/basics-commands/pods/pods.md)
- [Deployments](/basics-commands/deployments/deployments.md)
- [Services](/basics-commands/services/services.md)
- [Namespaces](/basics-commands/namespaces/namespaces.md)
- [ReplicaSets](/basics-commands/replicasets/replicasets.md)
