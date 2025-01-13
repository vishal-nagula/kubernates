# Secret Example

This example demonstrates how to create a Secret in Kubernetes.

## Secret Definition

- **apiVersion**: v1
- **kind**: Secret
- **metadata.name**: example-secret
- **type**: Opaque
- **data**: Base64-encoded key-value pairs for sensitive data.

### Usage

Apply the Secret using:

```bash
kubectl apply -f secret-example.yaml
```

Retrieve the Secret details:

```bash
kubectl get secret example-secret -o yaml
```

Decode the Secret value:

```bash
echo 'YWRtaW4=' | base64 --decode
```
