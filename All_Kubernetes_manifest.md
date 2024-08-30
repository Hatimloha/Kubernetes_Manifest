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
