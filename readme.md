# Spring PetClinic Docker Build Example

This is an example of running Docker builds on CloudBees Core on Kubernetes (GKE). This example runs a maven build, docker build and pushes the image to docker hub.

## Requirements
- CloudBees Core 1.212.2.1 with Kubernetes Plugin 1.7.1

## Setup

1. In CJOC, go to the top level Jenkins navigation and select the _All_ tab.
2. Select _kubernetes shared cloud_.
<img width="513" alt="kubernetes_shared_cloud" src="https://user-images.githubusercontent.com/6440106/43618799-49a8dcc2-967f-11e8-8a08-bd9b8ecd217d.png">

3. Select _Configure_.

4. Here you will add a Kubernetes Pod Template and add the containers you need. The Pod Templates are available to all masters. For this project, these values were specified:
<img width="700" alt="pod_template" src="https://user-images.githubusercontent.com/6440106/43618763-10c25244-967f-11e8-92ec-adb45a130957.png"> 
In some cases docker.sock is in a different location. Use _ADD Environment Variable_ to specify DOCKER_HOST = _path_. Example DOCKER_HOST=unix:///var/vcap/sys/run/docker/docker.sock

5. Then see the Jenkinsfile for an example pipeline of how these containers are used to do the maven build, docker build and push to the registry.

6. In this example, DockerHub is used. Add your credentials for DockerHub so that they can be referenced by the pipeline.
<img width="1265" alt="credentials" src="https://user-images.githubusercontent.com/6440106/43618773-243c4b0e-967f-11e8-8e80-1e3555410640.png">
