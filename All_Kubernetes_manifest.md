# Introduction
Kubernetes manifest files are essential configurations that define and manage the various resources within a Kubernetes cluster. These files, written in YAML or JSON format, specify the desired state and behavior of resources such as Pods, Services, Deployments, and more. They serve as the blueprint for deploying and maintaining applications and their infrastructure in a Kubernetes environment. This documentation provides an overview of the different types of Kubernetes manifest files, including their structure and purpose, to help you effectively manage and orchestrate your containerized applications. Whether you're setting up a basic application or managing complex deployments, understanding these manifest files is crucial for efficient Kubernetes operations.

# Kubernetes Manifest Files

Kubernetes manifest files are YAML or JSON configuration files used to define and manage resources in a Kubernetes cluster. Below is a comprehensive list of the most common Kubernetes manifest files and their purposes.

## 1. Pod Manifest

Defines a single Pod, the smallest deployable unit in Kubernetes. It can include one or more containers.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: my-container
      image: nginx
```
## 2. Deployment Manifest

Defines a Deployment that manages a set of identical Pods and provides rolling updates and rollback capabilities.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: nginx
```

## 3. Service Manifest

Defines a Service that provides a stable IP address and DNS name for a set of Pods and can load balance traffic between them.

## Type:
- Load Balancer
- ClusterIP
- Nodeport

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

## 4. ConfigMap Manifest

Defines a ConfigMap to store configuration data in key-value pairs that can be used by Pods.

## Type:
- Load Balancer
- ClusterIP
- Nodeport

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-configmap
data:
  key1: value1
  key2: value2
```

## 5. Secret Manifest

Defines a Secret to store sensitive data, such as passwords or OAuth tokens, in a secure manner.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  key1: dGVzdA==  # Base64 encoded value
```

## 6. StatefulSet Manifest

Defines a StatefulSet for managing stateful applications with stable, unique network identifiers and persistent storage.

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: my-statefulset
spec:
  serviceName: "my-service"
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: nginx
  volumeClaimTemplates:
    - metadata:
        name: my-storage
      spec:
        accessModes: ["ReadWriteOnce"]
        resources:
          requests:
            storage: 1Gi
```

## 7. ReplicaSet Manifest

Defines a ReplicaSet that ensures a specified number of pod replicas are running at any given time. Often managed by a Deployment.

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-replicaset
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: nginx
```

## 8. Job Manifest

Defines a Job that creates one or more Pods and ensures that a specified number of them successfully terminate.

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: my-job
spec:
  template:
    spec:
      containers:
        - name: my-container
          image: busybox
          command: ["sh", "-c", "echo Hello Kubernetes! && sleep 30"]
      restartPolicy: Never
```

## 9. CronJob Manifest

Defines a CronJob that runs Jobs on a scheduled time or interval, similar to a cron job in Unix-like systems.

```yaml
apiVersion: batch/v1
kind: CronJob
metadata:
  name: my-cronjob
spec:
  schedule: "0 0 * * *"  # Runs daily at midnight
  jobTemplate:
    spec:
      template:
        spec:
          containers:
            - name: my-container
              image: busybox
              command: ["sh", "-c", "echo Hello Kubernetes!"]
          restartPolicy: OnFailure
```

## 10. Namespace Manifest

Defines a Namespace to divide cluster resources between multiple users.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace
```

## 11. Ingress Manifest

Defines a Namespace to divide cluster resources between multiple users.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
    - host: example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: my-service
                port:
                  number: 80
```

## 12. NetworkPolicy Manifest

Defines a NetworkPolicy to control the traffic flow between Pods and/or between Pods and external endpoints.

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: my-networkpolicy
spec:
  podSelector:
    matchLabels:
      app: my-app
  policyTypes:
    - Ingress
    - Egress
  ingress:
    - from:
      - podSelector:
          matchLabels:
            role: frontend
  egress:
    - to:
      - ipBlock:
          cidr: 10.0.0.0/16
```

## 13. PersistentVolume (PV) Manifest

Defines a PersistentVolume for managing storage resources.

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /mnt/data
```

## 14. PersistentVolumeClaim (PVC) Manifest

Defines a PersistentVolumeClaim for requesting storage resources.

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

















































