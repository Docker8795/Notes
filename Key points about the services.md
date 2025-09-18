**Key Points to Remember about Kubernetes Services**



**Default Service Type:**



If you don’t mention the type field in a Service YAML, Kubernetes creates a ClusterIP Service by default.



This means the service is accessible only inside the cluster.



**NodePort Service Behavior:**



When you create a Service with type: NodePort, you can either specify a nodePort or leave it empty.



If you don’t specify it, Kubernetes will automatically assign a port from the default NodePort range (30000–32767).





**when you write a yaml file**



**Meaning of (port):**



The port field in the Service spec refers to the Service’s internal port (the port through which other services/pods in the cluster will access this Service).



**Meaning of (targetPort):**



The targetPort field maps to the container’s port inside the Pod where the actual application is running.



Example: if your container runs on port 8080, you set targetPort: 8080.



**Meaning of (nodePort):**



The nodePort field (only in NodePort type) exposes the Service on a port of the worker node.



**In short:**



**port →** Cluster Service Port



**targetPort →** Container/Pod Port



**nodePort →** Worker Node Port (external access)















