# ConfigMap Example

This example demonstrates how to create a ConfigMap in Kubernetes.

## ConfigMap Definition

- **apiVersion**: v1
- **kind**: ConfigMap
- **metadata.name**: example-configmap
- **data**: Key-value pairs representing configuration data.

### Usage

Apply the ConfigMap using:

```bash
kubectl apply -f configmap-example.yaml
```

Retrieve the ConfigMap details:

```bash
kubectl get configmap example-configmap -o yaml
```
