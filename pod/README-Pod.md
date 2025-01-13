
# Pod Example

This is a simple example of a Kubernetes Pod. A Pod is the smallest deployable unit in Kubernetes. It can contain one or more containers.

## YAML Explanation

- **apiVersion**: Specifies the API version (v1) for the Pod.
- **kind**: Defines the type of resource (Pod).
- **metadata**: Contains the metadata, such as the name of the Pod (`my-pod`).
- **spec**: Defines the specification of the Pod.
  - **containers**: Lists the containers inside the Pod.
    - **name**: The name of the container (`my-container`).
    - **image**: The Docker image to use (`nginx:1.14.2`).
    - **ports**: Specifies the ports to be exposed (80).

To create this Pod in your Kubernetes cluster, run:
```bash
kubectl apply -f pod-example.yaml
```
