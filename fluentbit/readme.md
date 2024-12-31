# Fluent Bit Logging Stack with Minikube

This guide demonstrates how to set up a simple logging stack using Fluent Bit in a Kubernetes (K8S) cluster created with Minikube. 
Fluent Bit is used to scrape logs from various sources, and in this example, it collects logs from a basic application and outputs them as tail.

## Overview

### What is Fluent Bit?
Fluent Bit is a lightweight and flexible log processor and forwarder. 
It collects logs from different sources, processes them, and routes them to various outputs. 

In this demo, Fluent Bit will:
- Scrape logs produced by application containers.
- Print the logs as output.


## Demo Stack Overview

### Cluster Setup
We use Minikube to create a Kubernetes cluster with 3 nodes:
- 1 Master/Worker Node (do both in minikube)
- 2 Worker Nodes

**To create the cluster:**
```bash
minikube start -n 3
````

**Step 1: Deploying a Basic Logging Application**
For this demo, we use the Docker image __chentex/random-logger__, which generates random log messages as output.

To deploy the application with 5 replicas, apply the provided deployment YAML file:
```bash
kubectl apply -f app.yaml
```

**Step 2: Ingesting Logs with FluentBit**
In this setup, Fluent Bit will scrape logs from our application containers.
Fluent Bit is configured using a ConfigMap to define how logs are collected and where they are sent. 

To deploy Fluent Bit, apply the provided configuration YAML file:

```bash
kubectl apply -f fluent-bit.yaml
```
