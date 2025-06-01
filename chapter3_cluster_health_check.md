# Chapter 3: Cluster Health Check

Kubernetes provides CLI tools like `kubectl` to inspect the control plane, nodes, and workloads. This chapter covers basic health checks.

## 3.1 Component Health

To check the overall health of key control-plane components:

```bash
kubectl get componentstatuses
# OR
kubectl get cs
```

> ⚠️ `ComponentStatus` is deprecated in v1.19+

**Sample Output:**

```
NAME                 STATUS    MESSAGE   ERROR
scheduler            Healthy   ok
controller-manager   Healthy   ok
etcd-0               Healthy   ok
```

## 3.2 Node Status

To list the status of all nodes:

```bash
kubectl get nodes
```

For more detailed information:

```bash
kubectl get nodes -o wide
```

**Sample Output:**

```
NAME         STATUS     ROLES           VERSION    INTERNAL-IP      OS-IMAGE
k8s-master   Ready      control-plane   v1.29.7    192.168.1.18     CentOS Stream 8
k8m-node1    NotReady   <none>          v1.29.7    192.168.1.50     CentOS Stream 8
k8m-node2    Ready      <none>          v1.29.10   192.168.1.33     CentOS Stream 8
```

## 3.3 Pod Health Across Namespaces

To inspect the status of pods in all namespaces:

```bash
kubectl get pods --all-namespaces
```

**Example Output:**

```
NAMESPACE       NAME                                   READY   STATUS    AGE
calico-system   csi-node-driver-vgbqs                 2/2     Running   257d
calico-system   csi-node-driver-zhpkh                 2/2     Running   172d
kube-system     kube-apiserver-k8s-master             1/1     Running   257d
kube-system     kube-controller-manager-k8s-master    1/1     Running   257d
kube-system     kube-scheduler-k8s-master             1/1     Running   257d
```

## ✅ Summary

- Use `kubectl get cs` to check core component health (deprecated).
- Use `kubectl get nodes -o wide` for detailed node information.
- Use `kubectl get pods --all-namespaces` to monitor cluster-wide pod health.
