# Kubernetes Service

- Kubernetes Service is an abstraction which defines a logical set of Pods and a policy by which to access them.

# Notes

- A Kubernetes Service is an abstraction that defines a logical set of Pods and a policy by which to access them. Services enable a loose coupling between dependent Pods, allowing them to be decoupled from the underlying infrastructure.
- A Service is defined using YAML or JSON, like any other Kubernetes object.
- A Service can be exposed in different ways by specifying a type in the ServiceSpec:

  - ClusterIP (default): Exposes the Service on an internal IP in the cluster. This type makes the Service only reachable from within the cluster.
  - NodePort: Exposes the Service on the same port of each selected Node in the cluster using NAT. This type makes a Service accessible from outside the cluster using `<NodeIP>:<NodePort>`.
  - LoadBalancer: Exposes the Service externally using a cloud provider's load balancer. NodePort and ClusterIP Services, to which the external load balancer routes, are automatically created.
  - ExternalName: Maps the Service to the contents of the `externalName` field (e.g., `foo.bar.example.com`), by returning a CNAME record with its value. No proxying of any kind is set up.

  # Basic Service definition

  ```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: my-service # Name of the service
    namespace: default # Namespace of the service
    labels:
      app: my-app # Label of the service
  spec:
    selector:
      app: my-app # Label of the pod
    ports:
      - protocol: TCP # Protocol of the port
        port: 80 # Port of the service
        targetPort: 80 # Port of the pod
  ```

  # Commands

  - # Save a service definition to a file:

    ```bash
    kubectl expose pod my-pod --port=80 --name=my-service --dry-run=client -o yaml > service-definition.yaml
    ```

  - # Create a service

    ```bash
    kubectl create -f service-definition.yaml
    ```

  - # Create a service with a specific namespace

    ```bash
    kubectl create -f service-definition.yaml --namespace=my-namespace
    ```

  - # Create a service with kubectl command

    ```bash
    kubectl expose pod my-pod --port=80 --name=my-service
    ```

  - # Get service

    ```bash
    kubectl get service my-service
    ```

  - # Describe service

    ```bash
    kubectl describe service my-service
    ```

  - # Delete a service

    ```bash
    kubectl delete service my-service
    ```

  # Related

  - [Pods](/pods/pods.md)
  - [Deployments](/deployments/deployments.md)
  - [ReplicaSets](/replicasets/replicasets.md)
  - [Namespaces](/namespaces/namespaces.md)
  - [ConfigMap](/configmap/configmap.md)
  - [Secrets](/secrets/secret.md)

  # Tags: [kubernetes, service]
