
# Deployment Example

This example demonstrates a Kubernetes Deployment, which provides declarative updates for Pods and ReplicaSets.

## YAML Explanation

- **apiVersion**: Specifies the API version (apps/v1) for the Deployment.
- **kind**: Defines the type of resource (Deployment).
- **metadata**: Contains the metadata, such as the name of the Deployment (`my-deployment`).
- **spec**: Defines the specification of the Deployment.
  - **replicas**: Number of desired Pod replicas (3).
  - **selector**: Specifies the label selector for the Pods.
    - **matchLabels**: Label query to match the Pods (`app: MyApp`).
  - **template**: Describes the Pods that will be created.
    - **metadata**: Metadata for the Pods.
      - **labels**: Labels to be applied to the Pods (`app: MyApp`).
    - **spec**: Specification for the Pods.
      - **containers**: Lists the containers inside the Pods.
        - **name**: The name of the container (`my-container`).
        - **image**: The Docker image to use (`nginx:1.14.2`).
        - **ports**: Specifies the ports to expose (80).

To create this Deployment in your Kubernetes cluster, run:
```bash
kubectl apply -f deployment-example.yaml
```
