
# Service Example

This example defines a Kubernetes Service, which is an abstraction that defines a logical set of Pods and a policy by which to access them.

## YAML Explanation

- **apiVersion**: Specifies the API version (v1) for the Service.
- **kind**: Defines the type of resource (Service).
- **metadata**: Contains the metadata, such as the name of the Service (`my-service`).
- **spec**: Defines the specification of the Service.
  - **selector**: A label query over Pods that should match this Service (`app: MyApp`).
  - **ports**: Specifies the ports to expose.
    - **protocol**: The protocol to use (TCP).
    - **port**: The port that the service will listen on (80).
    - **targetPort**: The port on the Pod that will receive the traffic (9376).

To create this Service in your Kubernetes cluster, run:
```bash
kubectl apply -f service-example.yaml
```
