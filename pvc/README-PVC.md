# PersistentVolumeClaim Example

This example demonstrates how to create a PersistentVolumeClaim in Kubernetes.

## PVC Definition

- **apiVersion**: v1
- **kind**: PersistentVolumeClaim
- **metadata.name**: example-pvc
- **spec.accessModes**: ReadWriteOnce
- **spec.resources.requests.storage**: 1Gi

### Usage

Apply the PVC using:

```bash
kubectl apply -f pvc-example.yaml
```

Check the PVC details:

```bash
kubectl get pvc example-pvc -o yaml
```
