# Exercise 1: Hello Pod - Kubernetes

## Objective
Deploy an NGINX web server on Kubernetes and expose it through a NodePort Service, simulating a lightweight Zepto storefront application.

## Tools Used
- Kubernetes
- kubectl
- NGINX container image
- Killercoda Kubernetes Playground

## Steps Performed

### 1. Create the Pod
    kubectl run hello-k8s --image=nginx --port=80

### 2. Verify the Pod
    kubectl get pods

The hello-k8s Pod reached Running status with 1/1 containers ready.

### 3. Expose the Pod
    kubectl expose pod hello-k8s --type=NodePort --port=80

### 4. Verify the Service
    kubectl get services

### 5. Test the Application
    kubectl run test-curl --image=curlimages/curl:latest --restart=Never --rm -i -- curl -I http://hello-k8s

The test returned HTTP/1.1 200 OK, confirming that NGINX responded successfully through the Kubernetes Service.

## Declarative Deployment

The hello-pod.yaml file defines the Pod and Service.

Apply the configuration:
    kubectl apply -f hello-pod.yaml

Verify:
    kubectl get pods
    kubectl get services

## Key Learnings
- Pods run containerized applications.
- Container images package application software.
- Services provide stable network access to Pods.
- NodePort exposes a Service through a port on cluster nodes.
- YAML manifests support declarative deployments.

## Environment
Tested using Killercoda's Kubernetes playground. Its resources are separate from a local Minikube cluster.

## Evidence
The screenshots directory is reserved for terminal screenshots showing successful execution.
