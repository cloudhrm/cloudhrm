# CloudHRM

This is a main repository of Could HRM - Cloud Human Resources System

System consists of multiple modules, which are developed as independant subprojects.

Here you can find project wise documentation and installation instructions.

# Install CloudHRM to Kubernetes cluster

## Requirements

* Kubernetes is installed
* You have full rights to your cluster

## Install

### Prepeare

First you have to create namespace for CloudHRM. Let's say we create test environment namespace:

```bash
kubectl create namespace cloudhrm-test
```

Optionally allow your namespace to be managed by Istio:

```bash
kubectl label namespace cloudhrm-test istio-injection=enabled
kubectl get namespace -L istio-injection
kubectl config set-context $(kubectl config current-context) --namespace=cloudhrm-test
```

### Deploy base

### Deploy modules

Deploy auth module:

```bash
kubectl apply -f ./k8s/db-service.yaml
kubectl apply -f ./k8s/db-deployment.yaml
kubectl apply -f ./k8s/prisma-service.yaml

kubectl apply -f ./k8s/prisma-deployment.yaml
kubectl apply -f ./k8s/auth-deployment.yaml
# Finish with gateway
kubectl apply -f ./k8s/cloudhrm-gateway.yaml
```
