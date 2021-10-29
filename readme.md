# Spring PetClinic Docker Build Example using Kaniko

[![IaC](https://app.soluble.cloud/api/v1/public/badges/39d6c464-21e2-4103-8ca3-0ab52d618307.svg)](https://app.soluble.cloud/repos/details/github.com/jefferyfry/spring-petclinic-kaniko-build)  [![CIS](https://app.soluble.cloud/api/v1/public/badges/90325000-74f8-448f-b172-3905b4b5a3a2.svg)](https://app.soluble.cloud/repos/details/github.com/jefferyfry/spring-petclinic-kaniko-build)  

This is an example of running Docker builds on CloudBees Core on Kubernetes. This example runs a maven build, docker build and pushes the image to GCR using Kaniko. This example also uses the Kubernetes Plugin yamlFile option to specify the agent pod template.

## Requirements
- CloudBees Core 1.212.2.1 with Kubernetes Plugin 1.10.2

## Setup

This example pipeline pushes to Google Container Registry (GCR). To use Kaniko to push to GCR, you must create a ServiceAccount on GCP and download the resulting ServiceAccoint JSON file. Then execute this commant to create the secret:

```
kubectl create secret generic kaniko-secret --from-file=kaniko-secret.json
```
