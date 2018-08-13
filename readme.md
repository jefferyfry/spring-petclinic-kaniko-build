# Spring PetClinic Docker Build Example using Kaniko

This is an example of running Docker builds on CloudBees Core on Kubernetes. This example runs a maven build, docker build and pushes the image to GCR using Kaniko. This example also uses the Kubernetes Plugin yamlFile option to specify the agent pod template.

## Requirements
- CloudBees Core 1.212.2.1 with Kubernetes Plugin 1.10.2

## Setup

This example pipeline pushes to Google Container Registry (GCR). To use Kaniko to push to GCR, you must create a ServiceAccount on GCP and download the resulting ServiceAccoint JSON file. Then execute this commant to create the secret:

```
kubectl create secret generic kaniko-secret --from-file=kaniko-secret.json
```
