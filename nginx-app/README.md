# Nginx Test Application

This directory contains a complete test nginx deployment for Kubernetes.

## Files

- `deployment.yaml` - Kubernetes deployment with 2 replicas of nginx
- `service.yaml` - ClusterIP service to expose the nginx pods
- `ingress.yaml` - Ingress resource to expose the service externally
- `kustomization.yaml` - Kustomize configuration to manage all resources

## Deployment

### Using kubectl directly:
```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
```

### Using kustomize:
```bash
kubectl apply -k .
```

## Access

The application will be available at `http://nginx.biasotti.co`.

**Note:** You'll need to configure DNS to point `nginx.biasotti.co` to your cluster's external IP address, or add an entry to your `/etc/hosts` file for local testing.

To find your cluster's external IP:
```bash
kubectl get svc -n kube-system traefik -o wide
```

For local testing, you can add to `/etc/hosts`:
```
YOUR_CLUSTER_IP nginx.biasotti.co
```

## Verification

Check the deployment status:
```bash
kubectl get pods -l app=nginx-test
kubectl get svc nginx-test-service
kubectl get ingress nginx-test-ingress
```

## Scaling

To scale the deployment:
```bash
kubectl scale deployment nginx-test --replicas=3
```

## Cleanup

To remove all resources:
```bash
kubectl delete -k .
``` 