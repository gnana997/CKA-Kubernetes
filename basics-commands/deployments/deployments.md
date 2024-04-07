# Deployments

- Deployments are a higher-level concept that manages ReplicaSets and Pods.

# Notes:

- A Deployment is a higher-level concept that manages ReplicaSets and provides declarative updates to Pods along with a lot of other useful features.
- A Deployment ensures that a specified number of Pod replicas are running at any given time.
- A Deployment allows you to describe an application's life cycle, such as which images to use for the app, the number of Pods, and how to update them.

# Basic Deployment definition

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment # Name of the deployment
  namespace: default # Namespace of the deployment
  labels:
    app: my-app # Label of the deployment
spec:
  replicas: 3 # Number of replicas
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

- # Save a deployment definition to a file:

  ```bash
  kubectl run deployment --image=nginx:latest --replicas=3 --dry-run=client -o yaml > deployment-definition.yaml
  ```

- # Create a deployment

  ```bash
  kubectl create -f deployment-definition.yaml
  ```

- # Create a deployment with a specific namespace

  ```bash
  kubectl create -f deployment-definition.yaml --namespace=my-namespace
  ```

- # Get deployments

  ```bash
  kubectl get deployments
  ```

- # Get deployment details

  ```bash
  kubectl describe deployment my-deployment
  ```

- # Get deployment logs

  ```bash
  kubectl logs deployment/my-deployment
  ```

- # Delete a deployment

  ```bash
  kubectl delete deployment my-deployment
  ```

- # Scale a deployment

  ```bash
  kubectl scale deployment my-deployment --replicas=5
  ```

- # Update a deployment

  ```bash
  kubectl set image deployment/my-deployment my-container=nginx:1.17
  ```

- # Rollback a deployment

  ```bash
  kubectl rollout undo deployment/my-deployment
  ```

- # Pause a deployment

  ```bash
  kubectl rollout pause deployment/my-deployment
  ```

- # Resume a deployment

  ```bash
  kubectl rollout resume deployment/my-deployment
  ```

- # Get deployment history

  ```bash
  kubectl rollout history deployment/my-deployment
  ```

- # Get deployment history details

  ```bash
  kubectl rollout history deployment/my-deployment --revision=1
  ```

- # Get deployment status

  ```bash
  kubectl rollout status deployment/my-deployment
  ```

- # Get deployment events

  ```bash
  kubectl get events --field-selector involvedObject.name=my-deployment
  ```

- # Get deployment pods

  ```bash
  kubectl get pods --selector=app=my-app
  ```

- # Get deployment replicasets

  ```bash
  kubectl get replicasets --selector=app=my-app
  ```

- # Get deployment services

  ```bash
  kubectl get services --selector=app=my-app
  ```

# Related

- [Pods](/basics-commands/pods/pods.md)
- [ReplicaSet](/basics-commands/replicasets/replicaset.md)
- [Namespaces](/basics-commands/namespaces/namespaces.md)
- [Services](/basics-commands/services/services.md)
